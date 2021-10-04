# Markdown Resume 

This repo allows you to build/maintain your resume in a Markdown file, and then publish it into an HTML or PDF file. 
Technically, you could output it into any file you wanted with pandoc, or wkhtmltopdf, but I wasn't interested in those scenarios so I explore those avenues. 

The inspiration for this project came from my need to look for a job, my need to update my resume, and my desire not to have to write something in Google docs, or Microsoft Word, so I scoured the web for newer way to build/maintain a resume, while doing so I ran into this [project by Sonya Sawtelle](https://sdsawtelle.github.io/blog/output/simple-markdown-resume-with-pandoc-and-wkhtmltopdf.html). 

I modified the CSS for my taste, and noticed that some of the documentation needed to be updated. 

Since Sonya's post is nearly five years old, there have been many changes to the command line utilities that she used, so I've updated this README to reflect those changes. 

# Workflow

The workflow is pretty simple. 

1. Edit the resume.md file. 
1. Run pandoc to convert the Markdown file to HTML. OR 
1. Run pandoc to convert the Markdown file into a PDF.


The big difference between Sonya's workflow is that if you want, you can convert from MD -> PDF in one step, rather than two. You can still go from MD -> HTML -> PDF, but if you don't want to have an HTML file, you don't have to. 

I also don't feel like supporting/using Microsoft Word, so I'm not even trying to output to .docx. 


# Updated instructions for a Mac .. or 2021
A lot has changed since Sonya wrote her blog post and shared her workflow, so here are some updates on how to get started and building/updating your own resume. 

# Pre-Requisites. 
## [Pandoc](https://pandoc.org) a universal document converter.

```bash 
    brew install pandoc 
```

## [Wkhtmltopdf](https://wkhtmltopdf.org)
```
    brew install wkhtmltopdf
```

## Markdown to HTML 
```
pandoc resume.md -f markdown -t html -c resume-stylesheet.css -s -o resume.html
```

## Markdown to PDF 

```
pandoc resume.md -f markdown -t pdf --pdf-engine=wkhtmltopdf -c resume-stylesheet.css -s -o resume.pdf
```

## HTML to PDF 

If you want to convert from HTML to PDF for some reason, you'll need to add a switch to wkhtmltopdf so that it works properly. 

```
wkhtmltopdf --enable-local-file-access resume.html resume.pdf
```

# TODO 
 - [x] [github action](https://github.com/pandoc/pandoc-action-example) will run and create the HTML and PDF file automatically. 
 - [ ] the Author field in the PDF, it seems to not work when the pdf-engine is set to wkhtmltopdf 
 - [ ] make a release or a package? 

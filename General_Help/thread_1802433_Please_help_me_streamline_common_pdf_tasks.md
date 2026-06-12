---
title: "Please help me streamline common pdf tasks"
date: 2011-07-11
forum: General Help
---

### Post by TomSahz on 2011-07-11
Hi there,

Im running Ubuntu Maverick on my Asus eee 1000HA netbook with limited-moderate knoweledge of linux.

I have 2 scenarios that I would greatly appreciate some help to streamline:
[U]
**Journal Articles** [/U]
I frequently download journal articles from Nature and join them into complete volumes. I log in to Nature's  online archive through my University's proxy then expand the year, and  choose the month. Each month contains 4-8 issues, which make up one  volume (1 volume for each month). So my usual procedure is to: 

[LIST=1]
[*]click the link for each issue in a given month
[*]use the downthemall Firefox extension to download/rename all of the pdf articles on the page
[*]then use PDFTK to join the articles into a group of issues + join the issues into a volume.
[/LIST]
So my question is: _Can anyone see a better way of doing this?_  I suppose it wouldnt be possible to produce a script to do this as the  pdf's require a proxy login and are on separate pages for each issue.
[U]
**General web articles/Recipes etc**[/U]
For pages/web articles that Id like to save in pdf I do the following:

[LIST=1]
[*]Load the page of interest usually from an RSS reader
[*]Copy the URL of the page to a text document
[*]Copy the template [wkhtmltopdf -s A4 X Y.pdf] underneath the link
[*]Type the name of the article or page underneath the template.
[*]Insert the URL into the template to replace 'X' and an ascending number into 'Y'
[*]Once I have a large list of articles I want to download I:
[*]Open the text file with the 3 line groups above
[*]Copy the templateline containig the URL and a number into the terminal and execute it.
[/LIST]
The webpages are then downloaded/transformed by the command line  utility 'wkhtmlyopdf' into pdf's named '1.pdf', '2.pdf' etc in a folder  on my desktop. I then copy the article names from the text document to  rename the pdf files to the name of the articles.  _Id like to know if anyone can see a faster way to automate all of this with a script or some other method._ It seems to possible to me to implement a script here although I have no idea how to go about such a script. 

I have tried 'Web2PDF' , 'PDFDownload' and the free Nitro pdf software  for converting web pages to pdf but the results are always far more  superior doing it with 'wkhtmltopdf'.

Thank you for reading this, any help is greatly appreciated :smile:

---


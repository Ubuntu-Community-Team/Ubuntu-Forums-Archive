---
title: "Custom paper sizes for Adobe Reader/Epson 1290"
date: 2010-09-18
forum: General Help
---

### Post by Nick Payne on 2010-09-18
I want to set a custom page size for printing some PDF three and four-page musical scores to roll paper on an Epson 1290 using Adobe Reader 9.3.4 on Ubuntu 10.04, using the page scaling print option in Reader to output multiple pages per sheet. The printer properties in the print dialog has a media size option, and one of the choices is "custom", but having chosen "custom", the dialog does not allow me to add the actual page size to the lpr printer command. I can see that when I choose "custom", the lpr command is
```
lpr -P Stylus-Photo-1290 -o PageSize=Custom etc
```
but what I need for a three page output, for example, is
```
lpr -P Stylus-Photo-1290 -o PageSize=Custom.297x630mm etc
```
and I can't see how to add the actual custom paper size. If I Ok the media size choice dialog with it just set to PageSize=Custom, I can see from the output preview in the print dialog that the actual page size that has been chosen is letter. The online Adobe doc for Reader 9 printing ([http://help.adobe.com/en_US/Reader/9.0/content.html#heading2.3](http://help.adobe.com/en_US/Reader/9.0/content.html#heading2.3)) says "For documents that are larger than the standard page size, go to File  > Page Setup.  Create a custom page size before you print your  document". The problem with that is that there is no "Page Setup" option on the File menu in the Unix version of Adobe Reader, only a "Print" option, which is where I already am.

If I open the PDFs in Evince, it allows me to add the custom page sizes I want, but as Evince doesn't have the option to print multiple pages per sheet, it won't give the desired output either...

---

### Post by jcottier on 2010-10-07
Yes, it used to work, and the resize zoom bar used to work too (now its grayed out). I don't know if this is a "who's to blame for it" thing, but its not getting fixed and its pretty bad that no one seems to care enough even to respond. I found my own solution by opening it in Gimp. Just right click and select open with other ...Gimp and it will import into it. In the Gimp Print dialog, you have a scaling percentage in the "Page Setup" tab, and size settings in the "Image settings" plus loads of other stuff including multiple copies.

---


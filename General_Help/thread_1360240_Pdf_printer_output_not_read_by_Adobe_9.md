---
title: "Pdf printer output not read by Adobe 9"
date: 2009-12-20
forum: General Help
---

### Post by Robbyx on 2009-12-20
Printing from Thunderbird to the cups printer I find I can not open the file in Acrobat. I chose print to file and put the pdf extension. 

What can I do about this so that it actually works without further conversion?

The first lines of the document looked at with a text editor shows:

> %!PS-Adobe-3.0
%%BoundingBox: 0 0 842 1191
%%HiResBoundingBox: 0 0 841.9 1190.55
%%Creator: Mozilla PostScript module (rv:1.8.1.23/2009081716)
%%DocumentData: Clean8Bit
%%DocumentPaperSizes: A3
%%Orientation: Portrait
%%Pages: 1
%%PageOrder: Ascend
%%EndComments
% MozillaCharsetName: iso-8859-1

To ensure that I am dealing with a pdf I have tried to open it with Adobe Reader 9. It will not open it. It says that it is either not a supported file type or it has been damaged.

---

### Post by lukeiamyourfather on 2009-12-20
The default output is not PDF if I remember correctly. Its a post script which Acrobat Reader will not read. There is an option to print as PDF but you'll have to do more than just change the file extension. Don't have Ubuntu in front of me to give the specifics. Cheers!

---

### Post by Robbyx on 2009-12-20
> **lukeiamyourfather said:**
> The default output is not PDF if I remember correctly. Its a post script which Acrobat Reader will not read. There is an option to print as PDF but you'll have to do more than just change the file extension. Don't have Ubuntu in front of me to give the specifics. Cheers!

Could you please check back if no one has given me the answer by the time you have access to Ubuntu?

---

### Post by lukeiamyourfather on 2009-12-20
See the screens attached. Note the print to file options, make sure to select the PDF output (not just change the extension). Tried it with the default PDF reader in Ubuntu 9.10 and in Acrobat Reader in Windows. Works fine in both. The print dialog is from Firefox viewing the Google homepage. Cheers!

---

### Post by kaibob on 2009-12-20
The easiest way to verify the file type is to use the file command. Just open a terminal window, change to the directory that contains the file in question, and type:

```
file filename
```

The file command ignores the file extension. Thus, for example, I renamed a PDF file to file.ps and a PS file to file.pdf, and I then checked these files with the file command:

> $ file file.ps
file.ps: PDF document, version 1.4
$file file.pdf
file.pdf: PostScript document text conforming DSC level 3.0, Level 2

---

### Post by lukeiamyourfather on 2009-12-20
> **kaibob said:**
> The easiest way to verify the file type is to use the file command. Just open a terminal window, change to the directory that contains the file in question, and type:

```
file filename
```

The file command ignores the file extension. Thus, for example, I renamed a PDF file to file.ps and a PS file to file.pdf, and I then checked these files with the file command:

Nice trick! I was unaware of that command. :)

---


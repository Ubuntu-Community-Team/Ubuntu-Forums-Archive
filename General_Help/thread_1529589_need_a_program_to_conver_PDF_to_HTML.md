---
title: "need a program to conver PDF to HTML"
date: 2010-07-12
forum: General Help
---

### Post by metalf8801 on 2010-07-12
I'm almost positive I've seen a program that runs on Ubuntu that can convert PDF files to HTML but I can't remember where I saw it and I have no idea what the name of it was :( 

It would also be great if I could find a program that can convert PDFs to .odt or .doc or another format that works well with Openoffice.org but thats not something I need right now

any help you can give would be great! 
Thank you 
Dan

---

### Post by mylesmadness on 2010-07-12
[http://www.pdfonline.com/convert-pdf-to-html/default.aspx](http://www.pdfonline.com/convert-pdf-to-html/default.aspx)

Thats a online version, I don't think there is a offline program for ubuntu

---

### Post by metalf8801 on 2010-07-12
> **mylesmadness said:**
> [http://www.pdfonline.com/convert-pdf-to-html/default.aspx](http://www.pdfonline.com/convert-pdf-to-html/default.aspx)

Thats a online version, I don't think there is a offline program for ubuntu

Thank you but I still think there is a native program that will convert PDF or HTML. Does anyone else have any ideas? 

Thanks again 
Dan

---

### Post by nmaster on 2010-07-12
isn't this exactly what you want?

[http://www.ubuntugeek.com/howto-convert-pdf-files-to-html-files.html](http://www.ubuntugeek.com/howto-convert-pdf-files-to-html-files.html)

---

### Post by Penguin Guy on 2010-07-12
You can use [poppler-utils]("apt:poppler-utils") to do the job, it's a command-line program though so you'll have to open the terminal and type:
```
pdftohtml -c input.pdf output.html
```
If you want to be able to do it graphically then you'll have to install [poppler-utils]("apt:poppler-utils"), download the attached script, put it in [FONT="Courier New"]~/.gnome2/nautilus-scripts/[/FONT] and restart Nautilus. You should then see a right click option '[COLOR="Green"]Scripts -> PDF->HTML[/COLOR]'.

---

### Post by metalf8801 on 2010-07-13
> **Penguin Guy said:**
> You can use [poppler-utils]("apt:poppler-utils") to do the job, it's a command-line program though so you'll have to open the terminal and type:
```
pdftohtml -c input.pdf output.html
```
If you want to be able to do it graphically then you'll have to install [poppler-utils]("apt:poppler-utils"), download the attached script, put it in [FONT="Courier New"]~/.gnome2/nautilus-scripts/[/FONT] and restart Nautilus. You should then see a right click option '[COLOR="Green"]Scripts -> PDF->HTML[/COLOR]'.

Sounds great but I don't see a right click option even after I put the script in  ~/.gnome2/nautilus-scripts/   and log out and log back in 
Do you have any ideas what I should try to do to get it to work? 

Thank you 
Dan

---

### Post by metalf8801 on 2010-07-13
PS using ```
pdftohtml -c input.pdf output.html
``` works great

---


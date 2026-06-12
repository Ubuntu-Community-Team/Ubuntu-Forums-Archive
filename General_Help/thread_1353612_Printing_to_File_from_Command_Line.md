---
title: "Printing to File from Command Line"
date: 2009-12-13
forum: General Help
---

### Post by nmaster on 2009-12-13
I really like being able to print to a pdf from the GUI, but how can I do this from the command line.  I've seen a bunch of things showing how to do this with cups-pdf, but I don't see why this is necessary.  If I can select "Print to File" from a GUI, how can I do this using "lpr"?

---

### Post by nmaster on 2009-12-13
just so you know, I have turn a lot of scanned documents into pdfs so doing this through the GUI would be really tedious.  the command line would definitely better.

---

### Post by nmaster on 2009-12-13
okay... so slight change in question.  I've decided to try cups-pdf.  however nothing ever goes to ~/PDF.  at first the folder doesn't exist, so then i mkdir it but there is never anything in the folder.  i never get errors when i run "lpr -P PDF file" or "lp -d PDF file".  what the what...

---

### Post by nmaster on 2009-12-13
just so you know, i did what it says here: [http://hydtech.wordpress.com/2009/03/17/how-to-print-to-pdf-in-ubuntu-intrepid-ibex-and-jaunty-jackalope/](http://hydtech.wordpress.com/2009/03/17/how-to-print-to-pdf-in-ubuntu-intrepid-ibex-and-jaunty-jackalope/)

---

### Post by juancarlospaco on 2009-12-13
OMG, you are talking to yourself, self-support :)

---

### Post by nmaster on 2009-12-13
> **juancarlospaco said:**
> OMG, you are talking to yourself, self-support :)

lol, yeah and i just solved it by myself too!  if anyone else has this problem this is what you should do:
```

sudo apt-get install cups-pdf
sudo chmod +s /usr/lib/cups/backend/cups-pdf
sudo mkdir ~/PDF
sudo chmod 755 PDF

```

now it works!

---

### Post by Primefalcon on 2009-12-13
Nice. 

You know talking to yourself is the first sign of madness, OMG most of the world is crazy, oh well to be sane in an insane world is to be truly insane.

Actually I just wanted to say thx for posting this, it's actually something I'll find useful myself, Thank you!

---

### Post by nmaster on 2009-12-13
This is ridiculous, I've completely solved my own post, but this might be an improvement.  

Instead of doing 'lpr -P PDF filename' and then having to move the printed file, I wrote this script.  I made the PDF folder hidden so you'll have to change /etc/cups/cups-pdf.conf but now you can just enter 'lpPDF filename' and it will show up in the current directory.

```

#! /bin/sh                                                                      
# prints file to pdf and moves it to the current directory                      
# 'lpPDF file' will print file to a pdf and move it to the current directory    

##########################################################################      
# set-up:       sudo apt-get install cups-pdf                                   
#               mkdir ~/.PDF                                                    
#               go into /etc/cups/cups-pdf.conf and change OUT to ~/.PDF        
##########################################################################      

name=$(echo $1 | cut -d'.' -f1);
new_file="${name}.pdf";
lpr -P PDF $1 && mv  ~/.PDF/$new_file .


```

---


---
title: "I want to modify PDF files!"
date: 2011-06-04
forum: General Help
---

### Post by SwingKid on 2011-06-04
I want to modify and make smaller changes in a PDF document. How do I do that in Ubuntu?? I have heard it is possible with Open Office when you have some extensions to it? I have tried PDF Mod but you can't make much with it. I need to change text inside the document. Please help me.

---

### Post by wgarcia on 2011-06-04
I've used PDF Editor in the past and it is not bad, but I remember it was sort of hard to figure out how to do some things (despite it has a graphical interface). 

Now I use a commercial application called PDF Studio.

---

### Post by SwingKid on 2011-06-04
> **wgarcia said:**
> I've used PDF Editor in the past and it is not bad, but I remember it was sort of hard to figure out how to do some things (despite it has a graphical interface). 

Now I use a commercial application called PDF Studio.

Is PDF Studio available for Ubuntu? Is it possible to edit the text in the pdf file with it? Or with PDF Editor?

---

### Post by HermanAB on 2011-06-04
Howy,

For small changes, The Gimp is the easiest.

OpenOffice has a PF Edit plugin, but it cannot handle large files.  If a file is large, you should break it into smaller chunks with something like PDF Shuffler first.

---

### Post by jamesisin on 2011-06-04
Of course if the PDF file contains images and not text you'll run into a dead end.  Something to keep in mind.

---

### Post by mike555 on 2011-06-04
I use "Xournal" for annotating .pdf's .

---

### Post by pksadiq on 2011-06-04
you may try   libreoffice-pdfimport or  openoffice.org-pdfimport packages according to  which ever Office you use as it was said, It worked for me, it also allows you to export back to pdf

install pdfimport by typing the following in terminal:
```
sudo apt-get install openoffice.org-pdfimport
```

or you can also find the package in Syanaptic or Ubuntu software center

and then open the pdf file using open office

---

### Post by SwingKid on 2011-06-04
> **HermanAB said:**
> Howy,

For small changes, The Gimp is the easiest.

OpenOffice has a PF Edit plugin, but it cannot handle large files.  If a file is large, you should break it into smaller chunks with something like PDF Shuffler first.

My file is only 33.4 kb. That would be considered small, right? Can you open PDF files in Gimp? :confused:
I tried to open my pdf file in Open Office but it was no use. How do I get this PF Edit Plugin for Open Office? Please.

I received this message in OO:

%PDF-1.4
%&#65533;&#65533;&#65533;&#65533;
2 0 obj
<</Filter/FlateDecode/Width 396/BitsPerComponent 8/Height 85/Subtype/Image/Length 31819/ColorSpace/DeviceRGB/Type/XObject>>stream
x&#65533;&#51015;\&#65533;&#65533;&#65533;&#65533;#l&#65533;&#1917;w&#65533;&#65533;jW&#65533;M&#65533;l&#65533;V&#65533;U&#65533;&#65533;&#65533;#L##b0&#B#H&#65533;)&#65533;!y&#65533;C}#&#65533;###l&#65533;#&#65533;[&#65533;[V&#65533;v&#764;&#65533;3s&#65533;J&#65533;!&#1540;<&#65533;#&#65533;s&#65533;&#65533;j}&#65533;&#1817;3&#65533;&#65533;;gf#c#&#65533;&#65533;Y&#65533;&~.&#65533;\&#65533;&#290;&#65533;~&#65533;#&#65533;#&#65533;s&#65533;&#65533;#&#65533;U&#65533;&#65533;&#1221;'&#1617;&#65533;#&#65533;&#65533;#+&#65533;&#65533;&#65533;:&#65533;|&#65533;&#65533;&#65533;&#65533;{#&#65533;>#L&#65533;&#65533;F&#65533;{&#65533;&#65533;_#&#65533;&#65533;&#65533;#&#457;y&#913;{&#65533;g&#65533;&#65533;~&#65533;q&#65533;&#65533;&#65533;&#65533;]>&#65533;&#65533;&#65533;&#65533;
&#65533;#&#65533;&#65533;#&#65533;S&#65533;&#65533;YY&#65533;G&#65533;&#65533;#&#65533;l&#65533;&#65533;&#65533;s&#65533;#]##(&#65533;w#&#65533;h&#7919;&#65533;e&#1324;&#65533;&#1727;&#65533;f#u&#65533;&#65533;#&#65533;&#65533;&#65533;;}&#65533;&#65533;2&#65533;,&#65533;f&#65533;?&#65533;f&#65533;&#65533;&#65533;&#65533;#&#65533;&#65533;#&#65533;s&#65533;&#65533;";&#65533;&#65533;#&#65533;&#65533;&#65533;&#65533;E&#65533;YF&#65533;&#1679;g&#2006;&#65533;}&#65533;&#975;&#65533;&#65533;#>&#65533;Q&#65533;?&#65533;&#65533;&#65533;&#18389;}g&#65533;7&#744;Y&#65533;_&#65533;YF}3&#65533;&#65533;.&#861;e&#65533;l=j&#65533;~R&#65533;#P&#65533;#E&#65533;#&#65533;&#65533;ge&#2006;&#65533;&#65533;2j&#65533;&#65533;&#65533;&#522;&#65533;&#65533;&#65533;d&#1281;&#65533;Jh#]&#65533;&#65533;&#65533;o&#65533;GM&#65533;&#65533;&#65533;&#65533;8k?#&#65533;#UU&#65533;&#65533;x&#1378;&#65533;0&#65533;&#65533;&#65533;&#65533;Q&#65533;#&#65533;h#&#65533;
o&#65533;&#65533;0U&#65533;&#55034;#F&#65533;&#1443;f2&#65533;&#65533;&#65533;&#65533;&#65533;&#1569;&#65533;&#65533;K#&#65533;&#65533;&#65533;&#65533;&#65533;M&#65533;#&#65533;&#65533;&#65533;W&#65533;N¾q#'&#65533;IQ"&#65533;J&#65533;&#65533;e&#65533;&#65533;&#65533;e&#1324;&#65533;t&#65533;#&#65533;(&#65533;x&#65533;&#65533;Phj&#65533;##&#65533;Jp

---

### Post by jamesisin on 2011-06-04
Maybe this is what you are seeking?

[http://extensions.services.openoffice.org/project/pdfimport](http://extensions.services.openoffice.org/project/pdfimport)

---

### Post by SwingKid on 2011-06-04
> **jamesisin said:**
> Maybe this is what you are seeking?

[http://extensions.services.openoffice.org/project/pdfimport](http://extensions.services.openoffice.org/project/pdfimport)

Yes. Which Linux version should I click? Linux x86-64 or just Linux?

Thank you so much.

---

### Post by jamesisin on 2011-06-04
Are you running 64 bit Ubuntu?

---

### Post by ugm6hr on 2011-06-04
Consider [http://www.pdfescape.com/](http://www.pdfescape.com/) if it's a one-off PDF.

---

### Post by SwingKid on 2011-06-04
> **jamesisin said:**
> Are you running 64 bit Ubuntu?

Nevermind. It says "502 Bad Gateway" when I try to download any of the links :(. What do I do now?

---

### Post by jamesisin on 2011-06-04
Sorry, man.  That's looking like an Oracle server problem.  You might do another Google search for that extension, see if there is a better download location.  Or maybe you'll have to wait for Oracle to fix whatever they need to fix.

---

### Post by linuxinstalledfromhdd on 2011-06-04
> **SwingKid said:**
> I want to modify and make smaller changes in a PDF document. How do I do that in Ubuntu?? I have heard it is possible with Open Office when you have some extensions to it? I have tried PDF Mod but you can't make much with it. I need to change text inside the document. Please help me.

Have you installed all of the different kinds of PDF editors available?

[http://cinderbox.net/2011/03/23/list-of-pdf-editing-tools-for-ubuntu-10-10/](http://cinderbox.net/2011/03/23/list-of-pdf-editing-tools-for-ubuntu-10-10/)

---

### Post by SwingKid on 2011-06-04
> **jamesisin said:**
> Sorry, man.  That's looking like an Oracle server problem.  You might do another Google search for that extension, see if there is a better download location.  Or maybe you'll have to wait for Oracle to fix whatever they need to fix.

No worries. It all worked out with [http://www.pdfescape.com/](http://www.pdfescape.com/) :)

---

### Post by linuxinstalledfromhdd on 2011-06-04
Ok, go ahead and close this thread if you are done. Thanks :O)

---


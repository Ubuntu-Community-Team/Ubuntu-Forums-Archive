---
title: "Printing in colour from bash script"
date: 2010-01-05
forum: General Help
---

### Post by red_lego_man on 2010-01-05
I have an EPSON RX620, it works just fine in Ubuntu and I can redirect text to "lp" and it also prints just fine, but in black only.  
Are there any utilities I can use to print text in different colours from a bash script?  Do I need to insert escape characters or pipe through another program?
Any advice much appreciated!

---

### Post by red_lego_man on 2010-01-06
bump.  Any ideas please?  Search terms for this kind of stuff refer to printing to screen, not to printers.

---

### Post by lmarmisa on 2010-01-06
Maybe this article will help:

[http://www.micahcarrick.com/09-29-2007/gedit-html-editor.html](http://www.micahcarrick.com/09-29-2007/gedit-html-editor.html)

---

### Post by red_lego_man on 2010-01-06
"Customizing gedit as a Web Developer&#8217;s IDE"??  That doesn't really help me print out colour text on my Epson printer from the command line.

---

### Post by lmarmisa on 2010-01-06
[http://projects.gnome.org/gtksourceview/documentation.html](http://projects.gnome.org/gtksourceview/documentation.html)

---

### Post by red_lego_man on 2010-01-06
Could you point out which part of that site I might find information on printers?  Bear in mind I am not looking to program anythin using gtk, I just have a simple text report I'd like to print in colour from the bash shell.

---

### Post by lmarmisa on 2010-01-06
Gedit and GtkSourceView are programs that are able to add colours to text files according to the rules that you define.

Your bash shell could prepare a text without any colour information. Then you can edit this text and the colours will automatically added by gedit according with the rules that you have defined. Finally you have to print the document with colours from gedit. This is the idea that I propose. This procedure is a general solution for all types of printers (not only for your EPSON RX620) or even for pdf files.

---

### Post by red_lego_man on 2010-01-06
Ah, ok, thanks.  However, can I add the colour information in gedit automatically somehow?  I want to be able to put this script in cron and have a nice colour print out waiting on the printer in the morning.

---

### Post by lmarmisa on 2010-01-06
Probably a complete automatic solution is not possible with gedit or other equivalent editor and requires some type of development. You can read this comment in the Features page of GtkSourceView:

[http://projects.gnome.org/gtksourceview/features.html](http://projects.gnome.org/gtksourceview/features.html)

***Language Bindings***

     *       GtkSourceView can be used from many programming languages. Among others,       it has been bound to       *

[LIST]
[*]*[Python]("http://projects.gnome.org/gtksourceview/pygtksourceview.html")*
[*]*[C++]("http://projects.gnome.org/gtksourceviewmm/")*
[*]*[C#]("http://mono-project.com/GtkSharp")*
[*]*[Perl]("http://search.cpan.org/perldoc?Gtk2::SourceView2")*
[/LIST]

---

### Post by red_lego_man on 2010-01-07
Answering my own question...
If I create an html file with colour, I can then use "htmp2ps" to convert the html file to postscript and simply pipe that to lp :

```
html2ps -U -o test.ps test.html
cat test.ps | lp -d Colour-Printer
```

simples.

---


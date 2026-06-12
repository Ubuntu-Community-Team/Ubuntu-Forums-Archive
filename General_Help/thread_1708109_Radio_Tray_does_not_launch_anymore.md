---
title: "Radio Tray does not launch anymore"
date: 2011-03-16
forum: General Help
---

### Post by jaezcurra on 2011-03-16
Hi, suddenly, when I launch Radio Tray 0.6.3 under Ubuntu 10.04.2, nothing happens.  I have uninstalled it and reinstalled and no way.  I went to [http://sourceforge.net/apps/trac/radiotray/report/1](http://sourceforge.net/apps/trac/radiotray/report/1) and did not find anything about that.

I usually maintain Ubuntu by checking daily new updates and I cannot recall anything significant.  The rest of the software/hardware works nominally and, of course, I have restarted and started the computer.

Any suggestion?

---

### Post by jaezcurra on 2011-03-17
Bump.

---

### Post by timgood on 2011-03-17
What happens if you try to start it with command line? Open a terminal and type:

```
radiotray &
```

and post the output. I don't think it's a problem with the program  as I have been running 0.6.3 fine under 10.10 for some time.

---

### Post by jaezcurra on 2011-03-17
joseangel@ubuntu:~$ radiotray &
[1] 31627
joseangel@ubuntu:~$ Loading configuration...
/home/joseangel/.local/share/radiotray/bookmarks.xml
/home/joseangel/.local/share/radiotray/config.xml
Traceback (most recent call last):
  File "/usr/bin/radiotray", line 15, in <module>
    radiotray.main(sys.argv[1:])
  File "/usr/lib/python2.6/dist-packages/radiotray/radiotray.py", line 33, in main
    RadioTray()
  File "/usr/lib/python2.6/dist-packages/radiotray/RadioTray.py", line 52, in __init__
    self.cfg_provider.loadFromFile()
  File "/usr/lib/python2.6/dist-packages/radiotray/XmlConfigProvider.py", line 35, in loadFromFile
    self.root = etree.parse(self.filename).getroot()
  File "lxml.etree.pyx", line 2692, in lxml.etree.parse (src/lxml/lxml.etree.c:49594)
  File "parser.pxi", line 1500, in lxml.etree._parseDocument (src/lxml/lxml.etree.c:71364)
  File "parser.pxi", line 1529, in lxml.etree._parseDocumentFromURL (src/lxml/lxml.etree.c:71647)
  File "parser.pxi", line 1429, in lxml.etree._parseDocFromFile (src/lxml/lxml.etree.c:70742)
  File "parser.pxi", line 975, in lxml.etree._BaseParser._parseDocFromFile (src/lxml/lxml.etree.c:67740)
  File "parser.pxi", line 539, in lxml.etree._ParserContext._handleParseResultDoc (src/lxml/lxml.etree.c:63824)
  File "parser.pxi", line 625, in lxml.etree._handleParseResult (src/lxml/lxml.etree.c:64745)
  File "parser.pxi", line 565, in lxml.etree._raiseParseError (src/lxml/lxml.etree.c:64088)
lxml.etree.XMLSyntaxError: Document is empty, line 1, column 1
^C
[1]+  Salida 1                radiotray
joseangel@ubuntu:~$

---

### Post by timgood on 2011-03-17
Try deleting /home/joseangel/.local/share/radiotray/bookmarks.xml and
/home/joseangel/.local/share/radiotray/config.xml and then restarting radiotray. Any joy?

---

### Post by jaezcurra on 2011-03-18
That's it!!!  Thank you very much!!!

---

### Post by timgood on 2011-03-18
It is my pleasure!

---

### Post by True_Snake on 2011-07-30
Thanks guys,
I had the same problem and your solution worked
I also deleted the suggested files and radio tray is back up and running.

greets

---

### Post by puigpuig on 2012-11-14
The same for me: I had the same problem and your solution worked well for me. Thank you!

---

### Post by nothingspecial on 2012-11-14
Old thread.

Closed.

---


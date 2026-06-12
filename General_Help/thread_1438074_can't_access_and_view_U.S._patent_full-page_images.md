---
title: "can't access and view U.S. patent full-page images"
date: 2010-03-24
forum: General Help
---

### Post by x19mark on 2010-03-24
Hi,

I want to be able to access and view U.S. patent full-page images (of old patent applications), using ubuntu and Firefox. According to the United States Patent and Trademark Office Web site, I "must have a TIFF image viewer plug-in installed in [my] Web browser to view and print these images." :sad:

Here's what I've done and thought about doing, so far:


[LIST=1]
[*]I've looked in Mozilla's Web site for the right add-on;
[*]I've tested Google Chrome (the Web browser);
[*]I've checked out the Plugger Web site--I don't know whether Plugger is intended for ubuntu and/or Firefox;
[*]I've checked out the alternatiff Web site--its plug-in appears to be for only Windows;
[*]I've checked out the interneTIFF Web site--its plug-in appears to be for only Windows;
[*]I've considered trying Opera (the Web browser);
[*]I've wondered whether I could somehow get Internet Explorer 8 to work under WINE;
[*]I've considered going back to Windows; :cry:
[*]I've considered going back to my Apple Mac mini;:frown:
[*]I've considered just forgetting the whole thing!
[/LIST]
What's the best way to proceed, please? (Please don't tell me to go back to Windows or Mac OS X!!)

Help!!!
 
Mark

---

### Post by darolu on 2010-03-24
```
$ sudo apt-get install libtiff-tools
```

or

[http://tiff-plugin.vinay.in/](http://tiff-plugin.vinay.in/)

[http://sourceforge.net/projects/tiff-plugin/](http://sourceforge.net/projects/tiff-plugin/)

and (this one has .deb file):

[http://www.mirrorservice.org/sites/download.sourceforge.net/pub/sourceforge/t/project/ti/tiff-plugin/tiff-plugin/0.4-1/](http://www.mirrorservice.org/sites/download.sourceforge.net/pub/sourceforge/t/project/ti/tiff-plugin/tiff-plugin/0.4-1/)

---

### Post by x19mark on 2010-03-24
Hi,

Thank you very much, Darolu!!

It works!! I downloaded the Mozilla TIFF plug-in from sourceforge.

Mark

---

### Post by Naggobot on 2010-05-16
For some reason installing the libtiff-tools through

<code> $ sudo apt-get install libtiff-tools <code>

did not do the trick for me in 10.04 lucid and firefox 3.6.3. I installed Aspator add-on to firefox but please note that it wants an e-mail address. 

I would recommend using this add-on only if you have an extra e-mail address you are willing to sacrifice in case using this add-on causes a spam flood. 

With asparator you can save the whole patent to pdf file which is handy especially if you need to go through multiple patents. 

When I have time I will try the lib-tiff tools to my other computer which has Karmic 9.10 installed. I'll post the results here.

---

### Post by Naggobot on 2010-05-16
I installed the deb from the mirror mentioned by darolu  and now it works. Repository version is 0.3.9. something and the .deb has newer version. 

Thank you

---


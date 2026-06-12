---
title: "Web Design"
date: 2010-09-13
forum: General Help
---

### Post by RedSingularity on 2010-09-13
I want to create a web page "offline" so that I can put it online on my server at a later date.  How can i do this?  Any software I can use?

---

### Post by dv3500ea on 2010-09-13
You could use [kompozer]("apt:kompozer") for a WYSIWYG interface or just use a text editor to edit the HTML code.

---

### Post by andrew.46 on 2010-09-13
Hi RedSingularity,

> **RedSingularity said:**
> I want to create a web page "offline" so that I can put it online on my server at a later date.  How can i do this?  Any software I can use?

You will need a web editor such as Bluefish and perhaps also a ftp program such as gftp. Both of these can be found in the Ubuntu Repositories. Good luck with your web pages :).

Andrew

---

### Post by fancypiper on 2010-09-13
I use [Bluefish](http://bluefish.openoffice.nl/) and Apache. [HOWTO: Setup an Apache Web Server For Free ($0)]](http://ubuntuforums.org/showthread.php?t=632841)

---

### Post by WorMzy on 2010-09-13
I use Vim or Gedit.

If you plan on making bunch of static (X)HTML pages, then you don't need a server to test it, you can develop it in your home area and move it to your server's directory once it's ready. If you want to build it in python, then each django project comes with it's own little offline test server which you can use to test it. PHP is a little more difficult, but you can probably set up a virtualhost to only serve your test pages if it's accessed through 127.0.0.1.

---

### Post by RedSingularity on 2010-09-13
This program looks great!  How can I add templates to it?

---


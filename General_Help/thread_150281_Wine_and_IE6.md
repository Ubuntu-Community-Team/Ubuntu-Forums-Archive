---
title: "Wine and IE6"
date: 2006-03-25
forum: General Help
---

### Post by cdorrington on 2006-03-25
Hey guys,

I know there's a lot to search on about this, but I'm in a bit of a rush and cannot find a definitive response. (I have Kubuntu on my girlfriend's office PC, and only have tonight to set this up) Could someone please let me know which version of WINE is currently working with IE6? I need it for a few sites which mandate the use of IE, and more specifically ActiveX. 

Also, is there any way to print from IE?

Thanks!!

---

### Post by trotski on 2006-03-25
AFAIK, IE6 has been working on Wine for years.  I use it myself when forced to.  According to Wine's website, any printer properly configured with CUPS should work without any further configuration.  I don't have a printer hooked up myself, so I cannot verify this.

A nice way to get IE6 and other apps working in Wine is the "winetools" utility.

Add this to your sources.list:

**deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/**

Then you can:

**$ sudo apt-get install wine winetools**

---

### Post by aysiu on 2006-03-26
IEs4Linux is a good, quick way to get IE6 installed.
I don't think ActiveX will work, though, even with Wine.

---

### Post by emperon on 2006-03-26
I agree, go for IEs4Linux

---

### Post by cdorrington on 2006-03-26
I have IE working uncuccessfully with the newest version. IEs4Linux fails with the new wine. IE continually locks up and goes to Windows Update as its homepage. I have read about problems like this with the most recent versions of WINE, and was hoping to find out which version can run IE stabally.

---


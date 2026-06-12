---
title: "How to install Microsoft Sharepoint Designer?"
date: 2009-07-26
forum: General Help
---

### Post by Lord Butters I on 2009-07-26
I own a copy of Crossover and have used it to get a copy of Microsoft Office installed on my Ubuntu 9.04 computer.  However, Crossover does not support Sharepoint Designer, a program that I need for my university classes, and my attempts to install it (including through Winetricks and Winedoors) have all failed.

I am using KompoZer at the moment but it is far from ideal; I need Sharepoint.  Can anyone help me out?

---

### Post by Lord Butters I on 2009-07-26
Seriously, I'm terrible at using Wine, that's why I bought Crossover.  Can anyone help me?

---

### Post by Lord Butters I on 2009-07-27
Google is of no help so my only hope is this site, someone HAS to know how to get this to work!

---

### Post by DGortze380 on 2009-07-27
> **Lord Butters I said:**
> Google is of no help so my only hope is this site, someone HAS to know how to get this to work!

I'd suggest a Windows VM if you depend on Windows Software for School.

---

### Post by cefn on 2010-12-01
To clarify the suggestion from DGortze380 you can install a piece of software which runs Windows as a Virtual Machine. I use VirtualBox for virtualisation. An alternative is Qemu, though it's not as easy to set up.

You need to have installation media (DVD/CD) and a license for Windows, but then you can have a mini-windows-os inside of Ubuntu for the rare occasion Windows will give you anything of value.

To make this really usable, you need a CPU which has support for hardware virtualisation...
[http://en.wikipedia.org/wiki/X86_virtualization#Processor](http://en.wikipedia.org/wiki/X86_virtualization#Processor)
...else the x86 chip has to be emulated, which is dog slow.

In my case I had kept the originally-installed windows partition, and can boot that, though this can be harder than you think to set up, there are instructions out there.

On this occasion you're being nicely pummelled by Microsoft's designed incompatibility for all of their technologies with anyone elses. Windows would only give you access into their closed-minded development world. I'm shocked that an educational institution could require you to use Windows in order to just build a website. Did they miss a class of Web 101?

Ask them, do they want their great-grandchildren to buy a Microsoft license to enter nursery, as a ticket to access the world's knowledge? They are being unbelievably irresponsible.

An alternative is to leave the class and learn web development with more capable tools from the internet or a different school. Try Grails, Wordpress, RoR, Google App Engine, NodeJS, learn PHP, Java, anything but Sharepoint.

If you're just editing HTML and CSS, you could do worse than Bluefish. If you can bear the sight of tags, when there's Komodo or Eclipse as validating editors for HTML and CSS, which would be my choice.

---

### Post by ShakeyJake on 2010-12-01
As much as I agree that the poor kid shouldn't be forced into using Windows and should maybe even complain, are you seriously suggesting he leaves his school because of an operating system?

I third the option of using a Windows VM, I have both XP and 7 in VirtualBox, can be really useful sometimes.

---

### Post by dvo_photo on 2010-12-07
Hi I searched this forum and found this thread. I was wondering how do I get Virtual Box to open a CD to install software? Newby Plus

---

### Post by Mark Phelps on 2010-12-08
> **dvo_photo said:**
> Hi I searched this forum and found this thread. I was wondering how do I get Virtual Box to open a CD to install software? Newby Plus

Answer ... by opening your OWN thread with your own question.

The only folks that are going to read THIS thread are those interested in solving MS Sharepoint Designer problems.

---


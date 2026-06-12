---
title: "KDE Not Installed Correctly (so the terminal says)"
date: 2011-05-24
forum: General Help
---

### Post by FormatSeize on 2011-05-24
I've been creating a website of late, and I've decided that I've come far enough along to get actual web development software ([though gedit has served well](http://www.micahcarrick.com/gedit-html-editor.html)). Anyhow, in Gnome, I have Bluefish, which is alright, but I also wanted something for KDE, since I also have Kubuntu 10.04 installed. I did some reading, and decided to see what all the fuss about Quanta Plus was about.

I download the tar file, extract it, but when I run ./configure, it goes through a couple of steps and everything seems to be checking out okay, and then I get an error message that says I am missing kde-config, and that I should check my KDE installation.
 
I didn't do anything abnormal during the Kubuntu installation, so I can't imagine what I could do to check that installation. So then I go tot the INSTALL file, and try the alternative installation ./configure method, and I get an error message that says the the C compiler can't output an executable. I have no idea what that means.

Any help would be appreciated.

---

### Post by linuxinstalledfromhdd on 2011-05-24
Try Kompozer. I'm really happy with the results with it so far and the work that I have done with it.  It's not too much or too little when it comes to HTML composition.  It's just the right application for what I needed to do.  It reminds me of Dreamweaver somewhat. Split screen.  Etc. 

In Terminal:

sudo apt-get install kompozer

---

### Post by ankspo71 on 2011-05-25
Hi,
I'm not sure if this will help because the Quanta Plus version you have downloaded is probably newer than what I am about to suggest, but Quanta Plus is available in Ubuntu's repositories, though it is at version 3.5 for Ubuntu/Kubuntu 11.04. You can get it by installing the package named 'quanta'.

kde-config and kde4-config are both files that can be found on my Kubuntu by using these comands.
```
whereis kde-config
whereis kde4-config
```

oops, made a typo. I meant to say quanta, not quantum

---


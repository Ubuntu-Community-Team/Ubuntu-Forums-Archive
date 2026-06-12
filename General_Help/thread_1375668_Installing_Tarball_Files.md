---
title: "Installing Tarball Files"
date: 2010-01-08
forum: General Help
---

### Post by ..::| Dave89 |::.. on 2010-01-08
I want to install Firefox 3.6 beta, I downloaded it from the Mozilla site, and it's in tar.bz2 archive format.  How do I install this under Karmic?

TIA

EDIT: Would it be OK to have both Firefox 3.5 and 3.6 installed on the same machine?  I wouldn't run them simultaneously.

---

### Post by scouser73 on 2010-01-08
Hi Dave, follow my instructions for setting up Firefox.

[[COLOR="Red"]**Download Firefox 3.5.7**[/COLOR]]("http://www.mozilla-europe.org/en/firefox/")

**1** - Right click & Extract the Firefox tar.bz2

**2** - Enter **gksudo nautilus** in Terminal

**3** - Copy & paste the Firefox file that you have just extracted to **/opt**

Enter these commands in Terminal

> sudo -i
Enter your password if asked
> cd /opt
> chown -R username firefox
[COLOR="Red"]**The username is your name**[/COLOR]

**4** - Right click on the Ubuntu start logo, select **Edit Menus**, 

**5** - Highlight the Internet sub menu & click New Item

You will now see a small dialogue box appear

**6** - In the Name field, type **Firefox**

**7** - In the Command field type **/opt/firefox/firefox**

**8** - In the Comment field type **Firefox**

You will now have Firefox installed.

As for having Firefox 3.5 & 3.6 on the same machine, I think you won't get any complications.

---

### Post by ..::| Dave89 |::.. on 2010-01-08
OK I've done it, it works.  The Firefox 3.6 launcher hasn't got the Firefox icon, I know how to change it, but where do I find the Firefox icon from the defualt install of Firefox 3.5?

EDIT: I found the icon in /usr/share/pixmaps

---

### Post by ..::| Dave89 |::.. on 2010-01-09
To uninstall the application, I just remove the folder in /opt, right?  Firefox 3.6 RC1 has just come out, and I want to uninstall the beta and install the release candidate.

---

### Post by scouser73 on 2010-01-09
Yes, remove the file in **/opt**

---


---
title: "DVD Rom not recognizing DVDs.."
date: 2009-12-02
forum: General Help
---

### Post by letmekilluplz on 2009-12-02
My DVD-Rom drive isn't recognizing my DVDs. They are legit commercial DVDs and I installed the DVD codecs. Also the DVD-Rom is listed under /media. Its listed as a "cdrom0" though don't know if that makes a difference or not. THanks!

---

### Post by gabo.cr on 2009-12-02
Are you using Totem?
What codecs did you installed?
Do you have a fresh Ubuntu installation?

---

### Post by alvinmoneypit on 2009-12-05
I have a similar problem.  My dvd hardware sees the dvd and lists the title, but movie player doesn't play it and the error message, "could not read from resource" comes up.  

Do I need codecs?

---

### Post by alvinmoneypit on 2009-12-05
Sorry... I'm running a fairly fresh install of 9.04 on a Lenovo N500 w/ dvd burner

---

### Post by Sin@Sin-Sacrifice on 2009-12-05
Bookmark [this]("http://linuxondesktop.blogspot.com/2007/02/13-things-to-do-immediately-after.html") and keep it handy for fresh installs. If you follow the mediabuntu section you should be able to get dvds to play. I've memorized the steps and haven't had a problem since feisty.

---

### Post by alvinmoneypit on 2009-12-05
I tried a method you have on there, but it didn't find it:

sudo /usr/share/doc/libdvdread3/./install-css.sh
[sudo] password for al: 
sudo: /usr/share/doc/libdvdread3/./install-css.sh: command not found

---

### Post by alvinmoneypit on 2009-12-05
Sin,

I got it running by referring to the official manual for Jaunty Jackalope [here]("https://help.ubuntu.com/9.04/musicvideophotos/C/video-dvd.html").

[https://help.ubuntu.com/9.04/musicvideophotos/C/video-dvd.html](https://help.ubuntu.com/9.04/musicvideophotos/C/video-dvd.html)

It's working now, thanks.

---


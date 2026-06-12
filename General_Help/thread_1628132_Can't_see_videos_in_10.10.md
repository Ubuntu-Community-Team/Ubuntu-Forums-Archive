---
title: "Can't see videos in 10.10"
date: 2010-11-22
forum: General Help
---

### Post by ubunt2guy on 2010-11-22
just installed Ubuntu 10.10.  great distro just can't watch videos.  youtube or vimeo or anything...

thanks for the help

---

### Post by matt_symes on 2010-11-22
Hi

Have you installed the Flash plugin for firefox? Get the correct one for the version you have.

[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

Also have you installed the restricted extras?

Open a terminal and type (case sensitive)

sudo apt-get install ubuntu-restricted-extras

Enter your password. It will not be echoed to the screen so you will not see it. This is normal.

Kind regards

---

### Post by dozycat on 2010-11-22
get these packages from the package manager:
openjdk-6-jre
icedtea6-plugin

---

### Post by ubunt2guy on 2010-11-22
ok thanks for the responses

I've installed all that was mentioned.  it worked for youtube but not other file types.

---

### Post by matt_symes on 2010-11-22
Hi

You installed the restricted extras and they installed properly?

Read this.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

What types are not playing?

Kind regards

---

### Post by ubunt2guy on 2010-11-22
this isn't playing

Gnash is the GNU SWF Player based on GameSWF.
Renderer: OpenGL, Cairo, AGG
Hardware Acceleration: XVideo
GUI: GTK2
Media: FFmpeg (avcodec version: 52.2.2)

---

### Post by Verbeck on 2010-11-22
after an ubuntu installation, you should install the 'ubuntu restricted extras' meta pakage
the how to and the reasons why it's not included by default is explained in the link posted above by matt_symes

edit: [flash aid]("https://addons.mozilla.org/en-US/firefox/addon/161939/") is a useful add-on for fixing flash issues

---

### Post by ubunt2guy on 2010-11-22
> **Verbeck said:**
> after an ubuntu installation, you should install the 'ubuntu restricted extras' meta pakage
the how to and the reasons why it's not included by default is explained in the link posted above by matt_symes

edit: [flash aid]("https://addons.mozilla.org/en-US/firefox/addon/161939/") is a useful add-on for fixing flash issues


i did install the ubuntu-restricted-extras though.  some vids work, and some do not.

---

### Post by matt_symes on 2010-11-22
Hi

> this isn't playing

Gnash is the GNU SWF Player based on GameSWF.
Renderer: OpenGL, Cairo, AGG
Hardware Acceleration: XVideo
GUI: GTK2
Media: FFmpeg (avcodec version: 52.2.2)

some vids work, and some do not.Sorry. I am am a bit confused by this. What videos are not working and in what applications are you trying to play them?

Is it some videos in Firefox on a web page?
Is it in Movie Player?

What are the types of video that are not playing?

Can you give examples?

Kind regards

---

### Post by ubunt2guy on 2010-11-28
figureed it all out

i'm a dummy and installed the 32bit not the 64bit drivers.

thanks for the  help

---


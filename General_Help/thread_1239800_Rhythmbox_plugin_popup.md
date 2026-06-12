---
title: "Rhythmbox plugin popup"
date: 2009-08-13
forum: General Help
---

### Post by Altay_H on 2009-08-13
Every time I run Rhythmbox I get a message saying:

> Search for suitable plugin?
The required software to play this file is not installed. You need to install suitable plugins to play media files. Do you want to search for a plugin that supports the selected file?

The search will also include software which is not officially supported.

If I choose Cancel or X out of it, it just pops back up. My only other option is to choose Search, which searches for a suitable codec for about a minute before finding nothing. It says the requested plugin is "Windows Media Audio decoder."

Rhythmbox is able to play ogg, mp3, m4a, and wma without any problems, so I don't know why Rhythmbox seems to think there's a missing codec. Neither Banshee, Totem, nor VLC have this problem. The missing plugin will continue to pop back up every time it's closed as long as Rhythmbox is running. Any advice is appreciated.

---

### Post by Sherlock Holmboy on 2009-10-05
I'm having the same issue

---

### Post by wojox on 2009-10-05
Open Syanaptic and search for:

```
w32 codecs
```

And

```
ubuntu-restricted-extras
```

---

### Post by nutzxian on 2009-10-06
I'm also having the exact same issue. All the itunes aac/m4a files that I created when I used to use windows no longer play on Rhythmbox. Now when I try to play them a window appears asking for "Search for suitable plugin?" This started happening a few weeks ago for no apprent reason. I have the latest versions of w32codecs and ubuntu-restricted-extras installed so I'm pretty sure this isn't the issue. I'm assuming this must be a rhythmbox issue rather than codecs as these files still play fine on Amarok. Any ideas anyone?

---

### Post by nutzxian on 2009-10-23
OK, I've managed to get my aac/m4a files working again. I found this webpage which was of help: [http://www.linuxquestions.org/questions/ubuntu-63/m4a-and-m4p-playback-with-rhythmbox-523497/](http://www.linuxquestions.org/questions/ubuntu-63/m4a-and-m4p-playback-with-rhythmbox-523497/). In the end, all the packages listed on this page were installed except for "gstreamer0.10-plugins-bad". I installed this and all my music files were playin again. Hope this post is of help to others.

---

### Post by vinutux on 2009-10-23
Add mediubuntu repos

---

### Post by slick_nick on 2009-11-05
I am having the same problem. Medibuntu repositories are added (see [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) if you need to do this!), and all gstreamer/w##codecs/etc are installed....

This wouldn't be as much of an issue if Rhythmbox would REMEMBER the list of import errors!

---

### Post by gokalpo on 2009-11-17
Hi,
I removed gnome-codec-install to solve this

---

### Post by Altay_H on 2009-11-19
> **gokalpo said:**
> I removed gnome-codec-install to solve this
That's a brilliant idea. I think it's the best solution. Unfortunately the problem went away on its own when I accidentally deleted my linux partition and used TestDisk to restore it -- not something I would recommend trying unless you want to learn about data recovery the exciting way. I'm not sure why or how that fixed the problem, but it did. Thanks for your post. It looks like a surefire solution to the problem.

---

### Post by Koppie on 2010-02-21
> **gokalpo said:**
> Hi,
I removed gnome-codec-install to solve this

Worked for me too.  Thanks!

---

### Post by parovelb on 2010-02-23
The *sudo apt-get ubuntu-restricted-extras* solved my issue. Thank you BIGubunti knowledge! :D

---

### Post by Eskobar on 2010-04-29
removing gnome-codec-install worked for me as well.  Thanks alot.  I'm using 10.04 Lucid...

---

### Post by krul on 2010-05-05
yes...this works (removing gnome-codec-install).

---

### Post by sdibaja on 2010-05-06
YES!!!!...this worked for me too (removing gnome-codec-install).

---

### Post by rileinc on 2010-09-05
Installing gstreamer0.10-pitfdll stops the codec search pop-up without removing gnome-codec-install. (For me, at least).

---

### Post by reyquito on 2010-11-11
Thankx.  It worked for me as well:

sudo apt-get remove gnome-codec-install

Beast regards,


Q

---


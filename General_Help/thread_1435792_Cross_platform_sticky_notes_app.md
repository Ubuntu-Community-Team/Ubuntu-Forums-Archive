---
title: "Cross platform sticky notes app?"
date: 2010-03-21
forum: General Help
---

### Post by rustyshakelford2 on 2010-03-21
Im looking for a program that will sync my sticky notes between my mac and my ubuntu netbook. Any suggestions?

---

### Post by PC_load_letter on 2010-03-22
I am not aware of any free or open-source software that does exactly what you want. 
Personally I use Gnote (a C++ rewrite of Tomboy) with Dropbox to sync my sticky notes w/ the several Ubuntu computers that I use.

As a partial solution, Thunderbird's calendar plugin "Lightning" can store files in the iCal format. Thunderbird is available for OS-X.

---

### Post by rustyshakelford2 on 2010-03-22
> **PC_load_letter said:**
> I am not aware of any free or open-source software that does exactly what you want. 
Personally I use Gnote (a C++ rewrite of Tomboy) with Dropbox to sync my sticky notes w/ the several Ubuntu computers that I use.

As a partial solution, Thunderbird's calendar plugin "Lightning" can store files in the iCal format. Thunderbird is available for OS-X.


Would their maby be a way to run gnote under osx? I know that you can make qt apps work.

---

### Post by PC_load_letter on 2010-03-22
I just found this, couldn't find it yesterday for some odd reason LOL: [http://live.gnome.org/Tomboy/Installing/Mac](http://live.gnome.org/Tomboy/Installing/Mac)

So, you should be able to run Tomboy on OSX after all, didn't know that.

---

### Post by gesy on 2010-10-31
I use Tomboy in a Dropbox directory and synchronise like this:

in the file "/etc/environment" add this line:

TOMBOY_PATH="/home/your_home_name/Dropbox/tomboy"

Restart the computer !

---


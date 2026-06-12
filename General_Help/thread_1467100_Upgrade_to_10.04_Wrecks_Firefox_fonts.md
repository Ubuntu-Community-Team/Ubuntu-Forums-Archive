---
title: "Upgrade to 10.04 Wrecks Firefox fonts"
date: 2010-04-30
forum: General Help
---

### Post by strange_cathect on 2010-04-30
I'm having a font problem after upgrading to 10.04. For some reason, my firefox fonts are all wrong. If you look at the following attachments, you'll see what I mean. File 1 is Georgia looking fine on Open Office Writer. File 2 is the same font on Firefox, which looks totally wrong. 

Ideas?

---

### Post by tzily on 2010-04-30
I'm having the same 'problem'...

---

### Post by strange_cathect on 2010-05-01
Seems like we're the only ones. Does anyone know a fix here? I've played with my font settings until I'm blue in the face, but nothing works.

---

### Post by Umang on 2010-05-01
Have you tried to install mscorefonts? 

```
sudo apt-get install ttf-mscorefonts-installer
```

---

### Post by strange_cathect on 2010-05-01
I have had them for a long time. On 9.10 the fonts looked basically identical to those in a Windows environment. Now, however, they've been altered after the upgrade to 10.04. Something changed.

---

### Post by Umang on 2010-05-01
Hmm. I thought so too, but didn't really pay much attention to that (got other problems: [http://ubuntuforums.org/showthread.php?p=9207218](http://ubuntuforums.org/showthread.php?p=9207218)) That's wierd though...

---

### Post by strange_cathect on 2010-05-01
GOT IT!

Follow the following steps [here]("http://ubuntuforums.org/showthread.php?p=7616965#post7616965").

1. Go to command line and type sudo nautilus. Enter password.
2. Browse to etc/fonts/conf.d.
3. Delete files that begin with a 10 (only two or three)
4. run: dpkg-reconfigure fontconfig

After, close firefox and then reopen. My fonts are perfect now.

---

### Post by traverlaw on 2010-05-04
> **strange_cathect said:**
> GOT IT!

Follow the following steps [here]("http://ubuntuforums.org/showthread.php?p=7616965#post7616965").

1. Go to command line and type sudo nautilus. Enter password.
2. Browse to etc/fonts/conf.d.
3. Delete files that begin with a 10 (only two or three)
4. run: dpkg-reconfigure fontconfig

After, close firefox and then reopen. My fonts are perfect now.

That did not work.

---

### Post by mmiicc on 2010-05-05
Thanks for the trick. It also enhanced fonts in qt applications (Skype, VirtualBox).

---

### Post by Der Astronaut on 2010-05-06
Thanks for that advice! Works fine :)

---

### Post by B00R4dL3y on 2010-05-11
I have the same problem as well.  The font smoothing isn't working or something in Firefox and Thunderbird.  I even tried installing FF from the daily PPA builds.

Anyways, I resorted to trying Google's Chromium.  It renders everything perfectly so far.

---

### Post by metalfan_ on 2010-07-11
according to:

[https://bugs.launchpad.net/ubuntu/lucid/+source/firefox/+bug/512615](https://bugs.launchpad.net/ubuntu/lucid/+source/firefox/+bug/512615)

this should be fixed by now.

i upgraded yesterday from 9.04 to 9.10 to 10.04. i also created a new user and started his firefox...still ugly fonts.

---


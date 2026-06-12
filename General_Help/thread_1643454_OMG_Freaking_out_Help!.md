---
title: "OMG Freaking out Help!"
date: 2010-12-11
forum: General Help
---

### Post by Christie_k22 on 2010-12-11
I was just trying to change a folder permission so I could move something into a specific folder. /usr/share i beleive. I found a thread on this forum and followed it (yes im still pretty new to Ubuntu) I think the command was something like sudo chmod R770 * I entered my PW and as my screen blinked a couple times. All of a sudden all my icons in my panel were X's and I cant use any programs at all. My friend suggested I try and restart. Which I did. Now its just a blank black screen. I dont know what exactly I did or how to fix it Please help me out!

---

### Post by Habeouscorpus on 2010-12-11
See this thread: [http://ubuntuforums.org/showthread.php?t=1643346](http://ubuntuforums.org/showthread.php?t=1643346)

Try creating a live disc and changing permissions from there.

---

### Post by bodhi.zazen on 2010-12-11
> **Christie_k22 said:**
> I was just trying to change a folder permission so I could move something into a specific folder. /usr/share i beleive. I found a thread on this forum and followed it (yes im still pretty new to Ubuntu) I think the command was something like sudo chmod R770 * I entered my PW and as my screen blinked a couple times. All of a sudden all my icons in my panel were X's and I cant use any programs at all. My friend suggested I try and restart. Which I did. Now its just a blank black screen. I dont know what exactly I did or how to fix it Please help me out!

By far and away the easiest fix is to reinstall. I have seen one person fix this, took a few days, perhaps a week, and I do not know if the fix worked long term.

---

### Post by dcstar on 2010-12-11
> **Christie_k22 said:**
> I was just trying to change a folder permission so I could move something into a specific folder. /usr/share i beleive. I found a thread on this forum and followed it (yes im still pretty new to Ubuntu) I think the command was something like sudo chmod R770 * I entered my PW and as my screen blinked a couple times. All of a sudden all my icons in my panel were X's and I cant use any programs at all. My friend suggested I try and restart. Which I did. Now its just a blank black screen. I dont know what exactly I did or how to fix it Please help me out!

No no NO!. **/usr/share** is a **system folder** that **you should not touch under any circumstances!**

This might fix things (it will set the permissions to what my system has):
```
cd /usr/share
sudo chmod 755 *
```

Do not blindly follow instructions telling you to anything with sudo unless you are happy that you system might get hosed (including this one!)

---

### Post by matt_symes on 2010-12-11
Hi

It wasn't 

sudo chmod -R 770 *
 
was it? I suspect your looking at a reinstall (depending on the folder you were in).

In the future if you want to move some files to /usr/share, or some other system folder, press Alt + F2 and type

gksudo nautilus

to open nautilus with root permissions. Move the files and then close nautilus right away.

Kind regards.

---

### Post by Christie_k22 on 2010-12-12
thankyou all for the quick replies! I am not so much worried about the system itself as much as the data I have on the system. I was planning on reinstalling (on a new hdd) come tomorrow anyways and was just trying something out before doing so. Obviously not what I should have done . . . The other thing I didn't think to mention (and the reason I am doing the other install) is that I have Studio right now and was going to standard distro. Don't believe there is a live cd for studio . . .

---

### Post by HermanAB on 2010-12-12
Well, first backup your data, then re-install.  Trying to fix a mess like that is usually not worth the effort.

---

### Post by Christie_k22 on 2010-12-12
how do i back up data if i cant even get to the desktop? Like I said Im not so much worried about setting everything back up as much as Im worried about all my docs/vids/music/pics/etc

---

### Post by Christie_k22 on 2010-12-12
I just wanted to say thanks again for every ones help and quick responses. Tho everything isnt where I would like it . . . I can rest easy tonight knowing that it will all be ok tomorrow. Don't be surprised if I am on here asking more questions tomorrow. The only 2 people I know that have ever used linux were ones that I introduced to it so don't have any where else to turn when things go wrong . . . <3 you all . . . I'm going to bed! Goodnite everyone!

<3 Christie

P.S. Can someone change the name of this thread to "What not to do"? LAWL!

---

### Post by HermanAB on 2010-12-12
Howdy,

Backup your data using the installation CD.

---


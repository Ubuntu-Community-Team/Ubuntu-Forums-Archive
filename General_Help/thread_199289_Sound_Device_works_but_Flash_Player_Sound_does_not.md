---
title: "Sound Device works but Flash Player Sound does not"
date: 2006-06-18
forum: General Help
---

### Post by calutateo on 2006-06-18
Dear all,

my sound device works well, however, Flash Movies don't play sound.

This is happening since I upgraded from Breezy to Dapper.

Regards, Carsten

---

### Post by Rui Pais on 2006-06-18
hi,
this should be the classic case of no sound on Flash ;)

(assuming that you have installed alsa-oss):

```
sudo gedit /etc/firefox/firefoxrc
```

Find the line with FIREFOX_DSP and replace it to:
> FIREFOX_DSP="aoss"

or you you want the trouble, start firefox (and edit launchers) with:
aoss firefox

---

### Post by calutateo on 2006-06-20
Adding, or modifying, the line FIREFOX_DSP="aoss" in /etc/firefox/firefoxrc had no effect.
However, thank you for the hint
"or you you want the trouble, start firefox (and edit launchers) with:
aoss firefox"

Now firefox works and Skype as well (I hadn't mentioned that Skype had also sound problems, I always reported a Sound Device problem).

Regards, Carsten

---

### Post by calutateo on 2006-06-27
Strange: when I started Skype with aoss, the sound worked really weird. The calling person had a childish voice, and I was told that my voice sounded like that of an old man.

???

---

### Post by Rui Pais on 2006-06-27
Hi,
theres a more complicated method on the how-to section... maybe it work better for your and solve that problem in skype, [check it here]("http://ubuntuforums.org/showthread.php?p=1183793").

But note that looks more like a bug in skype (wrong frequencies synchonization). Have you search for bugs like that?

---

### Post by JoeSchmoe1971 on 2006-07-20
> **calutateo said:**
> Adding, or modifying, the line FIREFOX_DSP="aoss" in /etc/firefox/firefoxrc had no effect.
However, thank you for the hint
"or you you want the trouble, start firefox (and edit launchers) with:
aoss firefox"

Now firefox works and Skype as well (I hadn't mentioned that Skype had also sound problems, I always reported a Sound Device problem).

Regards, Carsten

:-k 

OK, for the rest of us, can you PLEASE explain that part a bit more? I'm having the exact same problems with flash and skype.](*,)  What do you mean by starting firefox and edit launchers with aoss? Thanks:

---

### Post by Sef on 2006-07-21
You need to add alsa-oss.  

Ubuntu: Applications > Accessories > Terminal

sudo aptitude install alsa-oss

Kubuntu: Kmenu > Systems > Konsole

kdesu aptitude install alsa-oss


That's how I got my flash sound on Ubuntu.

---

### Post by Rui Pais on 2006-07-21
> **JoeSchmoe1971 said:**
> :-k 

OK, for the rest of us, can you PLEASE explain that part a bit more? I'm having the exact same problems with flash and skype.](*,)  What do you mean by starting firefox and edit launchers with aoss? Thanks:

Hi, no problem. 
What i mean was (assuming that you already installed alsa-aoss) try first start firefox or skype using a terminal (gnome-terminal, konsole...) typing:
```
aoss firefox
```
and check if that way sound works. 
If thats the case, you can edit your gnome/kde menus using alacarte (On Main Menu -> accessories) or kde equivalent (kmenuedit?)and search for firefox or skype entries, select them and with mouse menu access 'Properties'. There you can edit the 'Command' line. For firefox replace:
'firefox %u' -> 'aoss firefox %u'

For any launchers on desktop it's even easier, just edit them Properties that you can access with the mouse menu from right button.



If starting with aoss from command line didn't work, check [here]("http://ubuntuforums.org/showthread.php?p=1183793")  for another way (more complicated) to solve it.

hope that helps

---

### Post by smultron on 2006-07-21
when I run: sudo aptitude install alsa-oss
It says that alsa-oss isn't available, but another package is directing to it. And that is means that the package is missing, have gone obsolete or is only available from other sources.

What does this mean? aptitude didn't find flashplayer-nonfree either:/

I'm running 6.06 Ubuntu i386.

---


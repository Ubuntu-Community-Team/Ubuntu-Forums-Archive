---
title: "No sound, fresh install 9.04"
date: 2009-08-25
forum: General Help
---

### Post by trikster_x on 2009-08-25
Hello all!  I am having a bit of a problem getting sound to play in Ubuntu - it doesn't.  This is on a fresh install of 9.04 with /home on a seperate partition.  I have followed all the suggestions here, [http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449"), with no luck.  I have checked every thread I can find associated to my problem, but have found no solution.  I previously had 8.04 installed and sound worked perfectly.  I did not upgrade, but completely wiped and reinstalled on my hard drive.  I am including as much info as I think is helpful.  If more is needed, just let me know what and how to get it.  

```
triksterx@triksterx-desktop:~$ aplay -l
aplay: device_list:217: no soundcards found...

```

```
triksterx@triksterx-desktop:~$ lspci -v

02:0f.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)
	Flags: medium devsel, IRQ 17
	I/O ports at c000 [size=32]
	I/O ports at c400 [size=128]
	Capabilities: <access denied>
	Kernel modules: snd-ice1724

```

```
triksterx@triksterx-desktop:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such file or directory

```

I have purged and reinstalled ALSA, as well as recompiling the driver.  I really love the new features in 9.04, but I can't do without sound.  Please help me to avoid reverting back to 8.04.

---

### Post by P4man on 2009-08-25
Perhaps try this:

[http://www.mepis.org/docs/en/index.php/VIA_Envy24PT/HT](http://www.mepis.org/docs/en/index.php/VIA_Envy24PT/HT)

But report a bug anyway.

---

### Post by trikster_x on 2009-08-25
> **P4man said:**
> Perhaps try this:

[http://www.mepis.org/docs/en/index.php/VIA_Envy24PT/HT](http://www.mepis.org/docs/en/index.php/VIA_Envy24PT/HT)

But report a bug anyway.

I reported the bug last night.  Gave that link a try, but still nothing.  After I ran alsactl restore, it said no soundcards found:

```
triksterx@triksterx-desktop:~$ alsactl restore
alsactl: load_state:1608: No soundcards found...

```

---

### Post by trikster_x on 2009-08-25
Anybody?

---

### Post by uylug on 2009-08-25
Have you tried to play a sound as root?

---

### Post by Animal X on 2009-08-25
i had to get the gstreamer plugins (bad, ugly) before my sound would work. This was for RhythmBox on U 9.04

---

### Post by trikster_x on 2009-08-29
> **uylug said:**
> Have you tried to play a sound as root?

How would I go about doing this?  Just start rhythmbox with sudo?  Because I refuse to log in as root.


> **Animal X said:**
> i had to get the gstreamer plugins (bad, ugly) before my sound would work. This was for RhythmBox on U 9.04

Already did that.  This is a system wide problem, not just with audio files.  Thanks for the suggestion, though.


Also, I installed 8.04 yesterday and audio works perfect O.o.t.B.  Is there any way I can transfer all the necessary files over to my 9.04 installation?  Or perhaps a downgrade of ALSA would be a good fix until I can force this version to work?

---

### Post by P4man on 2009-08-30
Im just guessing perhaps its an interrupt sharing issue. Maybe you can go in the bios and see if you can change something related to it. Assign the onboard sound its own IRQ (or the opposite).

---

### Post by tpk on 2009-08-30
I have had a similar problem since I first installed 8.10. I have 9.04 now but still I have the same problem. I cannot get my headphone jack to work. I have looked for every kind of fix and have found nothing that really works. I would like to use my headphones or my surround system but when i plug in, sound still plays through the speakers. It is definitely the right jack. I have more or less resolved myself to the fact that my headphones will never work but I would like to know if there is a workaround that *works.*

---

### Post by trikster_x on 2009-08-30
> **P4man said:**
> Im just guessing perhaps its an interrupt sharing issue. Maybe you can go in the bios and see if you can change something related to it. Assign the onboard sound its own IRQ (or the opposite).

There are no settings to change for my soundcard in my BIOS.  

Does anyone know how to install the ALSA version that is in 8.04?  That one seems to work well with my sound card, and I don't need pulseaudio to listen to music out of two speakers...

---

### Post by P4man on 2009-08-30
Not sure about backporting alsa,  and tbh, I doubt it will help as even lspci gives you a clear hint of a problem ("Capabilities: <access denied>
"), and that doesn't involve alsa or any sound driver. Unless you think that also happened under 8.10 ?

Perhaps one thing you can try still.
Add irqpoll to your kernel parameters. If you dont know how, here is a link :

[https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation](https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation)

---

### Post by trikster_x on 2009-08-30
> **P4man said:**
> Not sure about backporting alsa,  and tbh, I doubt it will help as even lspci gives you a clear hint of a problem ("Capabilities: <access denied>
"), and that doesn't involve alsa or any sound driver. Unless you think that also happened under 8.10 ?

Perhaps one thing you can try still.
Add irqpoll to your kernel parameters. If you dont know how, here is a link :

[https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation](https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation)

irqpoll didn't do anything as far as I can tell.  


```
02:0f.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)
	Flags: bus master, medium devsel, latency 32, IRQ 21
	I/O ports at c000 [size=32]
	I/O ports at c400 [size=128]
	Capabilities: <access denied>

```

This is the output of my sound card in 8.04 Hardy, notice the "Capabilities: <access denied>" here as well.  Yes I do think it is a problem with ALSA, since I am typing this from my hardy partition and I am listening to music right now.  I have done nothing with the sound settings in 8.04.  Therefore, I can only imagine the version included in 9.04 does not support my card, either that or there is a serious bug in ALSA.

---

### Post by trikster_x on 2009-09-02
Anybody have a suggestion on how to backport ALSA?  At this point I just want my sound to work, I don't care what program I have to use.

---

### Post by honey toast on 2009-09-03
[FONT=System]Hello, 
I'm new to the forum. Is it possible to use a windows media app via 'wine' to remedy this? I might be way off base here, but I thought I'd try. I have no sound either on a fresh jaunty install- hp 1030nr.:(
[/FONT]

---

### Post by bwitherell on 2009-09-03
Have you tried upgrading to the latest ALSA version? The one that comes with Jaunty 9.04 is not the latest release.

Here are two websites you should check out for upgrading:

[HTML]http://webupd8.blogspot.com/2009/08/how-to-upgrade-to-alsa-1020-on-ubuntu.html[/HTML]

[HTML]http://ubuntuforums.org/showthread.php?p=6589810[/HTML]

---

### Post by P4man on 2009-09-03
found a bug report on the HP mini not having sound with jaunty:

warning: long read.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/318942](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/318942)

The good news is that apparently a fix was released about a week ago. Im not sure if that would already appear in the update manager (what the difference between "fix released" and "fix committed") ? , but try to do a full system update, and cross your fingers. 

If that fails, there is an elaborate post in there that might fix it, but its not for the faint hearted: check post #63 in there.

---

### Post by trikster_x on 2009-09-04
I have tried to upgrade ALSA, with exactly the same problem popping up.  

My system is up to date.  Still no fix.  That bug report would be great if I had an intel card and could get ALSA to recognise my card.  

I would really like someone who knows how to backport ALSA or perhaps build an older version from source to give me a hand with this, since I am getting almost no help from the bug report I filed.

---

### Post by trikster_x on 2009-09-14
Well, here I am, a month into my sound problem.  The bug report is still absolutely no help.  And to top it off, I had to try some stuff out with very little to work off of for instructions.  Now my install of 9.04 Jaunty is totally fragged.  I would say that I am going to reinstall and start fresh, but I have seen the level of help I am going to get.  

*EDIT*

I found the fix for my problem.  I just needed to stop trying to make 9.04 work like 8.04 did and start making 8.04 work like 9.04 does.  Turns out destroying my install of Jaunty and having to downgrade to Hardy has saved me hours of searching and file modifying, not to mention a great many restarts.  Thank goodness older stuff actually just works with Hardy.

---

### Post by mustard675 on 2009-10-09
> **trikster_x said:**
> *EDIT*

I found the fix for my problem.  I just needed to stop trying to make 9.04 work like 8.04 did and start making 8.04 work like 9.04 does.  Turns out destroying my install of Jaunty and having to downgrade to Hardy has saved me hours of searching and file modifying, not to mention a great many restarts.  Thank goodness older stuff actually just works with Hardy.

this problem isnt fixed at all. why would you label the thread as such? just because you conceded and downgraded your ubuntu distro doesn't mean the rest of us are going to do so.

---


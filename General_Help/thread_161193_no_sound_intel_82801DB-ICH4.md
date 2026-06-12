---
title: "no sound /intel 82801DB-ICH4"
date: 2006-04-16
forum: General Help
---

### Post by mimihu88 on 2006-04-16
Hope any one can help!
the soundcard installed ok no error report,but just no sound


lsmod | grep snd
snd_intel8x0 30144 3
snd_ac97_codec 72188 1 snd_intel8x0
snd_pcm_oss 46368 0
snd_mixer_oss 16128 1 snd_pcm_oss
snd_pcm 78344 4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer 21764 2 snd_pcm
snd 48644 10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore 9184 1 snd
snd_page_alloc 10120 2 snd_intel8x0,snd_pcm

---

### Post by xXx 0wn3d xXx on 2006-04-16
[QUOTE=mimihu88]Hope any one can help!
the soundcard installed ok no error report,but just no sound


lsmod | grep snd
snd_intel8x0 30144 3
snd_ac97_codec 72188 1 snd_intel8x0
snd_pcm_oss 46368 0
snd_mixer_oss 16128 1 snd_pcm_oss
snd_pcm 78344 4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer 21764 2 snd_pcm
snd 48644 10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore 9184 1 snd
snd_page_alloc 10120 2 snd_intel8x0,snd_pcm[/QUOTE]
In terminal type:

sudo alsamixer

Make sure nothing is muted and make everything at max.

---

### Post by mimihu88 on 2006-04-16
n terminal type:

sudo alsamixer

Make sure nothing is muted and make everything at max.

I did what you said but didnot work.
please have a look at my attachment ,anything wrong?

thank you

why ,I can't see my attacment?!


but something did confuse me because I did see two masters one(OO) I can control it but another
(MM) I cannot  control it

---

### Post by mimihu88 on 2006-04-16
My God,I know how to make attachments

---

### Post by mimihu88 on 2006-04-19
I found that I did get some tiny sound by headphone but just tiny almost like no sound
and I cannot use my modem inside the laptop
I guess these two problems have some unknow connection

any one can help?

when I try to test sound "output" alsa and esd I can hear sound by headphone but no for input and I I cannot exit the test except by force

---

### Post by mimihu88 on 2006-04-27
I solved this problem and I get all sound out!!!

I found the solution occasionally.

It is that you must first select "external amplifier"(listed on the volume panel) and unselect it right away.

It make me feel very strange why have to do it but it does just work.

---

### Post by shuaibe on 2007-12-07
strange as it is but the external amplifier trick works for me too ... thanks for your input!!!

---

### Post by Salazar420 on 2007-12-08
And for me, the same. Thanks. It'd odd, because when I saw the external amplifier I figured keeping it enabled wouldn't hurt, and if anything might actually help (I tried turning everything up, googled, etc.,) but apparently I was wrong.

---

### Post by koback on 2008-04-26
This worked for me too. That's a really random solution. lol

---

### Post by azimuth on 2008-04-30
Bingo! It works in Hardy Heron too. You just gotta love Ubuntu forums and Google, what a combination.

---

### Post by usnmustanger on 2008-05-11
Deselecting "External Amplifier" didn't work for me.  Can someone please explain to me **exactly** how you got this to work?  FWIW, I'm using a Panasonic DF-48 Toughbook.
TIA!!!

---

### Post by richNYC on 2008-05-31
Deselecting 'external amplifier' didn't work for me either:(

I'm using Gateway M320 with intel 82801db-ich4 (ad1981b) sound in Hardy 8.04... Thanks;)

PS: I tried some other stuff listed at:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

and it didn't help at all.

---

### Post by rickatnight11 on 2008-06-10
Definitely worked for my Sony Vaio VGN-T160P laptop.

[LIST=1]
[*]Double-click the sound icon from the top panel
[*]Go to Edit->Preferences from the menu bar
[*]Scroll down to the bottom and *check* the External Amplifier (you *do* want this selected; this just lets us change its settings)
[*]Hit Close
[*]You should now have a tab called Switches that you can now click on
[*]External Amplifier should be here, and you can now uncheck it to disable it
[*]Your sound should now work!
[/LIST]

---

### Post by dishguy123 on 2008-06-11
This did it for me!  I have a SONY VAIO VGN-T370P.  Follow above & you'll be all set....thanX a million to ya!!!

---

### Post by slack---line on 2008-06-12
Okay, so any hints on how to solve this under a fresh Xubntu install?

You guys are all talking about menu selections etc. and those you've given sound like they're for KDE and not XFCE4 (the desktop that comes with Xubuntu).

More than happy to do stuff from the CLI and edit files (normally use Gentoo, all these menus and settings are a little alien ;) ).

This is the exact same sound card in a Sony Vaio PCG-5B1M.

---

### Post by slack---line on 2008-06-12
> **slack---line said:**
> Okay, so any hints on how to solve this under a fresh Xubntu install?

You guys are all talking about menu selections etc. and those you've given sound like they're for KDE and not XFCE4 (the desktop that comes with Xubuntu).

More than happy to do stuff from the CLI and edit files (normally use Gentoo, all these menus and settings are a little alien ;) ).

This is the exact same sound card in a Sony Vaio PCG-5B1M.


Okay, found the answer [here](http://ubuntuforums.org/showthread.php?p=5169942).

Basically just turn off the channel "External Amplifier" under alsamixer, then save the configuration (alsactl store 0).

The application mentioned in this guide will just be whatever front-end to alsamixer which you can use the ncurses interface to at the command line.

---

### Post by troupa on 2008-07-15
just to add to this... on my old gateway laptop I had to not only uncheck "External amplifier" but also "line jack sense"  if there's any other "sense" checkboxes you might need to uncheck those as well. :-)

---


---
title: "i am new and have 2 questions"
date: 2006-03-22
forum: General Help
---

### Post by thunderfox933 on 2006-03-22
1. How do i defrag ubuntu if it slows down.

2. i dont get any sound do i need drivers or sumthing

---

### Post by dragonfyre13 on 2006-03-22
1. Ubuntu does a disk check every 30 boots, but that is the closest thing that I have ever seen to a defrag. I believe that defragmenting is only needed if your HD is fragmented, which is a windows thing, not a linux thing.

2. There is a massive host of things that could cause that. The simplest answer is, "probably". Look at what kind of sound card you have, and post it here. I'll try to help you through it.

---

### Post by Ramses de Norre on 2006-03-22
1. ext3 isn't as sensitive to defragmentation as ntfs, so normally you wont need to defrag.

2. Don't really now, mine worked out of the box.. (still only got experience with things I encountered myself)

---

### Post by thunderfox933 on 2006-03-22
it is an intel 82801BA/BAM AC 97 sound card

---

### Post by dragonfyre13 on 2006-03-22
Lemme search for a sec.

---

### Post by dragonfyre13 on 2006-03-22
Go
System > Preferance's > Sound
and tell me if the sound card you have is showing up.

Also, tell me what you see in
System > Preferance's > multimedia System selector

---

### Post by dragonfyre13 on 2006-03-22
Oh, post the result of lspci.

To do that, go to a terminal, and type "lspci" in. Press enter, and then copy/paste the result.

---

### Post by thunderfox933 on 2006-03-22
ok give me 3 mintues i have to boot into ubunu

---

### Post by dragonfyre13 on 2006-03-22
That's fine. Great to have you here, and trying this, by the way. Welcome.

---

### Post by dragonfyre13 on 2006-03-22
do the same thing with "lsmod" as you did with "lspci"

---

### Post by thunderfox933 on 2006-03-22
the card is intel 82801BA-ich2

the defualt sink is ESD-Enligtment sound daemon

the defualt sorce is- OSS- open sound system

the lsipci is

0000:00:00.0 Host bridge: Intel Corp. 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 02)
0000:00:02.0 VGA compatible controller: Intel Corp. 82815 CGC [Chipset Graphics Controller] (rev 02)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 01)
0000:00:1f.0 ISA bridge: Intel Corp. 82801BA ISA Bridge (LPC) (rev 01)
0000:00:1f.1 IDE interface: Intel Corp. 82801BA IDE U100 (rev 01)
0000:00:1f.4 USB Controller: Intel Corp. 82801BA/BAM USB (Hub #2) (rev 01)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801BA/BAM AC'97 Audio (rev 01)
0000:02:08.0 Ethernet controller: Intel Corp. 82801BA/BAM/CA/CAM Ethernet Controller (rev 01)

---

### Post by dragonfyre13 on 2006-03-22
scratch that last one, type this in the terminal instead.

lsmod | grep snd

That's a "pipe" in the middle. it's generally right around the backslash, and you have to press shift to get it.

---

### Post by thunderfox933 on 2006-03-22
this is what is says

snd_intel8x0           30144  3
snd_ac97_codec         72188  1 snd_intel8x0
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  2 snd_pcm
snd                    48644  10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm

---

### Post by dragonfyre13 on 2006-03-22
IEC is an input to certain high end sound cards that support optical (fiber optic) sound feed from such things as DVD players etc.. My sound card is SIS on board and certainly doesn't have ability of using IEC. But Ubuntu turned on those options by default.
To turn off those options, rum "alsamixer" (without quote) in gnome terminal. You can move around each option with your arrow key (right and left key.) Move to every IEC related options, turn off all of those options (use keyboard "m" to turn off.) After turning off hit "Esc" key to save, and type "sudo alsactl store" so that it is saved permanently.

---

### Post by dragonfyre13 on 2006-03-22
By the way, your drivers seem fine, now we are checking configuration of the sound card, and the configuration of how it uses it.

Oh, and check to make sure it's not muted. I worked for an hour one time, and didn't think to look in the upper right corner. ^_^

---

### Post by az on 2006-03-22
[QUOTE=thunderfox933]this is what is says

snd_intel8x0           30144  3
snd_ac97_codec         72188  1 snd_intel8x0
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  2 snd_pcm
snd                    48644  10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm[/QUOTE]
Your drivers are loaded.  Is the sound muted, by chance?  (Is there a speaker icon at the top of your screen and is there a little x on it?  What sliders do you get if you click it twice?

---

### Post by dragonfyre13 on 2006-03-22
Try "aplay -l"

Also, from the wiki:

# Check that sound is unmuted and that the volume is turned up
    *  Unmute everything. I had to unmute "Master Surround" even though I only have two speakers, for example.

---

### Post by thunderfox933 on 2006-03-22
thanks just one more problem how do i play mp3 files it says i need the decoder

---

### Post by dragonfyre13 on 2006-03-22
I know I'm throwing a bunch at you at once, but here is another. This won't report anything back, but it may solve the problem.

"sudo chmod 666 /dev/dsp"

This will require you to type in your password, since you are allowing yourself access to a system file. You aren't doing anything to it, other than allowing access though.

---

### Post by dragonfyre13 on 2006-03-22
Ah, now that's the fun part. Grab easy ubuntu, I'll find the link in a sec, and it will install all your codecs, and a bunch of other useful things, in addition to modifying your repositories, giving you access to a few thousand more programs, and drivers, and libraries...

---

### Post by dragonfyre13 on 2006-03-22
[http://placelibre.ath.cx/keyes/downloads/EasyUbuntu-2.4beta4.tar.bz2](http://placelibre.ath.cx/keyes/downloads/EasyUbuntu-2.4beta4.tar.bz2)

make sure that synaptic is not open when you run this program. Just open it up in fileroller (the default application, just double click) and then extract it to somewhere. go to the folder you extracted it from, and run EasyUbuntu. Have fun, and again, Welcome!

---

### Post by thunderfox933 on 2006-03-22
ok i but i g2g thanks for all your help i will check out the link when i return

---

### Post by dragonfyre13 on 2006-03-22
No problem!

---

### Post by cab1024 on 2006-03-22
[QUOTE=dragonfyre13][http://placelibre.ath.cx/keyes/downloads/EasyUbuntu-2.4beta4.tar.bz2](http://placelibre.ath.cx/keyes/downloads/EasyUbuntu-2.4beta4.tar.bz2)
 go to the folder you extracted it from, and run EasyUbuntu. Have fun, and again, Welcome![/QUOTE]
EasyUbuntu did not work with my newly installed system. If it doesn't work fo you either, try EasyBreezy. I still got NULL errors, but the software installed anyway. It did not with EasyUbuntu.

---

### Post by dragonfyre13 on 2006-03-27
[QUOTE=cab1024]EasyUbuntu did not work with my newly installed system. If it doesn't work fo you either, try EasyBreezy. I still got NULL errors, but the software installed anyway. It did not with EasyUbuntu.[/QUOTE]


It's roughly the same thing. They are actually merging right now, so I can't wait for the new version. I hear it is going to have something more polished than a zenity interface.

---

### Post by Nordoelum on 2006-04-04
Adding this to my topics :P

---


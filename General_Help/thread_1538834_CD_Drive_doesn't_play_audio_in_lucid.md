---
title: "CD Drive doesn't play audio in lucid"
date: 2010-07-25
forum: General Help
---

### Post by Michl on 2010-07-25
In 10.04 lucid my SONY CRX 140E drive reads data CDs but does
not even read and audio CDs.  This was not the case in Hardy
and I dual boot and just checked in Windows and audio CDs
are no problem there.

---

### Post by oaxacamatt1 on 2010-07-25
A couple thoughts have come to mind on your issue:
1) Have you loaded the proper codecs for music playback by going to the Software Center and installing the 'Ubuntu restricted extras'?
2) Did your Sony CD drive have a special driver that is needed for full operation in Hardy that you may not have loaded this time around?
3) Goto the command line and type in 'lshw' and look for your CD drive.  Does it have any pertinent info??
HTH,
M

---

### Post by Michl on 2010-07-27
ubuntu-restricted-extra is installed;
I always install all the medibuntu stuff;
I never used any special drivers for it
and everything looks fine in lshw.  It
is recognized as a removeable audio, cd-r
and cr-rw disk drive.

The only problem I had in the past was
that for burning the Sony wouldn't work 
with brasero (data or audio) and that was
a known issue,  but it worked with other cd
burners.

---

### Post by dino99 on 2010-07-27
is it the only one sound issue ?

install gnome-alsamixer and paprefs, then set your prefs into: apps sound alsamixer

---

### Post by Michl on 2010-07-27
> **dino99 said:**
> is it the only one sound issue ?

install gnome-alsamixer and paprefs, then set your prefs into: apps sound alsamixer

It's the only sound issue I know of.  I'm quite sure
it's an issue with reading audio files, not playback.

In any case, both files installed and settings seem ok.

---

### Post by oaxacamatt1 on 2010-07-28
Hey Michl,
Out of curiousity, where is the CD from?  Did you burn it yourself?  What software did you use?  What kind of CD is it? CD-RW?  I only ask because I have had issues with CD-RWs and certain music CDs in the past.  You also mentioned that you don't use Brasero.  What sogtware do you use?
Hmmmm,
M

---

### Post by Michl on 2010-07-28
> **oaxacamatt1 said:**
> Hey Michl,
Out of curiousity, where is the CD from?  Did you burn it yourself?  What software did you use?  What kind of CD is it? CD-RW?  I only ask because I have had issues with CD-RWs and certain music CDs in the past.  You also mentioned that you don't use Brasero.  What sogtware do you use?
Hmmmm,
M

Just trying to play regular music CDs, nothing
burned.  In Hardy I was able to work and play 
ordinary music CDs.  Still can in windoze.

---

### Post by gordintoronto on 2010-07-28
What program are you using to play the audio CD?

I suggest VLC Media Player. You might have to install it from Synaptic or Software Centre.

---

### Post by Michl on 2010-07-29
> **gordintoronto said:**
> What program are you using to play the audio CD?

I suggest VLC Media Player. You might have to install it from Synaptic or Software Centre.

I just logged on to report that VLC will recognize and
play audio cds when I saw your note.  VLC is the
answer.  Rythmbox, Mplayer, Gnome CD master, and 
some others I tried don't recognize audio cds on my PC
(Dell 220; the Sony drive I mentioned above.).  VLC does
and the other one that did was goobox, but goo box seemed
to have a bug.  It didn't eject, and wouldn't play another
CD until you reinstalled the program.

There;s still a difference.  In Hardy I'd insert the
audio CD and a player would open. In Lucid nothing
happens.  I have to open VLC and choose the media, but
then it recognizes the audio cd and I can hit play.

In any case, VLC is the answer.

---


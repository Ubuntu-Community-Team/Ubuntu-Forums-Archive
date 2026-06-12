---
title: "can handbrake be adjusted to recognise .mpg files"
date: 2010-03-15
forum: General Help
---

### Post by Arminius on 2010-03-15
I'm trying to get handbrake to convert some .mpg files to mp4, so I can watch it on my ps3 using mediatomb.

But everytime I click on a .mpg in media tomb, it scans it then says nope not interested.

So is there something I can install that will help handbrake work with .mpg? or is there another container converter I should work with?

---

### Post by howefield on 2010-03-15
If handbrake won't do it, have a look at Winff.

A GUI frontend to ffmpeg which will convert mpg to your desired output. It can be installed with Synaptic Package Manager. Or of course, you can use ffmpeg direct via the command line.

---

### Post by bryanl on 2010-03-15
If Handbrake will not recognize the file, it is either corrupt or needing codecs you do not have installed.

see [medibuntu](https://help.ubuntu.com/community/Medibuntu) as a means to gain the ability to read just about any valid video container and codec.

---

### Post by JohnAStebbins on 2010-03-16
> it is either corrupt or needing codecs you do not have installed
HandBrake doesn't rely on any external codecs for scanning or transcoding.  The live preview feature uses gstreamer which does use external codecs, but this isn't the OP's problem.  Most likely, the mpg file is invalid.  This is a problem you would get more help with on [HandBrake's forums]("http://forum.handbrake.fr/").  And you should make yourself familiar with the activity log.  It will tell you a lot about what it going wrong and it is required in order to get help in handbrake's forums.

---

### Post by Arminius on 2010-03-16
> A GUI frontend to ffmpeg which will convert mpg to your desired output. It can be installed with Synaptic Package Manager. Or of course, you can use ffmpeg direct via the command line.

couldn't find the gui frontend in synaptic, but I tried the command line, and the output files video quality was atrocious.

 and I tried WinFF
but when I clicked on convert, it just came up with Unknown encoder 'libmp3lame'
 in terminal.

so anyone know how to fix WinFF? or more details on how to find ffmpeg's gui?

---

### Post by carlosgs91 on 2010-03-16
.

---

### Post by Arminius on 2010-03-16
thanks
Damnvid seems to read and convert mpeg's with out a problem.
haven't been able to test if ps3 can play them but given the many output choices I would be surprised if none of them were compatible.

---

### Post by LowSky on 2010-03-16
the PS3 should play MPEG just fine. Are you sure the Mediatomb has access to the file. check the file's permissions.

---

### Post by Arminius on 2010-03-18
yes they show up in mediatomb's database, and their file permissions are exactly the same as the avi files that are showing up on the ps3.

Only MPEG's have gone missing

---

### Post by howefield on 2010-03-18
> **Arminius said:**
> couldn't find the gui frontend in synaptic, but I tried the command line, and the output files video quality was atrocious.

What I meant was that Winff is a GUI frontend to the excellent ffmpeg. What was the command you used to output your video ?

> and I tried WinFF but when I clicked on convert, it just came up with Unknown encoder 'libmp3lame' in terminal.

You'll find libmp3lame0 Synaptic.

---


---
title: "Dvd::rip asking for a &quot;mount point&quot;? what is a mount point?"
date: 2011-09-14
forum: General Help
---

### Post by AlexOnVinyl on 2011-09-14
Hi there,

I've been seeing bits and pieces of this term being used around the linux community when copying a disc, be it dvd or cdrom, and I'm not sure what it means to specify a "mount point".

I'm currently trying to use the program Dvd::rip to backup a dvd of mine and it's asking me to specify a "mount point" for my cdrom and mentions something about "fstab"

my biggest concern here is doing something with the mount point would alter how my Ubuntu automounts my cdrom - I want to avoid from doing something that would alter how it reads the discs... so if messing with a "mount point" does that, im not sure i want to mess with that..


I'm sorry, im very new to linux and just learning. please help.

---

### Post by seawolf167 on 2011-09-14
A mount point is just a "mounted" filesystem (of any type - USB, hard drive, cd/dvd, etc.). And yes, I know I shouldn't use the word itself in a definition. Read [here ]("https://help.ubuntu.com/community/Mount")for more information on mounts.

Since you are attempting to backup a dvd, if it is asking for the source mount, you'll want to specify where your dvd is "mounted". This is usually something like

/media/dvd_name
or
/mnt/dvd_name

The actual physical dvd drive is located at

/dev/dvd

---

### Post by AlexOnVinyl on 2011-09-14
> **seawolf167 said:**
> A mount point is just a "mounted" filesystem (of any type - USB, hard drive, cd/dvd, etc.). And yes, I know I shouldn't use the word itself in a definition. Read [here ]("https://help.ubuntu.com/community/Mount")for more information on mounts.

Since you are attempting to backup a dvd, if it is asking for the source mount, you'll want to specify where your dvd is "mounted". This is usually something like

/media/dvd_name
or
/mnt/dvd_name

The actual physical dvd drive is located at

/dev/dvd


So setting a mount point wont change how my system automounts my cds or dvds?

that's mainly what I'm concerned with is how it will affect the mounting settings I have in place that came out of box.

as you can see in the attached picture, that - its asking me to configure something in fstab?

will that alter how my mounting already works??

---

### Post by WyleECoyote on 2011-09-14
looks to me like you have to install the restricted codecs for playing/decrypting dvd's like libdvdcss which is not installed by default because of legal issues.

here for Ubuntu:
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

This is what I use for Debian Wheezy:
[http://debian-multimedia.org/](http://debian-multimedia.org/)

and no it will no affect your automount, but personally when I backup my kids vids I install playonlinux which will add any version of wine and install these apps :

ripit4me
DVD Decrypter 3.5.4.0
DVD Shrink
and FixVTS

just by running ripit4me it will automatically open all apps as needed

using wine version 1.1.38 or 0.9.8

---

### Post by AlexOnVinyl on 2011-09-14
> **WyleECoyote said:**
> looks to me like you have to install the restricted codecs for playing/decrypting dvd's like libdvdcss which is not installed by default because of legal issues.

[http://debian-multimedia.org/](http://debian-multimedia.org/)

and no it will no affect your automount, but personally when I backup my kids vids I install playonlinux which will add any version of wine and install these apps :

ripit4me
DVD Decrypter 3.5.4.0
DVD Shrink
and FixVTS

just by running ripit4me it will automatically open all apps as needed


using wine version 1.1.38 or 0.9.8


I actually have installed the libdvdcss already along with medibuntu package

---

### Post by WyleECoyote on 2011-09-14
did you do this as well?

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

that is the same error I had every time I forgot to install css

If you have done all that, I have no idea what the problem could be but from screenshot it appears to read the dvd drive just fine and I never mess with fstab for cd/dvd drives

---

### Post by AlexOnVinyl on 2011-09-14
> **WyleECoyote said:**
> did you do this as well?

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```that is the same error I had every time I forgot to install css

If you have done all that, I have no idea what the problem could be but from screenshot it appears to read the dvd drive just fine and I never mess with fstab for cd/dvd drives

OH NO! I havent done that, I just got an error about dvd::rip stopping short of a few frames when ripping the movie. Ill try that then update my post.

---

### Post by AlexOnVinyl on 2011-09-14
> **AlexOnVinyl said:**
> OH NO! I havent done that, I just got an error about dvd::rip stopping short of a few frames when ripping the movie. Ill try that then update my post.

Alright I did that. and it installed. now should I be good now?

---

### Post by AlexOnVinyl on 2011-09-14
I got this error message when trying to rip the dvd with Dvd::rip.

"It seems that transcode ripping stopped short.
The movie has 161936 frames, but only 135073
were ripped. This is most likely a problem with your
transcode/libdvdread installation, resp. a problem with
this specific DVD."

any info on this?

---

### Post by WyleECoyote on 2011-09-16
that seems to happen to me a lot too on newer movies, it does rip the whole movie but does not give you the thumbnails for setting the frame size etc.. in the next tab. you can guestimate them then try the rip but sometimes the audio/video gets out of sync, if that happens, I use cat and mencoder from command line to do my conversion like this:

cat moviepart1.vob moviepart2.vob moviepart3.vob > movie.vob

that will add all partial clips into 1 then I use mencoder, which takes a lot to figure out but once you do it is really a life saver I made a 3 pass conversion script but it is far from complete enough to share but look into mencoder here is a place to start:

[http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-mpeg4.html](http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-mpeg4.html)

---


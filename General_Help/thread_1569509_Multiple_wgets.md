---
title: "Multiple wgets?"
date: 2010-09-06
forum: General Help
---

### Post by t0p on 2010-09-06
Imagine: you've opened a terminal and typed in the command 

```

wget -c http://nl3.releases.ubuntu.com/releases/10.04.1/ubuntu-10.04.1-desktop-i386.iso

```Then later on, you forget that you've already started the wget job.  So you open another terminal and type in the same command

```

wget -c http://nl3.releases.ubuntu.com/releases/10.04.1/ubuntu-10.04.1-desktop-i386.iso

```So, there's a file in your home called ubuntu-10.04.1-desktop-i386.iso; and it's getting bigger all the time, being fed by multiple 'mothers'.

When wget has finished with the file, will it be okay?  Will the multiple wgets somehow get it together and downloaded the file correctly?  Or will it be an awful mess of a file, good for nothing but the trash?

The reason I ask: I just realised I had 2 instances of wget both downloading the same file.  I quickly annihilated one of the wgets: now there's only one instance running and it's claiming an ETA of about 60 mins.  Is there any point in downloading the rest of the file?  Or should I just put the poor thing  out of its misery?

Hmm... I think I may continue the download, as an experiment.  But I value any feedback.

---

### Post by kalos on 2010-09-06
You can check the md5 sums to make sure the file downloaded correctly.

```
wget http://releases.ubuntu.com/10.04.1/MD5SUMS
md5sum -c MD5SUMS
```

I was curious myself, and the 7.2 MB file I downloaded was 11 MB, so I guess wget doesn't do the right thing. I generally get my ubuntu ISOs from bittorrent so I don't have to worry about checksumming them myself.

---

### Post by tg3793 on 2010-12-08
Well you think you've got something going on, how about me :-) ... I had **eighteen**[check the attached screenshot] (is that right?) instances of wget _all downloading the same file_?

However this didn't happen because I was forgetful. It happened because I had set up a [COLOR="Green"]cron job[/COLOR] thinking that it would only start if I had ended it already.

I am 95% certain, based on your feedback and my brief experience here, that wget is trashing the file. However I would like to know what's going on _in a deeper sense_ and how I could get this action not to repeat itself so I can set this up in a cron job like I want.

Sometime in the next few minutes however, if something else doesn't pull me away from this, I am going to try to use [COLOR="Green"]aria2c[/COLOR] instead of wget (in my cron job) and see if that fixes it.

---

### Post by tg3793 on 2010-12-08
Ok well I have good news. It appears that this is _only a bug with  wget_ because [COLOR=Purple]**aria2c**[/COLOR] [COLOR=Purple]seems to be able to handle the peculiarity[/COLOR] that  I'm throwing at it. I opened up three terminal windows and ran "aria2c  -c  http://ph.archive.ubuntu.com/ubuntu/pool/universe/z/zynaddsubfx/zynaddsubfx_2.4.0-1_i386.deb"  on each of them. The file size came in exactly at the 1.3MB that it was  supposed to and installed flawlessly. Hope this helps someone.

[COLOR=Gray]I'll add a note to this laboratory experiment just in  case you are thinking what I would probably be thinking. 'No', having  three concurrent downloads directed at the same file did NOT speed  things up any. If anything I wonder if it didn't slow things down a bit  ... And if you aren't familiar with aria2c you should check out the -j  argument for it. You 'are' actually able to speed up downloads and  direct the output to one file if you are downloading from two or more  different locations. I've tried this three times and it's worked great  so far.[/COLOR]

---


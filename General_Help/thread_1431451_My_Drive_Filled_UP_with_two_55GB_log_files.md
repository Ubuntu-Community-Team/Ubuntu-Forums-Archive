---
title: "My Drive Filled UP with two 55GB log files"
date: 2010-03-16
forum: General Help
---

### Post by lmicu on 2010-03-16
Anybody has an idea how to fix this?

I am not a rookie in linux, but I am not an guru. 

I realized that I had 0 k free on my drive and when I search to find out what was the problem this is what I have found.

In /var/log/ I had two 55GB files, one called "user.log" and the other "syslog", since it had 55GB I had to tail it and came out with this:


lucian@lucian-laptop:~/luciserver$ tail log_2ndfile_55G_tail 
Mar 16 15:40:39 lucian-laptop scanadf: io/hpmud/pml.c 375: SetPml channel_write failed ret=31
Mar 16 15:40:39 lucian-laptop scanadf: sane_hpaio_cancel: already cancelled!
Mar 16 15:40:39 lucian-laptop scanadf: io/hpmud/hpmud.c 632: invalid channel_write state
Mar 16 15:40:39 lucian-laptop scanadf: io/hpmud/pml.c 375: SetPml channel_write failed ret=31
Mar 16 15:40:39 lucian-laptop scanadf: sane_hpaio_cancel: already cancelled!
Mar 16 15:40:39 lucian-laptop scanadf: io/hpmud/hpmud.c 632: invalid channel_write state
Mar 16 15:40:39 lucian-laptop scanadf: io/hpmud/pml.c 375: SetPml channel_write failed ret=31
Mar 16 15:40:39 lucian-laptop scanadf: sane_hpaio_cancel: already cancelled!
Mar 16 15:40:39 lucian-laptop scanadf: io/hpmud/hpmud.c 632: invalid channel_write state

and with:

Mar 16 15:39:07 lucian-laptop scanadf: io/hpmud/hpmud.c 632: invalid channel_write state
Mar 16 15:39:07 lucian-laptop scanadf: io/hpmud/pml.c 375: SetPml channel_write failed ret=31
Mar 16 15:39:07 lucian-laptop scanadf: sane_hpaio_cancel: already cancelled!
Mar 16 15:39:07 lucian-laptop scanadf: io/hpmud/hpmud.c 632: invalid channel_write state
Mar 16 15:39:07 lucian-laptop scanadf: io/hpmud/pml.c 375: SetPml channel_write failed ret=31
Mar 16 15:39:07 lucian-laptop scanadf: sane_hpaio_cancel: already cancelled!
Mar 16 15:39:07 lucian-laptop scanadf: io/hpmud/hpmud.c 632: invalid channel_write state
Mar 16 15:39:07 lucian-laptop scanadf: io/hpmud/pml.c 375: SetPml chlucian@lucialucian@lucian-laptop:~/luciserver$ tail log_file_55G_tail 
Mar 16 15:39:07 lucian-laptop scanadf: io/hpmud/pml.c 375: SetPml channel_write failed ret=31
Mar 16 15:39:07 lucian-laptop scanadf: sane_hpaio_cancel: already cancelled!
Mar 16 15:39:07 lucian-laptop scanadf: io/hpmud/hpmud.c 632: invalid channel_write state
Mar 16 15:39:07 lucian-laptop scanadf: io/hpmud/pml.c 375: SetPml channel_write failed ret=31
Mar 16 15:39:07 lucian-laptop scanadf: sane_hpaio_cancel: already cancelled!
Mar 16 15:39:07 lucian-laptop scanadf: io/hpmud/hpmud.c 632: invalid channel_write state
Mar 16 15:39:07 lucian-laptop scanadf: io/hpmud/pml.c 375: SetPml channel_write failed ret=31
Mar 16 15:39:07 lucian-laptop scanadf: sane_hpaio_cancel: already cancelled!
Mar 16 15:39:07 lucian-laptop scanadf: io/hpmud/hpmud.c 632: invalid channel_write state
Mar 16 15:39:07 lucian-laptop scanadf: io/hpmud/pml.c 375: SetPml ch

Now I did:
root@lucian-laptop:/var/log# ps ax | grep scan

and got:
14999 pts/0    R+     0:00 grep scan
15013 ?        S    221:11 scanadf --device-name=hpaio:/usb/hp_LaserJet_3015?serial=00MXBM177501 --mode=Gray --source=Auto -x 210 -l 0 --compression=None -y 297 --resolution=600 -t 0 --batch-scan=yes -o out%d.pnm --start-count=1 --end-count=1


Then I kill -9 15013


Can somebody tell me what has created this mess?

---

### Post by Penguin Guy on 2010-03-16
It appears to be something wrong with [FONT="Courier New"]scanadf[/FONT] - maybe reinstalling will help: [FONT="Courier New"]sudo apt-get update sane[/FONT]

---

### Post by dcstar on 2010-03-17
> **Penguin Guy said:**
> It appears to be something wrong with [FONT="Courier New"]scanadf[/FONT] - maybe reinstalling will help: [FONT="Courier New"]sudo apt-get update sane[/FONT]

Or removing and reinstalling the HP device with the document scanner - something is definitely borked.

---


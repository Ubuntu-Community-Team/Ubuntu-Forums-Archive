---
title: "Safely using dd?"
date: 2010-02-05
forum: General Help
---

### Post by AnonymUser on 2010-02-05
For my project, I need to back up and restore SD card images.

I have been using[FONT=monospace]
[/FONT]```
[FONT=monospace]
[SIZE=3]sudo dd if=/oldimages/sd2gb.img of=/dev/sdb[/SIZE][/FONT]
```[FONT=monospace][SIZE=3]
[/SIZE][/FONT]from what I understand, if I ever end up typing in 

sudo dd if=/oldimages/sd2gb.img of=/dev/**sda**

I'll have a nuked hard drive on my hands, no warnings or 2nd chances.

I was wondering what if anything I could do to avoid that.  Can I rename or alias /dev/sdb somehow? to /dev/sdcard or something along those lines?

---

### Post by tom.swartz07 on 2010-02-05
> **AnonymUser said:**
> For my project, I need to back up and restore SD card images.

I have been using[FONT=monospace]
[/FONT]```
[FONT=monospace]
[SIZE=3]sudo dd if=/oldimages/sd2gb.img of=/dev/sdb[/SIZE][/FONT]
```[FONT=monospace][SIZE=3]
[/SIZE][/FONT]from what I understand, if I ever end up typing in 

sudo dd if=/oldimages/sd2gb.img of=/dev/**sda**

I'll have a nuked hard drive on my hands, no warnings or 2nd chances.

I was wondering what if anything I could do to avoid that.  Can I rename or alias /dev/sdb somehow? to /dev/sdcard or something along those lines?

If you have the card mounted it should be listed in /media/nameofcard ... you could use that path instead?

My best advice is to either triple check the command before you run it, or just make a symbolic link to the device folder that you are running it to and have the of=/symbolic/link/goes/here


Hope this helps!

---

### Post by falconindy on 2010-02-05
You could write a udev rule to recognize SD cards and force a different naming scheme for the nodes, but that seems a little too involved when all you really need to do is take a few seconds to look over the "destroy data" command you're about to run.

To paraphrase a few sigs I've seen on these forums: Linux doesn't hold your hand. It assumes it knows what you're doing.

---

### Post by gmargo on 2010-02-05
> **AnonymUser said:**
> 
I was wondering what if anything I could do to avoid that.

Write a shell script to do the dirty work, so you never have to type it out.

---

### Post by rnerwein on 2010-02-05
hi
please don't use a shell script when using dd and the output ( of= ) is a device !!!
ciao

---

### Post by t0p on 2010-02-05
> **AnonymUser said:**
> For my project, I need to back up and restore SD card images.

I have been using[FONT=monospace]
[/FONT]```
[FONT=monospace]
[SIZE=3]sudo dd if=/oldimages/sd2gb.img of=/dev/sdb[/SIZE][/FONT]
```[FONT=monospace][SIZE=3]
[/SIZE][/FONT]from what I understand, if I ever end up typing in 

sudo dd if=/oldimages/sd2gb.img of=/dev/**sda**

I'll have a nuked hard drive on my hands, no warnings or 2nd chances.

I was wondering what if anything I could do to avoid that.  Can I rename or alias /dev/sdb somehow? to /dev/sdcard or something along those lines?

Three possible solutions:

1.  See if you can use the location name /media/disk (or whatever the SD card is called under /media);

2. Just don't type in /dev/sda.  This is easily done by making sure you've typed /dev/sdb before pressing <Enter>.  The letters "b" and "a" look very different, and the A and B keys are quite far from each other on a QWERTY keyboard;

3. Don't use dd.  Find a program that holds your hand instead.

---

### Post by geirha on 2010-02-05
You can make a little wrapper script that shows some information about the drive you are about to overwrite and ask for confirmation.

Something like this:

```

#!/bin/bash

if (( $# != 2 )); then 
    echo "Usage: ${0##*/} infile outfile" >&2
    exit 1
fi

infile=$1 outfile=$2

fdisk -l "$outfile"

read -p "Really overwrite $outfile (y/N)? "
if [[ $REPLY = [yY] ]]; then
    dd "if=$infile" "of=$outfile"
else
    echo "Aborting."
fi

```

Save it as something like /usr/local/bin/mydd or whatever name you like, make it executable, and just remember to run that script instead of dd ;)

---


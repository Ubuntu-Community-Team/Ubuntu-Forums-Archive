---
title: "/dev/dvd and dev/sr0 Acidrip"
date: 2010-04-21
forum: General Help
---

### Post by xtremedementor on 2010-04-21
Hi,

I am trying to use acidrip to rip some dvds.

DVDs play fine in Mplayer and k9copy detects the dvds as /dev/sr0

In disk utility the dvd drive shows as /dev/sr0/ and mount point as /media/cdrom0/

AcidRip looks for /dev/dvd/ and cant find the DVD drive with an error message "Can't read DVD Track" if i change this to /media/cdrom0 acidrip trys to load but says "no valid files found"

I was looking at this last night and i believe it has something to do with (Please feel free to correct my terminology as i am a nOOb) the following

/dev/sr0/ being the device and /media/cdrom0 being the mount point
AcidRip is looking for a mount point(?) of /dev/dvd/.
I also believe this needs to be set up as a dynamic link?

I am just looking for 
a)some clarification on if what i have said is correct?
b)wether this will solve my problem
c)if so how to set up the dynamic link between /dev/sr0 and /dev/dvd

Thanks in advance for any help as always.

Ubuntu 9.1

---

### Post by dannyboy79 on 2010-04-21
if acidrip can't be configured to look at /dev/sr0 then just create /dev/dvd by creating a symlink /dev/dvd pointing to /dev/sr0 suing this command:
sudo ln -s /dev/sr0 /dev/dvd

that should make the /dev/dvd fake device and it'll point to /dev/sr0. good luck

---

### Post by xtremedementor on 2010-04-22
Thats what i was looking for symbolic link!!

I will try it tonight when i get home.

Thanks

---

### Post by xtremedementor on 2010-04-25
Well no joy there. The symbolic link did not do the trick. The dvd still will not load in acidrip.
It plays fine and other apps see the dvd just not acidrip.

Anyone any ideas?

Thanks

---

### Post by dannyboy79 on 2010-04-26
i am not sure what the real problem is here but this guide seems simple enough.

[http://www.communitytechnology.org.uk/pub/howtoacidrip/howto.html](http://www.communitytechnology.org.uk/pub/howtoacidrip/howto.html)

---

### Post by xtremedementor on 2010-05-02
Thanks dannyboy that has done the trick nicely. acidrip needed to be pointed to the /media/DVD_TITLE.

Much appreciated.

---


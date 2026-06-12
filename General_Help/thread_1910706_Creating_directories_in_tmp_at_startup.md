---
title: "Creating directories in /tmp at startup"
date: 2012-01-17
forum: General Help
---

### Post by lloyd_a on 2012-01-17
I'm running ubuntu 11.04 from a usb stick (on an O2 joggler), and want to have some log files written to /tmp (which I believe is in RAM) to save on usb stick writes. Where is the best place to create folders on /tmp at startup.
 
Thanks
 
Lloyd

---

### Post by gsgleason on 2012-01-17
/etc/rc.local would be my recommendation

---

### Post by lloyd_a on 2012-01-17
does that run before items in rc0.d, as I need the directory in place before that.

---

### Post by Paqman on 2012-01-17
> **lloyd_a said:**
> log files written to /tmp (which I believe is in RAM)

It's not in RAM unless you've put it there, but does get deliberately wiped every boot, which might create the impression of it being in RAM.

---

### Post by lloyd_a on 2012-01-18
> **Paqman said:**
> It's not in RAM unless you've put it there, but does get deliberately wiped every boot, which might create the impression of it being in RAM.
 
Late last night I was beginning to come to the same conclusion. 
 
I guess I can create one at startup:
 
mkdir  /ramdisk
chmod 777 /ramdisk
sudo mount -t tmpfs -o -size-10M tmpfs /ramdisk
 
 
 
Lloyd

---

### Post by Lars Noodén on 2012-01-18
> **lloyd_a said:**
> does that run before items in rc0.d, as I need the directory in place before that.

rc.local runs after all the systemV init scripts.  I don't know how it fares against the Upstart scripts.  You could change when rc.local runs by using update-rc.d to reassign a prioty to it.  It has a script in /etc/init.d/ just like the regular SystemV init scripts.

---

### Post by Paqman on 2012-01-18
> **lloyd_a said:**
>  
mkdir  /ramdisk
chmod 777 /ramdisk
sudo mount -t tmpfs -o -size-10M tmpfs /ramdisk


Nothing to stop you putting /tmp itself onto a ramdisk, of course. I tend to do just that on SSDs, so that all the flipflap in /tmp doesn't get needlessly written to disk.

---

### Post by lloyd_a on 2012-01-19
> **Paqman said:**
> Nothing to stop you putting /tmp itself onto a ramdisk, of course. I tend to do just that on SSDs, so that all the flipflap in /tmp doesn't get needlessly written to disk.
 
Only got 512MB of ram to play with on the joggler, so need to be a bit cautious on size of drive.  Will see how big other files get, and then may move /tmp to ram.

---


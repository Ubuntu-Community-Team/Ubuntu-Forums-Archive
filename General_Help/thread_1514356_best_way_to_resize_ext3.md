---
title: "best way to resize ext3"
date: 2010-06-20
forum: General Help
---

### Post by sunnyl on 2010-06-20
Hi all,

Here is my situation: I have a file server thats running 9.04 desktop using a HighPoint RR2310 card in RAID 5 configuration. Home is mounted on a single ext3 partition on the array, and it works great. The OS is on a separate drive.

I recently added a 4th 500GB drive to the array because I was running out of space - now I've added the new 500GB into the array via the on board BIOS, but I need to extend the ext3 partition to use the space.

The RR2310 requires a driver to be installed for Ubuntu to be able to recognise the array.

Whats the best way to go about doing this? I've looked around and found some options I could try, but had a hard time finding some step-by-step instructions I could follow.


1) I read about SSHing in and unmounting home then running parted, but it would be best if I could use something like GParted, as I'm more comfortable with a GUI disk partitioner. 

2) I haven't found an easy procedure to install the driver onto a live CD so I can resize it from there.

Any pointers appreciated!

---

### Post by Revolutionary101 on 2010-06-20
Are you already able to SSH into your server?

If you are able to just enter this into terminal:

```
ssh -X username@serverip
``` (The -X will give you the ability to launch GUI programs on your computer that are run remotely)

Then once you log into your server enter this into terminal:

```
sudo gparted
```

That will launch Gparted.

Although, I don't know how to install the driver for your RAID card.

---

### Post by sunnyl on 2010-06-21
Thanks...can't believe I didn't think of that beforehand!

I've gone ahead and done the resize. Just a note though, I needed to start gparted before umounting, otherwise putty would throw an error:

```
Xlib: connection to "localhost:10.0" refused by server
Xlib: PuTTY X11 proxy: MIT-MAGIC-COOKIE-1 data did not match
Error: Can't open display: localhost:10
```

I also used the instructions here to get the cleanly unmounted:
[http://ocaoimh.ie/how-to-umount-when-the-device-is-busy/](http://ocaoimh.ie/how-to-umount-when-the-device-is-busy/)

---

### Post by Revolutionary101 on 2010-06-21
I am glad I could help.

---


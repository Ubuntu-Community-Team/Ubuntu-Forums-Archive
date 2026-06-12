---
title: "owfs - can't see directory"
date: 2010-03-04
forum: General Help
---

### Post by MickSulley on 2010-03-04
Hi,

I am trying to get owfs towork reading sensors on a 1-wire network.  I have followed several guides I found, but I always hit a problem with the 1-wire directory tha should be holding the data.  When I try to read it I get a permission error, if I ls -l I see that the permissions are d????????? and all the other data is ? as well, just the d for directory and the name 1-wire are readable.  

What could cause this?  

I have followed 
[https://help.ubuntu.com/community/1wireSoftware](https://help.ubuntu.com/community/1wireSoftware)
[http://10-10-20.blogspot.com/2010/01/installing-configuring-owfs-under.html](http://10-10-20.blogspot.com/2010/01/installing-configuring-owfs-under.html)
and a few other bits that I found.

this is what I get when I run it
[HTML]mick@mick-desktop:/var/lib$ sudo /opt/owfs/bin/owfs -u -F /var/lib/1-wire
DEFAULT: ow_ds9490.c:DS9490_sub_open(555) Opened USB DS9490 bus master at 001/006.
DEFAULT: ow_ds9490.c:DS9490_detect_found(415) Set DS9490 001/006 unique id to 81 F7 AA 2C 00 00 00 B1
fuse: mountpoint is not empty
fuse: if you are sure this is safe, use the 'nonempty' mount option
mick@mick-desktop:/var/lib$ 
[/HTML]
I don't think the 'nonempty' bit is a problem, just that I have run this a few times.


[HTML]
[/HTML]

Thanks

Mick

---

### Post by linuxonbute on 2010-08-19
> **MickSulley said:**
> Hi,

I am trying to get owfs towork reading sensors on a 1-wire network.  I have followed several guides I found, but I always hit a problem with the 1-wire directory tha should be holding the data.  When I try to read it I get a permission error, if I ls -l I see that the permissions are d????????? and all the other data is ? as well, just the d for directory and the name 1-wire are readable.  

What could cause this?  

I have followed 
[https://help.ubuntu.com/community/1wireSoftware](https://help.ubuntu.com/community/1wireSoftware)
[http://10-10-20.blogspot.com/2010/01/installing-configuring-owfs-under.html](http://10-10-20.blogspot.com/2010/01/installing-configuring-owfs-under.html)
and a few other bits that I found.

this is what I get when I run it
[HTML]mick@mick-desktop:/var/lib$ sudo /opt/owfs/bin/owfs -u -F /var/lib/1-wire
DEFAULT: ow_ds9490.c:DS9490_sub_open(555) Opened USB DS9490 bus master at 001/006.
DEFAULT: ow_ds9490.c:DS9490_detect_found(415) Set DS9490 001/006 unique id to 81 F7 AA 2C 00 00 00 B1
fuse: mountpoint is not empty
fuse: if you are sure this is safe, use the 'nonempty' mount option
mick@mick-desktop:/var/lib$ 
[/HTML]
I don't think the 'nonempty' bit is a problem, just that I have run this a few times.


[HTML]
[/HTML]

Thanks

Mick
Don't know if you have solved this. I have just started playing with these have a look at this thread:
[http://ubuntuforums.org/showthread.php?t=220436&highlight=1-wire](http://ubuntuforums.org/showthread.php?t=220436&highlight=1-wire)

---


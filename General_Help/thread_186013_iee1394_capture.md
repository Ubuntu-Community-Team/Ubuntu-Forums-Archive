---
title: "iee1394 capture"
date: 2006-06-01
forum: General Help
---

### Post by rider-m on 2006-06-01
All right, I have Kino installed and only able to run as root.  I can live with that.  When I capture video from my camcorder, the video is VERY jerky and audio is all over the place.  I also installed cinelerra and I am not able to select the DV camera as the source.

I know the machine is enough hp (amd 3800x2) because running XP 64  has no problem with the capture.  Any ideas?

TIA

---

### Post by gratefulfrog on 2006-06-05
it's a long uphill climb, I've been there and know how you feel...

There's probably some config issues...

Check out my web page for help: [http://gratefulfrog.net]("http://gratefulfrog.net")  (maybe broken now, if so try this page: [http://home.tiscali.be/asld0009/PhotoAndVideo/HowToDvd.html]("http://home.tiscali.be/asld0009/PhotoAndVideo/HowToDvd.html")

Also, the cinelerra IRC channel can be very helpful.

---

### Post by fsman on 2006-06-05
Running kino as root is not a good idea.
I've been in discussion with the devs about this. 

Follow the steps in my kino guide and all will be well running kino as a normal user

[http://members.lycos.co.uk/fsman/](http://members.lycos.co.uk/fsman/)

---

### Post by xtacocorex on 2006-06-05
I remember I had to change the permissions of /dev/raw1394 to allow read/write to the firewire port for all users. 

I have yet to try in Dapper since I just installed it Friday night.

It may not be the best fix, but at least it worked for me.

EDIT: I should have read fsman's website before posting, go with that info.

---

### Post by Floydius on 2006-06-08
I am running amd64 6.06 Dapper as well; my Kino will start, but always provides the message when attempting to capture:

"WARNING: raw1394 kernel module not loaded or failure to read/write /dev/raw1394!"

this also occurs if i run Kino as $sudo kino

however, if I run completely as root, i.e.:

$sudo su
#kino

all the sudden I can capture.  On a side note, dvgrab runs as a normal user.

I have already added myself to the group "disk", but no such luck.  Have also changed permissions for /dev/raw1394 to read and write (but not execute) for all users.  any other ideas?  do i need to put up execute permission?  seems a little scary given how much access that gives, but whatever.

thanks in advance

---


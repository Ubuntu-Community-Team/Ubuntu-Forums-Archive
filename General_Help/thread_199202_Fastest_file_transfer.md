---
title: "Fastest file transfer"
date: 2006-06-18
forum: General Help
---

### Post by danpre on 2006-06-18
I have two computers:

1. Compaq with debian 3.1 working as server
2. Laptop with kubuntu dapper

and small cable/wifi router

I'm just wondering what would be fastest files transfer over lan network (from laptop to server and then from server to laptop).

(I need to transfer a lot of files every time I plaing with linux setting - just in case something goes wrong)

Because it is going to be transfer over my own lan - it doesn't have to be safe - I need speed! (about 10GB to copy everytime)

At this time I'm using konqueror with ssh transfer, but I think it a bit slow.

Is there any faster transfer to run on debian server? 

DANIeL

---

### Post by johnnymac on 2006-06-18
Yes, ssh is going to be slow because it's encrypted sent and the decrypted.  IMO you'd be better off just setting up a share and just mount the share and copy that way.  Since it's your own network you'll only be limited by what your nextwork can transfer.  If you have a 10/100MB router and 10/100MB cards then you'll transfer data that fast.

---

### Post by nix4me on 2006-06-18
The share would be NFS.

nix4me

---

### Post by blkish on 2006-06-18
[QUOTE=danpre]I have two computers:

1. Compaq with debian 3.1 working as server
2. Laptop with kubuntu dapper

and small cable/wifi router

I'm just wondering what would be fastest files transfer over lan network (from laptop to server and then from server to laptop).

(I need to transfer a lot of files every time I plaing with linux setting - just in case something goes wrong)

Because it is going to be transfer over my own lan - it doesn't have to be safe - I need speed! (about 10GB to copy everytime)

At this time I'm using konqueror with ssh transfer, but I think it a bit slow.

Is there any faster transfer to run on debian server? 

DANIeL[/QUOTE]

FTP has very low overheads and is pretty robust (you can resume failed transfers). 

i don't know your exact circumstances/hardware and probably you've already considered this, but if you're transfering over your wireless network a crossover cable between the two machines (wired) ethernet would also speed things up considerably.

---

### Post by Jeruvy on 2006-06-19
Maybe I'm barking at the wrong tree, but doesn't OpenSSH server support SFTP and or SCP protocals?

I'm gonna read the docs again...

---

### Post by scxtt on 2006-06-19
yes, you can sFTP and sCP if you've installed OpenSSH server ...

---

### Post by longinus on 2006-06-19
Pure simple FTP is very fast... I would go with that.

One thing... your 10gb of data will always be different? If only part of it changes, you can try RSync... so you don't need to send all the 10gb...

---

### Post by joshrobinson on 2006-06-19
[QUOTE=johnnymac]Yes, ssh is going to be slow because it's encrypted sent and the decrypted.  IMO you'd be better off just setting up a share and just mount the share and copy that way.  Since it's your own network **you'll only be limited by what your nextwork can transfer**.  If you have a 10/100MB router and 10/100MB cards then you'll transfer data that fast.[/QUOTE]

you can only send data as fast as it can be pulled off your hard-drive, and you can only save data as fast as it can be saved to the hard-drive.. i wouldnt tell someone they are gona get a full 100mbps just because the lan can do it

it can bottleneck in there somewhere.. the laptop probibly has a slower RPM hard-drive so that will slow it down

either way 10 gig over a network isnt very bad.. ive sent 300gb across mine and it didnt take but a few hours

---

### Post by tymanthius on 2006-06-19
I frequently use ftp in combination with mc (Midnight Commander) from the command line.  VERY easy to use, and it's fast.  It also has an option to only overwrite if files are of different sizes.  That can be convient.

However, if it's the same files everytime, or even mostly the same files, I'd suggest a system somewhat like this:

on each system, make a script to copy all the important files to an NFS shared directory.

Make a second script to copy from one pc to the other.

And a last script to restore the files.

There a few other things you might need to do in there, but I hope that gets the idea across.

---

### Post by nix4me on 2006-06-19
I still think NFS is the way to go.

FTP as a second alternative.

nix4me

---

### Post by danpre on 2006-06-21
Thanks guys,

NFS is a good idea.

Finally I have set it up:
it was much easier to set it up on server with webmin
than on a client side

with nfs I'm getting 3 times faster transfer than with ssh - maybe it could be faster but server is a bit slow (old 500mhz compaq) and I laptop connects via wifi.

Thx again

danpre

---


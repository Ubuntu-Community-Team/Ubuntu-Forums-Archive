---
title: "Diskless installation"
date: 2006-01-24
forum: General Help
---

### Post by rklauco on 2006-01-24
Hello everyone.

I am searching for an Ubuntu diskless installation.
I have 3 very simmiliar computers in my home network and fourth running a Ubuntu as server.
Right now, all workstations have 512MB of RAM and all of them have HDD for local Ubuntu installation.
I would like to make a network boot to get rid of HDD sound and to run from network storage, but not as a terminal client, but as a full workstation with root located on NFS server.
Is it possible?
I have searched a lot of forums/how-to and did not find any usefull information.
Did anyone managed to run it like this already?
Can you share you knowledge?
Thanx in advance.

---

### Post by tim15856 on 2006-01-25
Try [https://wiki.ubuntu.com/Installation/Netboot](https://wiki.ubuntu.com/Installation/Netboot) for a network install

---

### Post by rklauco on 2006-01-26
[QUOTE=tim15856]Try [https://wiki.ubuntu.com/Installation/Netboot](https://wiki.ubuntu.com/Installation/Netboot) for a network install[/QUOTE]
Well, thanks for the reply, but that's not what I meant.
This is only network installation over pwe, I'd like to run the whole system from network using diskless station.

---

### Post by tim15856 on 2006-01-26
So you're looking for thin client support? [https://wiki.ubuntu.com/ThinClientHowto](https://wiki.ubuntu.com/ThinClientHowto)

---

### Post by rklauco on 2006-01-31
Well, not really.
I am not looking for thin client. I would like to boot regular PC but without disk from the network. I saw a Slackware installation running like this. It's a bit slower, but the diskless operation is a huge plus for me...

---

### Post by Blippe on 2006-03-22
[https://wiki.ubuntu.com/Installation/OnNFSDrive](https://wiki.ubuntu.com/Installation/OnNFSDrive)

You will need to compile your own kernel, with support for booting with your root on a nfs-drive and non-module (as in the kernel) support for your network-card.

---

### Post by rklauco on 2006-03-22
GREAT!
This is what I was searching for!
Thanks again, I knew it must be possible :-)

---

### Post by PhairOh on 2006-03-22
Sorry for coming in on this thread, but I have a question.

I'm having trouble distinguishing the difference between using thin clients and what rklauco actually wants.  Can someone explain?

---

### Post by rklauco on 2006-03-22
The difference is in processor usage.

If you are using thin client, all calculations (starting from Xserver, ending at the office documents) are done by the server side. Client actsw only as dome "display" device.

But in my solution, I have full-featured client workstation, but to keep the noise volume at 0 level, I need the disk to be removed from the station and located at the server.

Basicly, all the processing is done the same way it is on usual workstation, except the disk storage is on the server and the workstation boots over PXE, not from local harddrive.

Can you see the difference?

---

### Post by rklauco on 2007-06-25
Seems like not only myself was interested in:
[https://help.ubuntu.com/community/DisklessUbuntuHowto](https://help.ubuntu.com/community/DisklessUbuntuHowto)

---


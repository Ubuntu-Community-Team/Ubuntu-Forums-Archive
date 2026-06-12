---
title: "Make a backup server from old computer"
date: 2009-10-11
forum: General Help
---

### Post by sickly on 2009-10-11
Hi this is my first post ever on here or anywhere. I have been searching for 2 days now and have not found any useful information or tutorials that can help me with my needs. What i am trying to do is take a old Dell Dimension 2400 that i have and make it so its like a backup for all my files, video's, audio and such. I am running Ubuntu 9.04 on two computers on my network, and do not have the Dell set up yet. I would just like to simply send the files and, or take the files from The Dell when I need to over the network . If someone can help me out and tell me what I need, or point me in the right direction I would be very thankful.

---

### Post by diesch on 2009-10-11
Use NFS. See [https://help.ubuntu.com/9.04/serverguide/C/network-file-system.html](https://help.ubuntu.com/9.04/serverguide/C/network-file-system.html) and [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo) for how to do that.

---

### Post by StuartN on 2009-10-11
> **sickly said:**
> What i am trying to do is take a old Dell Dimension 2400 that i have and make it so its like a backup for all my files, video's, audio and such.

Take a look at the rsync command. At the simplest level you can just open a share on your backup server and each workstation can then use rsync to back up into personal directories.

If you want more security and reliability then you can run the rsync daemon on the server and use rsync protocol from the workstations, or set up ssh on the back and use ssh in rsync. I like the rsync daemon because it seems to have excellent recovery on poor wireless links, others like ssh because it is very secure.

You could use bacula, back-in-time, unison or some other all-in-one backup solution on the workstations.

Personally, I prefer the backup to contain a mirror (or sequence of dated mirrors) of my filesystem, so I can retrieve any file from exactly where I expect it. I don't like compressed archives or any manipulation of my files.

---

### Post by sickly on 2009-10-11
Thanks for the replies. I didn't think I would get an answer so fast lol. But I forgot to mention that i cant run Ubuntu on the dell. It seems it cant handle it. the processor is descent for an old computer P4 2.6 GHZ but only 128 mb of RAM. I tried to install Ubuntu 9.04 twice but all it did was, well nothing. If you know of a good lightweight install that will be good for this let me know. I was lookin at ubuntu server but not sure if im ready for it. But i will read into these options you guys gave me. Thanks

---

### Post by noelvh on 2009-10-11
There is a free NAS OS you can you and I think it might work for you. It's called Free NAS. I have set one up on and old machine and it works really well. I was even able to connect windows XP to it and use offline files.


Noel

---

### Post by solitaire on 2009-10-11
That machine should run ubuntu. You might need the server or alternative disk to install. I've an old dell inspiron 8200 laptop that I'm going to use as a backup server and it runs 9.04 (had both server and desktop at one time) fine.

---

### Post by CharlesA on 2009-10-11
> **solitaire said:**
> That machine should run ubuntu. You might need the server or alternative disk to install. I've an old dell inspiron 8200 laptop that I'm going to use as a backup server and it runs 9.04 (had both server and desktop at one time) fine.

This. I've run the server version on a POS 900 Mhz duron with 128MB RAM.

It didn't run very fast, but when all it's doing is sitting at the logon prompt, you're fine.

---

### Post by sickly on 2009-10-13
Thanks for all the replies guys but i have decided to go with Free NAS. So far its working out for me.

---

### Post by VastOne on 2009-10-13
> **noelvh said:**
> There is a free NAS OS you can you and I think it might work for you. It's called Free NAS. I have set one up on and old machine and it works really well. I was even able to connect windows XP to it and use offline files.


Noel

+1

I was ot aware of NAS OS and just wanted to say thanks!

---


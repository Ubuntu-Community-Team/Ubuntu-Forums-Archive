---
title: "Useful syncing program"
date: 2011-09-29
forum: General Help
---

### Post by megabuffen on 2011-09-29
Hi!

I'm trying to synchronize folders on an Ubuntu server with my desktop PC at home. Before, when I ran Windows 7 on my PC, I used a software called 'Syncback' to do this. What it does is to compare a local directory on my computer with one on the server. Before making any changes, it displays what differences it has detected and allows me to manually change the actions to be taken. The key is that I always know what files will be overwritten.

Is there any kind of software for Ubuntu that can do this? I've tried Conduit and Unison, but Conduit doesn't display any changes, and Unison doesn't even allow me to specify a custom port.

---

### Post by collisionystm on 2011-09-29
I am not sure of any software that will allow you to specify the options you want. However you can try rsnapshot. It uses rsync and you can specify how far back you want to be able to go in time. It does 1 full backup of the directory(s) and then only backs up the bits of file that have changed after that. 

I.E. I have an ubuntu server with a USB drive attached and it runs an rsnapshot on my boxes. I can go to the rsnapshot folder on the drive and choose from 2 weeks worth of folders to get the file back that I want. Because of the way it backs up, it does not use a huge amount of disk space.

---

### Post by megabuffen on 2011-09-29
I'm not looking for a backup tool but rather a sync. I've been trying Unison again and it does seem to do what I want reasonably well, but the "port" text field is still grayed out. I suppose I could solve this by simply mounting the remote filesystem and using it like if it were a local directory, but connecting to a server in Ubuntu doesn't actually mount it; it merely shows up on the desktop. I've tried this command to do a real mount:
> sshfs -p 10 [email]kalle@silvertejp.nu[/email]:/ ~/Desktop/Silvertejp
The problem is that it only works when typed in the terminal. If i create an application launcher with the exact same contents, nothing happens!

---


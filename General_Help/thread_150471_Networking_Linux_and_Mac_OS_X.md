---
title: "Networking Linux and Mac OS X"
date: 2006-03-26
forum: General Help
---

### Post by N'Jal on 2006-03-26
As the title suggests i want to share files between OS X and Breezy, i aim to achieve this over ethernet, i have however managed to get Linux to see files from the OS X machine, but not vice versa.

Linux is networked to the iBook, which in turn is the Linux machines router, the laptop has built in wireless hence the router.

I have tried so many ways of sharing files form Linux (tcp wrappings, netatalk_howl, netatalk etc) but to no avail. I simply want to be able to move my entire audio library over to Linux and make iTunes retireve the song's from the Linux machine (among other reason's, namly the laptop ain't got a big hard drive, the desktop has, and i can back everything i need up onto the linux machine).

Would anyone be able to help me? I'm getting sick of only being able to have a tiny ammout of CD's stored on a computer.

Thanks
Njal

---

### Post by blaroe on 2006-03-26
I can only tell you what I did that worked for me using Breezy and OSX 10.4.5.

On the Ubuntu Box:
[LIST=1]
[*]Ensure you have Samba running on the Ubuntu machine.
[*]Set up a shared folder in *Ubuntu System->Administration->Shared Folders*.
[/LIST]

On the Mac:
[LIST=1]
[*]On the Mac in the *System Preferences->Sharing* menu turn on Windows sharing and set your account to enable windows sharing.
[*]On the Mac open Finder and hit the <Apple>-K key combo.  In the dialog enter **smb://<your Ubuntu box>** and hit enter.
[/LIST]

If you did this correctly, you will  see a choice of shared directories and a login.

Good luck,
b

---

### Post by Dankitymao on 2006-03-26
I currently use NFS for this purpose, and find it performs a bit better than Samba does.  NFS support is built in to OS X, and you can connect to an NFS server the same as you would a Samba server, but using nfs:// instead of smb://.  There are many howtos available on how to set up NFS; for a simple file server setup like this one, basically all you have to do is install the NFS server, and add a line to /etc/exports detailing what directory is to be accessed by NFS...

Also, in iTunes, make sure you turn off the "Copy files to local Library" option (I believe that's what it's called, something along those lines), otherwise the whole point is ruined as it will dutifully copy everying BACK over the network to your iBook.

---

### Post by N'Jal on 2006-03-26
No luck what so ever, i have NFS installed, but can i get a network share working? NNNNNNOOOOOOO.

Every tutorial either assumes prior knowledge or are out of date, i know what i want to achieve, but am only parially sucessfull with it.

If u could give me an easy way to set up NFS ( i decided to stick with that one), i would appriciate it.

---


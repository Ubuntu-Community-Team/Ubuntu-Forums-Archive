---
title: "Call me Mr Stupid, but..."
date: 2006-03-17
forum: General Help
---

### Post by s1mple_M4N on 2006-03-17
Hi all - I've just installed Breezy Badger on a machine on my home network and am enjoying Linux so far. But I have one problem causing me headaches. Hopefully someone can walk me through this...

I have 3 machines at home - 1 x W2K, 1 x XP Pro (simple sharing), and 1 x XP Pro (simple sharing, DSL internet gateway, mp3 storage). I have a folder shared on the mp3 store computer called Our Music which I have been able to mount as a network drive on the other PCs and access the music files as though they were on a physical drive on that computer.

The trouble I'm having is with Ubuntu doing the same thing so I can play these files through xmms.  I can access all network shared folders without problems. I can go through Nautilis and 'Connect to Server' so the folder icon is on the desktop, but they do not appear as a drive when browsing or saving with applications.

I have read many threads on this subject and have tried altering /etc/fstab, as well as install smbfs, etc, but to no avail. I do not want to risk ruining the Ubuntu installation, so I don't really know how reckless I can get with system settings.

Appreciate any help - or perhaps a screen-shot walkthrough??

Thanks in advance,

RoyJ

---

### Post by Jason_25 on 2006-03-17
That's because your apps are not supporting gnome-vfs or it isn't working properly.  There is better support for this in dapper.

---

### Post by skirkpatrick on 2006-03-17
My Breezy is setup to mount my server's Samba shares on bootup.  They appear as drives on my desktop and I can read/write them and even use XMMS or amaroK to access the music on it.  You have to install smbfs then create a mount point and add it to your /etc/fstab.

---

### Post by s1mple_M4N on 2006-03-17
Thanks for that - I have read a thread along those lines and attempted to add to /etc/fstab. I think the problem is that I'm not sure if I have to point it to an actual directory on my Ubuntu machine or not. And the shared folder 'Our Music' may be causing errors because it has a space in it??

---

### Post by rahelvey on 2006-04-25
[QUOTE=skirkpatrick]My Breezy is setup to mount my server's Samba shares on bootup.  They appear as drives on my desktop and I can read/write them and even use XMMS or amaroK to access the music on it.  You have to install smbfs then create a mount point and add it to your /etc/fstab.[/QUOTE]
good thing i was born with ubuntu linux knowledge so i do not have to learn how to do all this stuff it just comes natural
ok sorry for the funny stuff but mount point add to please a little more in depth for us noobs that just came from other distros

---

### Post by Computeruser on 2006-04-25
One of the very first things I do with a Windows install is dump simple file sharing immediately. It is a pain in the butt. Also make sure your Windows userid's have passwords. Then in Ubuntu -> Connect to Server, select Windows Share as the type, enter the Windows machine name without backslashes, enter C$ as the share, and then authenticate. Works for my Ubuntu 5.10 right out of the box. Good luck.

---

### Post by kupajava on 2006-04-28
Sorry, this is a long one... Im having the same problem.

I can browse my windows network shares through nautilus, but they don&#8217;t appear in file operation dialogs. What this means is that although I can see the individual network files, I have to save to the desktop and then copy over to the network share (and vice versa) - I can&#8217;t navigate to the share through the save dialog.

So I tried to mount the share to a local directory.

When I manually mount in the terminal screen, everything goes fine and without errors in the terminal screen but when I navigate to the mount, the folder is displayed as a unknown file and I get an access denied error (even with a gksudo nautilus browser) trying to open it. I know this cannot be the windows side since I can browse this server in nautilus using "connect to server" and everything opens just fine.

any ideas? Im sure I am just missing something obvious but just cant  to get it!

also, I have also tried the whole Mount Windows Shares Permanently with fstab method (//servername/sharename /media/mountname smbfs defaults,uid=1000,gid=1000,credentials=~/.smbcredentials,umask=777 0 0) with the same result. no errors in the terminal with mount -a, but as soon as I navigate to the mount point the folder I created becomes an unknown file that wont open. I know the credential file is correct because it wasnt at first and it errored in the mount -a dialog.  I even get the desktop icon for the mount but it gives me a system error beep and no response when I doubleclick it.

---


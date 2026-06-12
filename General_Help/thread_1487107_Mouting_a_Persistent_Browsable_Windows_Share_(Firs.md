---
title: "Mouting a Persistent Browsable Windows Share (First Post)"
date: 2010-05-18
forum: General Help
---

### Post by Shurafa on 2010-05-18
Warning I am a complete Ubunut N00b so please be gentle with me ;b
 
With that said I am looking for a way to install the equivelent of a network drive in windows.
 
Specifically I have a number of VMs that are stored on my windows server and I would like to be able to run them from Virtual box. I can browse them by using the network icon in places. I can also create a bookmark in both places as well as on the desktop however when I go to add a virtual drive in Virtual Box and try and browse to these network locations they do not show up. Same thing happens if I go to File Open in Firefox and try to browse for my bookmarks on the server.
 
Any assistance with this would be greatly appreciated.
 
PS. As a workaround I have copied a VM to my local ubuntu box and run it locally however I only have enough space on my tiny SSD for one VM.

---

### Post by mac9416 on 2010-05-18
Hi, Shurafa, welcome to UbuntuForums!

Unfortunately, having a network share auto-mount at startup isn't extremely easy; but there are ways to do it. One way is to edit what's called the "fstab" file to include the share. Perhaps an easier way is to use an app such as pysdm to do it for you. 

Since I haven't done either of those, I don't have the knowledge to tell you how. Instead, I'll point you to this page which might be helpful: [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

Hopefully that will help answer your question.

---

### Post by Shurafa on 2010-05-18
Hey Mac thanks for the reply. I am not sure having the share auto mount will help. I can get the windows shares to mount ok. I can access them using the systems file browser through "places". The problem occurs when trying to browse to the network share using an application like virtual box or firefox. If you go to file open file in firefox a file browser opens up (is there a name for this app?). This app shows a list of places on the workstation however it does not show any smb shares in the places menu on the left. Even if you browse to a shortcut created in the desktop folder it shows up as empty.
 
I am looking for a way to get these shares to show up in this app ideally in a persistent manner.
 
Hope this is clear. Thank you for your assistance it is greatly appreciated.

---

### Post by mac9416 on 2010-05-19
OK, so the problem is that you can open the Samba share in Nautilus (file manager) but not Firefox, Virtualbox, etc.

As I understand it, when you access a Samba share in Nautilus, it doesn't mount the partition. It treats the share more like a web server, accessing it and showing you the contents, but not making it a part of your filesystem. If you found a way to mount the Samba share, it would become a part of your filesystem somewhere like /media/smbshare (sorta like when you mount a flash drive), and you could access it with any program that way.

(Someone please correct me if I have any of that wrong.)

But I have no idea how to mount Samba shares, so I would suggest searching Google for something like "mount samba ubuntu." Maybe you'll turn up something useful there.  :)

---

### Post by Shurafa on 2010-05-19
Bingo.
 
Nautalis is able to open and browse the Samaba shares just fine however other applications are not able to see them.
 
My objective is to be able to run a Virtual Machine off of a remote network drive using VirtualBox however VB is unable to see the Samba Shares.
 
I have Googled it several times however I have been unable to find a solution (Thats how I found these forums)

---

### Post by mac9416 on 2010-05-19
When you mount a Samba share, all programs will see that share as just another directory on your filesystem (like in Windows).

Here are a few things I found that may be helpful:

[LIST]
[*][http://ubuntuforums.org/showthread.php?t=280473](http://ubuntuforums.org/showthread.php?t=280473)
The original poster describes how to permanently mount a Samba share. But 2006 is a long time ago, so there's no guarantee that everything will be the same.

[*][https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)
The title decribes exactly what you want to do. However, the instructions seem to be a lot of commands with little explanation of what they're doing. Just the kind of instructions that cause folks to make mistakes.

[*][https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)
That appears to describe the steps much better.

[*][http://www.mattvanstone.com/2006/06/automatically_mounting_smb_sha/](http://www.mattvanstone.com/2006/06/automatically_mounting_smb_sha/)
An oldish blog post laying out the steps very well (as far as I can tell).
[/LIST]

Also, this post seems to confirm what I believed about Nautilus not actually mounting your Samba share: [http://ubuntuforums.org/showthread.php?t=289918](http://ubuntuforums.org/showthread.php?t=289918)

That may seem like an information overload, but I'm sure among all that you'll find the info you're looking for.  :)

---


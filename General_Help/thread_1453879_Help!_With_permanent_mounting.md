---
title: "Help! With permanent mounting"
date: 2010-04-13
forum: General Help
---

### Post by sh0wtym3 on 2010-04-13
I'm taking a computer science class, and the all of the assignments so far have been easy coding stuff (html, css, javascript, etc). Now all of a sudden this new assignment requires us to install VirtualBox and create a virtual machine with Ubuntu as the OS.... Which is kind of unfair as he hasn't showed us how to do ANYTHING and said basically "figure it out". This all looks Chinese to me and is way over my head!!!

Ok, sorry, I'm done venting.



Obviously I figured out how to install the virtual machine and get Ubuntu running on my own, but there are quite a few parts I need assistance with. I don't want to clutter this one thread with all of them so I'll start by just asking for help with permanent mounting. Here are the direct instructions:

> 
3.6 Mounting 
Create a shared directory between your host machine and the guest machine. Edit the ftab le under /etc/ftab to make Ubuntu automatically mount your shared directory when it boots up. Create a directory sharedData under /media/. This is the mount point for this shared directory.
I CHMOD'd the /media/ directory so I could create the folder "sharedData" inside it. Now I have /media/sharedData

I even edited the ftlab file according the instructions I found via Google here:
[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)


... but it's not working. The instructions say:

**"The Windows computer name is *servername*, this can be either an  IP address or an assigned name."**

... But I'm not even sure what *servername* should be, I'm guessing it's the IP address I see when I type in "IPCONFIG" on my windows command prompt? See how lost I am?


Please help a poor lost soul who's about to tear his hair out

---

### Post by Calash on 2010-04-13
First, make sure you are editing /etc/fstab  I see that you typed ftab a couple of times and if you are trying this file it will not work....because that file does not exist.

I go with IP address when working with Windows to Linux mappings, but it really depends on your network.  IP will probably get you working quicker, so go with that for now.

You will need to format the share path something like this 


\\IP.ADDRESS\SHARENAME

Hopefully that will get you on the right track :)

---

### Post by Iowan on 2010-04-13
A couple more links for you:
[http://ubuntuforums.org/showthread.php?t=288534]("http://ubuntuforums.org/showthread.php?t=288534")
[http://ubuntuforums.org/showthread.php?t=1186877]("http://ubuntuforums.org/showthread.php?t=1186877")

---

### Post by sh0wtym3 on 2010-04-13
> **Calash said:**
> First, make sure you are editing /etc/fstab  I see that you typed ftab a couple of times and if you are trying this file it will not work....because that file does not exist.

I go with IP address when working with Windows to Linux mappings, but it really depends on your network.  IP will probably get you working quicker, so go with that for now.

You will need to format the share path something like this 


\\IP.ADDRESS\SHARENAME

Hopefully that will get you on the right track :)

Yep it's "fstab", sorry he misspelled it in his instructions and so did I when quoting him. 

Sorry for the noobish questions, but for IP address, would I put the IP address I see when typing in "IPCONFIG" in the command prompt?

And what would I put for shared name?

The folder I'm trying to share is located at C:/Ubuntu on my windows (host) system.

---

### Post by Calash on 2010-04-14
The IP address will be what you get back from ipconfig, but you have to make sure it is on the same network as the Virtualbox setup.  This will depends a lot on how you configured the guest as well as the physical systems hardware.  

When you created the share on Windows you gave it a name.  By default the name will be the same as the folder, so if you did not put anything in use the folder name.

---

### Post by Morbius1 on 2010-04-14
Are you trying to access the host shared folder using VirtualBox's "Shared Folder" feature or are you trying to simulate mounting a Samba shared folder across a network? There's a difference.

The answers above relate to accessing a Samba shared folder across a lan. To access a VirtualBox Shared Folder on the host it's a different process.

Let's say you identified to VirtualBox the shared folder C:/Ubuntu as "ubuntu"

* Step 1: Create a mount point on the Linux Guest for the Host to live in:*

**sudo mkdir /media/sharedData**

* Step 2: Add a line in fstab to mount the "Ubuntu" shared folder:*

**ubuntu /media/sharedData vboxsf rw,uid=1000 0 0**

* Step 3: Issue a command that will mount all new entries in fstab:*

[B]sudo mount -a

[/B]I guess it depends on the point of the exercise. If it's to use Virtual Box to teach you how to mount a remote share in a real life network then please disregard my post. 

> 3.6 Mounting 
Create a shared directory between your host machine and the guest machine.I've interpreted that statement to mean a "Virtual Box Shared Directory". Not a real "Samba Shared Directory". But then I always got in trouble in school for my "interpretations" :)

---

### Post by sh0wtym3 on 2010-04-14
> **Morbius1 said:**
> Are you trying to access the host shared folder using VirtualBox's "Shared Folder" feature or are you trying to simulate mounting a Samba shared folder across a network? There's a difference.

The answers above relate to accessing a Samba shared folder across a lan. To access a VirtualBox Shared Folder on the host it's a different process.
Yep, he wants us to use VirtualBox's Shared Folder feature, not Samba.


> **Morbius1 said:**
> 
Let's say you identified to VirtualBox the shared folder C:/Ubuntu as "ubuntu"

* Step 1: Create a mount point on the Linux Guest for the Host to live in:*

**sudo mkdir /media/sharedData**

Thats done.


> **Morbius1 said:**
> 
* Step 2: Add a line in fstab to mount the "Ubuntu" shared folder:*

**ubuntu /media/sharedData vboxsf rw,uid=1000 0 0**

I've added that exact line and saved it. Then I reopened fstab using gedit text editor to make sure it saved.


> **Morbius1 said:**
> 
* Step 3: Issue a command that will mount all new entries in fstab:*

**sudo mount -a**

I opened up the terminal and typed in that command, [B]and it worked!


[/B]> **Morbius1 said:**
> 
I guess it depends on the point of the exercise. If it's to use Virtual Box to teach you how to mount a remote share in a real life network then please disregard my post. 

I've interpreted that statement to mean a "Virtual Box Shared Directory". Not a real "Samba Shared Directory". But then I always got in trouble in school for my "interpretations" :)
lol. By the way thanks for the help I appreciate it.

---


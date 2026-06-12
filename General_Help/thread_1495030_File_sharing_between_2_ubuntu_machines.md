---
title: "File sharing between 2 ubuntu machines"
date: 2010-05-27
forum: General Help
---

### Post by jasontkennedy on 2010-05-27
Hi there! I'll be concise. I hope I can get some help :)

Problem: Neither Ubuntu 10.04 Lucid Lynx 64 bit machine can access any shared folders on windows PC's, or on the other Ubuntu machine. However, my windows machine CAN access the folders I've set up to share with Samba.  

When I click Places>Network it FINDS the other computers, but when I double click one of the other machines the "wait" pointer comes up and then it says: blah blah blah...
 "**The folder could not be displayed**: Sorry, could not display all the contents of "Windows shares on debbie-desktop": DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."

Why can the windows computers access shared files FROM linux, but the linux computers can't access anything non-local? 

Halp! :confused:

---

### Post by jasontkennedy on 2010-05-27
BTW, I've seen lots of tutorials on file sharing between Ubuntu and Windows, XBOX 360, Mac, the church, democracy, and the moon. 

Ubuntu shares... it is giving so freely, why can it not receive?
XD

---

### Post by morrcahn on 2010-05-27
Have you opened up your firewall on your pc so that others can look at the pc share?

---

### Post by jasontkennedy on 2010-05-27
No. Is that a setting I can access from the GUI? I'm still fairly new. I'm trying to teach myself CLI.. So most settings I've checked have been through GUI. 

Also, my Windows Laptop can see the Ubuntu machines and pull files off of them. It is the Ubuntu machines that cannot access anything non local.

---

### Post by Morbius1 on 2010-05-27
And by any chance are all the remote shares you are attempting to access require authentication. And when you access it did you set the password to "remember forever". If so you may be the victim of this bug:

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/463267](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/463267)

See post #4 for a work around.

---

### Post by morrcahn on 2010-05-27
It could be a firewall setting on your windows machine. To make it easier on yourself, you should just download WinScp. You can use that to transfer back and forth over both machines.

---

### Post by jasontkennedy on 2010-05-27
@ Morrcahn - it isn't connecting to windows machines, OR ubuntu machines. 

@Morbius1 - I checked out the workaround under passwords and encryption keys: nothing there of interest. 
What now?

---

### Post by Morbius1 on 2010-05-27
From Ubuntu post the output of
```
smbtree
```

---

### Post by jasontkennedy on 2010-05-27
Sorry for being such a nub. :/

madscientist@madscientist-desktop:~$ smbtree
Enter madscientist's password: 
WORKGROUP
	\\MADSCIENTIST-DES		madscientist-desktop server (Samba, Ubuntu)
		\\MADSCIENTIST-DES\IPC$           	IPC Service (madscientist-desktop server (Samba, Ubuntu))
		\\MADSCIENTIST-DES\Videos         	
		\\MADSCIENTIST-DES\Pictures       	
		\\MADSCIENTIST-DES\print$         	Printer Drivers
		\\MADSCIENTIST-DES\Downloads      	share
	\\DEBBIE-DESKTOP 		debbie-desktop server (Samba, Ubuntu)
		\\DEBBIE-DESKTOP\downloads      	open
		\\DEBBIE-DESKTOP\IPC$           	IPC Service (debbie-desktop server (Samba, Ubuntu))
		\\DEBBIE-DESKTOP\print$         	Printer Drivers
madscientist@madscientist-desktop:~$

---

### Post by Morbius1 on 2010-05-27
I know you're not going to believe me but your machine name is too long.

In a terminal:
```
 gksu gedit /etc/samba/smb.conf
```Add the following line to the [global] section:
```
netbios name = something
```*[COLOR=Blue]"something" can be anything you want but it has to be 15 characters or less.[/COLOR]*

Save the file, exit gedit, and back in the terminal type:
```
sudo restart smbd
sudo restart nmbd
```

[COLOR=Blue]**EDIT:**[/COLOR] Oh and no spaces or weird character please

---

### Post by morrcahn on 2010-05-27
Ha, looks like I won't be needed here.

> **Morbius1 said:**
> I know you're not going to believe me but your machine name is too long.

I would have to agree with this though. :)

---

### Post by jasontkennedy on 2010-05-27
you're right, I don't believe you. But I'm going to try it! :)

---

### Post by jasontkennedy on 2010-05-27
@ Morbius1 - 

Here is what the global section looks like (see below). I am adding the line you suggested AFTER the 6th line of text (workgroup = workgroup). The "something" I'll name it is jtkdesk. I'll then reboot the machine and see if that fixes it the "sudo restart XXXX" commands don't work.  

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
	workgroup = workgroup

# server string is the equivalent of the NT Description field
	server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
	dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

---

### Post by lakerssuperman on 2010-05-27
When setting up my machines I change this line

; name resolve order = lmhosts host wins bcast

to 

name resolve order = lmhosts wins bcast host

I read in the forums that it has to have host at the end otherwise it times out and causes issues.  I've never much bothered to investigate further but it works and I can share between all my machines.

---

### Post by jasontkennedy on 2010-05-28
@Morbius1 - I tried your fix of shortening the name.. It only made it so that Places>Network only saw my computer, the others had completely disappeared.Before I saw the other computers, it would just hang up when I tried to click on them. 

@lakerssuperman - I tried your fix and I now get an error message just by clicking on Places>Network>Windows Network>Workgroup.It says "Failed to retrieve share list from server"

---

### Post by Morbius1 on 2010-05-28
Rerun and post the **smbtree** command again. Based on your original output of smbtree you only had two machines on your network and both of them are linux. Did you have a Windows box connected to the network when you originally ran smbtree.

You might want to post the output of this command as well just to see if a firewall is in the way:
```
 nmap -sT 192.168.0.100/22
```*[COLOR=Blue]Change 192.168.0.100 to the ip address of the machine you're using.[/COLOR]*

*You may not have nmap installed but when you issue the nmap command it will ask you if you want to install it - you do. Once it's installed run the nmap command again.*

Either that or the Windows machines are Win7 and you have "Windows Live Sign-In Assistant" installed.

---

### Post by frogotronic on 2010-05-28
> **morrcahn said:**
> It could be a firewall setting on your windows machine. To make it easier on yourself, you should just download WinScp. You can use that to transfer back and forth over both machines.

```
$sudo apt-get install gufw
```

This will install the GUI for the Uncomplicated Firewall.  Then add/open the IP address of your windows machine: 192.168.2.XXX (likely)

What I did to get this to work is to run "ipconfig /all" on my windows box.  Then I entered this into nautilus "smb://192.168.2.XXX/", navigated to the desired directory and then made a bookmark.

- CH

---


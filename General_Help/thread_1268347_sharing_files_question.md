---
title: "sharing files question"
date: 2009-09-16
forum: General Help
---

### Post by HolyShnikes on 2009-09-16
I am trying to share files from my desktop running ubuntu to my laptop running ubuntu.  I have the files shared(samba), but apparently that only allows me to view my files in ubuntu in windows on the same computer.

Can someone help?

---

### Post by earthpigg on 2009-09-16
hi,

giver is the easiest possible way to share stuff between linux machines (not just ubuntu) on the same network.

> sudo apt-get install giver

---

### Post by swerdna on 2009-09-16
A few key things to get the communications going:

[LIST]
[*]Set the "name resolve order =", the "netbios name =" and the "workgroup =" parameters properly in the [global] stanzas of the Samba config files.

[*]You should drop the firewalls and get the network going that way, then set the firewalls to allow Samba. then raise the shields.
[/LIST]

This will help: [The Samba LAN Primer for Ubuntu: HowTo Set up an Ubuntu-Windows Home Office LAN/Network]("http://ubuntu.swerdna.org/ubulanprimer.html")

---

### Post by HolyShnikes on 2009-09-16
Giver has to be installed on both computers correct?

---

### Post by earthpigg on 2009-09-16
> **HolyShnikes said:**
> Giver has to be installed on both computers correct?

yes.

start it on both, run it, the computers running giver will find each other.

---

### Post by 3rdalbum on 2009-09-16
> **HolyShnikes said:**
> I am trying to share files from my desktop running ubuntu to my laptop running ubuntu.  I have the files shared(samba), but apparently that only allows me to view my files in ubuntu in windows on the same computer.

No, Samba allows you to share folders to different machines whether they be Windows, Macintosh or Linux clients.

If you can't access your Samba share from the other computer, then make sure you don't have any firewalls in the way.

Also try going to Nautilus on the client and put in the server's IP address and share name into the location bar, in this format:

smb://ip-address/share-name

---

### Post by HolyShnikes on 2009-09-17
Thanks.  I am running into an error however when I browse for any kind of thing.  [http://ubuntuforums.org/showthread.php?p=7961797#post7961797](http://ubuntuforums.org/showthread.php?p=7961797#post7961797)

You guys think you could help with that too?  I am trying to share files from my desktop and it freezes.  It doesnt do it on my laptop.  Which is weird because I heard laptops have more problems...but so far its not true.  :confused:

---

### Post by SteveDee on 2009-09-20
> **earthpigg said:**
> hi,

giver is the easiest possible way to share stuff between linux machines (not just ubuntu) on the same network.

I've recently started using Giver, but I'm not sure its working 100%.

Issue 1: if I'm running it on machine#1 and machine#2 logs onto the network, the Giver window does not update to show the new user until I quit Giver on machine#1 & restart the app.

Issue 2: The User Specified feature just gives me the "Give a folder/file" options, but does not ask where to send it.

I know the Giver app does not have full functionality (I've managed to get it to accept photos by editing the Preferences file). But I just wondered if someone could confirm whether the 2 points above should work when correctly installed?

---


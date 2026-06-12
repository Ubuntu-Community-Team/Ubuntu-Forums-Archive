---
title: "No sound on local machine when using Terminal Server Client"
date: 2011-11-18
forum: General Help
---

### Post by Windsurferdude on 2011-11-18
Hi,

I am running Ubuntu Lucid on an old Panasonic Toughbook CF-48.  I have two other machines running Windows 7 and one with Windows XP.  I have been experimenting with the Terminal Server Client and can connect with my other machines without difficulty.  My only issue is that for some reason I can't play the sounds of the remote machine on my local machine. The sound will work on the remote machine.  I've done a lot of searching and I guess this is an unusual problem because I have been unable to find any useful solutions.  Thanks in advance for your help.  Scott

---

### Post by dcstar on 2011-11-18
> **Windsurferdude said:**
> Hi,

I am running Ubuntu Lucid on an old Panasonic Toughbook CF-48.  I have two other machines running Windows 7 and one with Windows XP.  I have been experimenting with the Terminal Server Client and can connect with my other machines without difficulty.  My only issue is that for some reason I can't play the sounds of the remote machine on my local machine. The sound will work on the remote machine.  I've done a lot of searching and I guess this is an unusual problem because I have been unable to find any useful solutions.  Thanks in advance for your help.  Scott

I can get sounds from a remote Vista client to play using the TS client - you have to set the "Local Resources-Remote Computer Sound" option to play on the Local machine.

When you have a connection and check the Sound properties in Control Panel on the Windows box it should say something like "Microsoft RDP Audio Transport".

I have also just tested this with the **Remmina** package and it also works.

---

### Post by Windsurferdude on 2011-11-19
Hi, I got it to work with my Windows XP machine.  If I leave the settings for sound on the remote machines it works.  If I try to listen to the remote machines on my local computer, it doesn't work.  The only difference is that the other two machines are running windows 7.  I hope this makes sense.  Scott

---


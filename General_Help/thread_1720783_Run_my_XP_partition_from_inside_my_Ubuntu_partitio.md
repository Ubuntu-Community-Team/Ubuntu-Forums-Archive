---
title: "Run my XP partition from inside my Ubuntu partition???"
date: 2011-04-03
forum: General Help
---

### Post by emilward on 2011-04-03
I have my HDD in 3 partitions. 1 has Ubuntu 10.10, the 2nd has XP Pro, and the 3rd is a generic FAT 32 for all my music, photos, docs, etc. I was wondering if it was possible to run my XP Pro partition from within my Ubuntu partition so I am not constantly booting to and from XP to perform JUST a quick simple task. I installed Virtual Box OSE from the software center but it looks like it only runs .ISO images. 

Can anybody help me out?

---

### Post by TeoBigusGeekus on 2011-04-03
> **emilward said:**
> I have my HDD in 3 partitions. 1 has Ubuntu 10.10, the 2nd has XP Pro, and the 3rd is a generic FAT 32 for all my music, photos, docs, etc. I was wondering if it was possible to run my XP Pro partition from within my Ubuntu partition so I am not constantly booting to and from XP to perform JUST a quick simple task. I installed Virtual Box OSE from the software center but it looks like it only runs .ISO images. 

Can anybody help me out?

What's this "quick simple task" you mention?

---

### Post by techunit on 2011-04-03
I've got no idea how you'd accomplish that with windows. In linux you could chroot into the other partition and using the terminal tell it to start the GUI for that session but I don't know about with windows.

---

### Post by emilward on 2011-04-03
its always some kind of random editing or feature that linux cannot support or have. Like my wireless printer can scan an image to a file. My linux drivers for my printer doesn't support that. So I have to go into XP, scan my image, save it to my swap partition, and then boot to linux. Another is my Virtual Campus for my school use special programs that just don't work in linux. So i have to go into XP, to my assignment, save it to my swap drive, and then boot back to linux. its nothing life or death, just annoying. It'd be nice if I could open up xp in a kind of VM, do what i need to do and save to my swap drive, and go back to linux all from within Ubuntu.

---

### Post by Dry Lips on 2011-04-03
If you have a legal copy of XP, you ought to have the installation CD somewhere. In that case it is easy to create a ISO file using Brasero disk burner, and use that file for your virtualbox installation...

edit:
If you want to use USB devices, you ought to install the proprietary version of VB. 
(+ install the extension pack too...)
[http://www.virtualbox.org/wiki/downloads](http://www.virtualbox.org/wiki/downloads)

---

### Post by emilward on 2011-04-03
I do have my XP disk, actually. I will give that a shot, thanks

---

### Post by techunit on 2011-04-03
You better off installing the XP in a Virtualbox VM.

---

### Post by ExTruckie on 2011-04-03
> **Dry Lips said:**
> If you have a legal copy of XP, you ought to have the installation CD somewhere. In that case it is easy to create a ISO file using Brasero disk burner, and use that file for your virtualbox installation...

edit:
If you want to use USB devices, you ought to install the proprietary version of VB. 
(+ install the extension pack too...)
[http://www.virtualbox.org/wiki/downloads](http://www.virtualbox.org/wiki/downloads)

I agree with Dry Lips, install xp on a virtual machine and run it in the background, I do something similar to this to listen to an online public safety scanner that only runs on Media Player. I use VMWare Player

---

### Post by techunit on 2011-04-03
> **ExTruckie said:**
> I agree with Dry Lips, install xp on a virtual machine and run it in the background, I do something similar to this to listen to an online public safety scanner that only runs on Media Player. I use VMWare Player
Accept he **doesn'**t need to make a ISO out of his CD first. He can just use it to install XP as a VM.

---

### Post by Dry Lips on 2011-04-03
You need to make a couple of additional steps after installing VB and guest additions, before your USB devices actually works in XP. These are roughly the steps you need to take:
 
 a) Install VirtualBox + the additional pack.
 b) Install XP
 c) Install guest additions when running XP (Devices > Install guest additions.)
 d) Next you'll have to make sure you allow VB to use your USB-devices.  
 In Ubuntu go to System>Administration>Users and Groups
 Click &#8220;manage groups&#8221;. Add vboxusers. Voila! You can now select your USB devices from the devices menu in VB.
 
 The only thing you ought to be aware of, is that that you ought to unmount external HDD's etc in Ubuntu before using them in XP. Not doing so can mess things up.
 
 e) Finally, if you want to share files from XP to Ubuntu, you need to set up a shared folder. In XP you have to join a network group called &#8220;vboxsf&#8221; and then share a Ubuntu folder from the devices menu. Your shared folder can then be accessed from your virtual network (click on my computer, it will appear there...)
 
 Believe or not, this took me a while to figure out ;)

---


---
title: "how do I see root filesystem in windows VMware?"
date: 2006-03-25
forum: General Help
---

### Post by jms830 on 2006-03-25
I have a 2 reiserfs filesystems and and an ntfs external drive.  How can I get my windows xp pro running in VMware to recognize them? I installed a program to see reiserfs in the windows xp, but I do not think it even can see the drives.

---

### Post by dashnak on 2006-03-25
You have to set up some sort of share, like via SAMBA or something. The Virtual machine only "sees" the image file you created when installing XP, that's it's whole HD, it doesn't "communicate" in any way with root or any other filesystem not contained inside it's own virtual HD.

---

### Post by jms830 on 2006-03-26
hmm so is there a way i can move files to a location (within nautilus/ubuntu) so that VMware windows xp can see them? thanks by the way

---

### Post by syntek on 2006-03-26
just share the folder you want to be able to access from windows, then you could map a drive in windows so X: could be your home folder, or another folder of your choosing.

sudo apt-get install samba

then go to System > Administration > Shared Folders
Add a folder in there and Share it with SMB.

Then from Windows within VMWare you could click start > run and type \\[name of your linux box]. If you named your box ubuntu, you would just type \\ubuntu

Hit enter and you should see that folder listed, right click on it and map network drive. check the box to reconnect at login and select a drive letter.

that's pretty much it in a nutshell...

---

### Post by jms830 on 2006-03-27
ok thanks. are there any security concerns with sharing folders on Samba? I'm not exactly positive how it works, is it only within computers on the same router?

Edit: oh and how do i find out the name of my box? //ubuntu doesn't seem to work.

---

### Post by Marshall2day on 2006-03-27
No need for Samba and stuff. In vmware you can add a shared directory in the settings of your virtual machine. This way you can manipulate your hosts filesystem from within the VM. I'm not sure about ReiserFS since I have Ext3 but  it works like a charm. The share you defined shows up in my network places.

---

### Post by jms830 on 2006-03-27
Marshall2day so how do I go about doing that?

---


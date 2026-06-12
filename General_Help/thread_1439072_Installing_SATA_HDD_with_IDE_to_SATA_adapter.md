---
title: "Installing SATA HDD with IDE to SATA adapter"
date: 2010-03-25
forum: General Help
---

### Post by ThePinkWitch on 2010-03-25
Hi I'm just learning my way around computers and I have a second computer that had a 40G HDD that died so I took the old 80G out of my main machine and wanted to put it in the other machine. Unfortunately the second computer is IDE and the HD is SATA, so I bought an IDE to SATA adapter. Do I have to format this disk before using it? I had stuff on there I wanted to copy onto a USB. I want to format it after and put Ubuntu on it. Thanks for any help.

---

### Post by RemiemB on 2010-03-25
Assuming that you had Ubuntu on your machine, you could resize the partition on your SATA HDD, create a new partition, install Ubuntu on that new partition, transfer your files and then erase your old partition. Worked for me. 

I had 2 computers with Windoze and my nephew splash pop all over one of them. So i took the old drive and used it as a primary drive (using the above mentioned method) and now everything works like a charm.
Hope it helps!

---

### Post by ThePinkWitch on 2010-03-25
> **RemiemB said:**
> Assuming that you had Ubuntu on your machine, you could resize the partition on your SATA HDD, create a new partition, install Ubuntu on that new partition, transfer your files and then erase your old partition. Worked for me. 

I had 2 computers with Windoze and my nephew splash pop all over one of them. So i took the old drive and used it as a primary drive (using the above mentioned method) and now everything works like a charm.
Hope it helps!

Thanks  for your reply :) No It had WinXP on it. I didn't format it and it still has data on from my other computer. I put the IDE to SATA adapter on and tried to boot up the machine with the G Parted disk in but it won't read the HD. I thought maybe I should put it back in the original machine and format it then put it in the second one. At the moment GParted can't read the disk. Not sure if the IDE to SATA adapter is crap or what.

---

### Post by ThePinkWitch on 2010-03-26
Can anyone help? I really don't know what I'm doing here. Should I format this HD then try again?

---

### Post by RemiemB on 2010-03-26
If gparted can't read the disk, then try any HDD recovery tool. Can your other computer read it? Are the adapter connections properly in place? You can start there....

---

### Post by ThePinkWitch on 2010-03-27
> **RemiemB said:**
> If gparted can't read the disk, then try any HDD recovery tool. Can your other computer read it? Are the adapter connections properly in place? You can start there....

I put it in the original computer where it was working quite happily and even that won't read it. I think I killed it :( Trying to use the adapter seems to have done it. Yes the connections were in place. I don't have any HDD recovery tools. Thanks anyway. I think it's dead so no point trying to do anything else. The screen says DMI update success or something like that, and there's just a blinking cursor and it stays like that. It had winxp on it and I wanted to put Ubuntu on. oh well. Thanks for your help :)

---

### Post by viper250 on 2010-03-27
are you connecting a sata drive to an ide machine?
if so you need to look at your adapter and see if it has master and slave jumper pins 
set the jumper to master and connect the secondary master ide cable to the adapter (use the master connector! usually the one on the end is master).
If the pin setting is incorrect to the cable the drive may not even read at all

---

### Post by ThePinkWitch on 2010-03-27
> **viper250 said:**
> are you connecting a sata drive to an ide machine?
if so you need to look at your adapter and see if it has master and slave jumper pins 
set the jumper to master and connect the secondary master ide cable to the adapter (use the master connector! usually the one on the end is master).
If the pin setting is incorrect to the cable the drive may not even read at all

Yes as it states in my post I have an IDE board and a SATA HD. I have a male IDE adapter to SATA it's just a small adapter I plug into my HD and then plug the IDE cable into that. 

Thankyou, this sounds like really usefull info but I have no idea how to tell if it has master and slave pins. What do they look like? Maybe I need to explain this better. This 80G HD was the original in my Acer SA80 computer. I bought a 250G and the computer guy put it in for me. So the 80G was the master I assume that had WinXP on it. I eventually wanted to take that 80G out and put it in my second computer so I just took that out and the 250G I left in and formatted to dual boot Winxp and Ubuntu. I didn't mess with anything else. Just took the original drive out and formatted the other one and put WinXP and Ubuntu on it. I didn't set jumpers to master or slave or anything like that. I'm thinking you're right and thats probably whats wrong. The 80G still has WinXP and all my files on it from my Acer. I tried putting it back in the Acer to format it , but the Acer won't even find it in the Bios. I did Auto detect HD but no luck. This drive was working perfectly till I put the IDE adapter on and screwed around with it :(

---

### Post by viper250 on 2010-08-12
sorry for the delay in replying I was out of commission for a while
(Eye surgeries) 
the adapter may have been causing problems 
have you tried the drive in an external usb case?
sometimes this would bee the best way to deal with it. and it would be portable too

---

### Post by oldfred on 2010-08-12
This shows the jumper pins.

[http://unplugg3d.wordpress.com/2008/09/14/how-to-set-jumpers-on-a-hard-disk/](http://unplugg3d.wordpress.com/2008/09/14/how-to-set-jumpers-on-a-hard-disk/)

You can have master & slave or cable select. I would expect your IDE/SATA adapter to tell you what setting to have.

---


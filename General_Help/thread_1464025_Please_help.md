---
title: "Please help"
date: 2010-04-27
forum: General Help
---

### Post by Iviesaur on 2010-04-27
Please help me!!! I've been trying to install Ubuntu 9.10 on my new computer. It is now running XP. I did everything in the steps i.e. Download, Burn, Place in computer, restart computer. But i couldn't get it to work. And yes i changed the BIOS to where the CD drive would boot first and nothing i can't get the install screen to come up. Then i went and made a bootable flash drive. Did everything perfect yet again nothing. :/ Any help would be greatly appreciated.

Also i used wubi to download 9.10. That actually worked but now i wanna delete XP is that possible at all? Any help would be great.

---

### Post by peter d on 2010-04-27
Did you burn the iso file as an image? You can't just copy (burn) onto CD.

---

### Post by Zintha on 2010-04-27
> **peter d said:**
> Did you burn the iso file as an image? You can't just copy (burn) onto CD.
Thats what i'm suspecting has happened.
You can't just copy the file to the CD and have it work, you need an ISO burner.

Did you do that?

---

### Post by Iviesaur on 2010-04-27
yes i did

---

### Post by limey_rick on 2010-04-27
If you can't boot the Live CD, then its one of two problems, both mentioned. Either the BIOS is not set correctly, or the CD is burned incorrectly. 

Try another CD if you have a Windows XP install CD for example. If this boots into the CD installation program, its not the BIOS. 

If the BIOS is ok, open the CD in windows using explorer and verify that it is in fact a burned ISO image, rather than just the ISO image file copied to the CD. 

If the burned ISO image is ok, see if you can use it to boot another computer, although I appreciate this may not be possible. 

If all of this is OK, check your BIOS for any setting that may stop it from booting from the CD or another OS. I have a laptop that has a BIOS in which you tell it the OS type you want to boot. If this is set wrong,  can't book Live CDs for example.

Try to download burn another version or CD and see if you have any more luck.

---

### Post by Iviesaur on 2010-04-27
i'll try but idk i feel i've done everything right

---

### Post by Iviesaur on 2010-04-27
Question: Your BIOS can tell you what OS to boot? If thats the case what tab would it be under?

---

### Post by limey_rick on 2010-04-27
My BIOS had this where you selected the hard drives to boot from, I am not in front of it now, but I think it was Advanced Configuration. It had XP, VISTA and Other. For some reason, when set to XP, I had problems - it may have been something to do with the memory configuration or something else though, but I could not boot the Live CD with XP selected.

---

### Post by Iviesaur on 2010-04-27
Yeah i'm not seeing where it would say that. :/ Sorry! I seriously don't understand why this won't work. Like i have it dual booted with XP. But if i try to put in the cd then i can't even get to the install screen :[

---

### Post by limey_rick on 2010-04-27
So you may have to consider resetting your CMOS to clear the BIOS and restore to default values. Is this a desktop? If so, see if you can find out how to do this from the manufacturer or look-up the motherboard manufacturer. With a desktop this is fairly easy, with a laptop it may be more complicated. 

If you're computer is not letting you into the BIOS, then this is really what you need to do.

---

### Post by Iviesaur on 2010-04-27
Jeeze this is so very fustrating I've tried everything. I don't want to keep it dual booted cause that'll take up alot of memory. :// If anyone has any more suggestions i'll try anything. Also if anyone knows a direct download where it'll directly download on to my computer that would be awesome (I know it doesn't exist i'm just grasping at straws)

---

### Post by Iviesaur on 2010-04-27
No i can get into the BIOS i'm in it right now. yes it is a desktop. But i'm just not seeing where it would say that i can only have XP

---

### Post by Dareth on 2010-04-27
Which program did you use to burn the .iso?

---

### Post by Iviesaur on 2010-04-27
my friend burned it using brasero

---

### Post by limey_rick on 2010-04-28
So if you can now get into the BIOS and you are sure that the PC is booting from the CD/DVD drive try any other disk that you know it will boot from. If it boots then you know its a problem with your Ubuntu CD. If it does not boot, then you may have some issue with your CD/DVD drive.

If you don't have another boot CD/DVD, try to download another distro like KOPPIX [www.koppix.net](www.koppix.net) or something like the ultimate boot cd - [http://www.ultimatebootcd.com/download.html](http://www.ultimatebootcd.com/download.html).

Again, make sure you burn as ISO image and not just copy the ISO image to the CD and then burn the file.

---


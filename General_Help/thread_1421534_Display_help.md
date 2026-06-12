---
title: "Display help"
date: 2010-03-04
forum: General Help
---

### Post by Cpierce on 2010-03-04
I am new to Ubuntu, and know there is a ton of posts here, so thank you in advance for anyone who takes the time to help me. being a newbie, please outline step-by-step.
 
I did a fresh install of 9.10 on an older computer. I have two issues sound (in another post) and graphics driver. The card is an Intel 82830 - 830. Ubuntu does see this card. I went and tried to enable extra effects, but it wouldn't let me. So I installed compiz thinking it may force the driver to work, but it didn't, so I removed compiz. I installed Cairo Dock and I get the black box around the dock which I can't remove. From what I have read, it is because I am running on the default graphics driver. Hope that is the case. I also noticed that when I first see the image on the start up screen, it is dancing around like crazy for a few seconds, then locks in. I believe that is a driver conflict that results with the default driver being installed. 
 
I have spent hours reading on the web, and it seems that on the newer kernels, there is a thing called kernel probing that causes this issue with my graphics card. It says to open the Grub.cfg file with gedit and add "i915.modeset=0" to one of the lines and then save the file and run "update grub". I can do all this, but when I go to save in gedit, there is no option to "save", only "save as". How do I do this ?
 
The screen is current in 1024x768 resolution. Is the Intel 830 card able to support compiz effects if everything was working correctly ? Is this "i915.modeset=0" the right thing to do ? 
 
Any help would be greatly appreciated

---

### Post by Cpierce on 2010-03-04
Here is some more info. I downloaded and installed a program called compiz-check. I ran this and it said everything was okay to run compiz. So I installed compiz again and went to preferences>appearance>visual effects and tried to enble "customs effects", but it wouldn't let me. 
 
I feel I am close, if someone could just help me out, it would be greatly appreciated.

---

### Post by Cpierce on 2010-03-04
bump

---

### Post by Cpierce on 2010-03-05
Bump again

---

### Post by ssulaco on 2010-03-05
What are the specs of your computer,that sounds like an onboard chipset that may not drive visual effects...I would recommend Nvidia chipset graphics card (30-40 dollar) range worked well for me.

---

### Post by Cpierce on 2010-03-05
chipset is the Intel 830. The sound card is Ess Technology ES1988 Allegro-1 PCI. Hope that helps

---

### Post by ssulaco on 2010-03-06
> **Cpierce said:**
> Here is some more info. I downloaded and installed a program called compiz-check. I ran this and it said everything was okay to run compiz. So I installed compiz again and went to preferences>appearance>visual effects and tried to enble "customs effects", but it wouldn't let me. 
 
Im sorry,overlooked you had run compiz-check.....
Go......System >  Administration > Hardware Drivers......see if its enabled and/or the status of the driver......if you can get it enabled....then go and enable extra effects

---

### Post by Cpierce on 2010-03-06
bump

---

### Post by sandyd on 2010-03-06
go to applications -> accessories -> terminal
type in
```

compiz --replace
```

---


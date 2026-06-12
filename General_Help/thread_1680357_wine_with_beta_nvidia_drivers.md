---
title: "wine with beta nvidia drivers"
date: 2011-02-02
forum: General Help
---

### Post by Dans564 on 2011-02-02
I had windows for a while dualbooting with linmint 10 just so i could play cod4.  After getting Cod4 working flawlessly in wine... well bye bye windows.  I had the most up-to-date nvidia drivers, 260.19.36, and i was getting close to 100 fps.  Now i have upgraded the nvidia driver to the beta, 270.18, and my performance has plummeted.  Now i get like 20 fps which is unplayable IMHO.  Anyone have some tips to get full performance again??? this would be much appreciated

---

### Post by drewsus on 2011-02-02
Maybe don't use beta drivers?

---

### Post by cascade9 on 2011-02-02
260.1936- released 21/01/2011
270.18 beta- released 21/01/2011. 

Interesting, looks like with your card at least the 270.xx drivers are _very_ beta. Just revert to the 260.xx drivers.

Just out of intrest, what card are you running? Also, were the 270.xx drivers manually installed or from a PPA?

---

### Post by Dans564 on 2011-02-02
I'm using two EVGA gtx 460 with 1024mb of memory in sli.  And i got the driver by using the x-swat ppa, its just the driver it gave me.  ussually they send you the current nvidia supported driver but for some reason i got the beta.  Anyways, how do I revert back down to 260

---

### Post by drewsus on 2011-02-02
Interesting, I just noticed that I am on 270.18 as well (I too use that ppa). Thats... pretty lame that they are pumping out beta drivers.

---

### Post by Dans564 on 2011-02-02
yea and beta drivers with regressions it looks like.  Any ideas how to rollback??
my guess is it would go something like this.  Delete the x-swat ppa, and reload sources.  Then deactivate the driver using "additional drivers" app.  reboot.  and reactivate the driver.  what do u think.


ps. i think the x-swat team is doing this because the official ubuntu repo is on the 260 driver at this point, and x-swat purpose would be defeated if they too had the 260 driver.  just a guess though

---

### Post by drewsus on 2011-02-02
As far as I can tell, the official repos are at version 173.14.28. 

Open synaptic package manager. Search for Nvidia. 
Select these packages (but you have to do it one at a time):
nvidia-current 
nvidia-current-modaliases 
nvidia-settings
Press CTRL+E (or go to Packages->Force Version) and then select the version you want to apply (it only offers the beta version you already have and the most current stable version - that you want - 260.19.06). Repeat for the other two, then select Apply.

This is untested by me for these 3 packages, but I have done this with completely unrelated packages in the past.

---

### Post by cascade9 on 2011-02-02
> **Dans564 said:**
> yea and beta drivers with regressions it looks like.  Any ideas how to rollback??
my guess is it would go something like this.  Delete the x-swat ppa, and reload sources.  Then deactivate the driver using "additional drivers" app.  reboot.  and reactivate the driver.  what do u think.

I'd probably do that, but rather than deactivating I'd purge the nvida drivers totally. 

> **Dans564 said:**
> ps. i think the x-swat team is doing this because the official ubuntu repo is on the 260 driver at this point, and x-swat purpose would be defeated if they too had the 260 driver.  just a guess though

The repo has 260.1906, which doesnt appear on the nvidia list at all...probably because its s beta driver as well. :S 

[http://www.nvnews.net/vbulletin/showthread.php?p=2318734](http://www.nvnews.net/vbulletin/showthread.php?p=2318734)

Theres been several 260.xx drivers since then- 260.1912 (13-10-2010), 260.1929 (11-11-2010) and the 260.1936 out on the same day as the 270.xx drivers. 

I'd guess that somebody decided that since beta drivers worked for ubuntu 10.10, and people who want to add a PPA for drivers want the absolute 'latest and greatest'. So instead of 260.1936 they put those beta drivers in. 

I'd try sending a message to the PPA maintainer, and tell them about this _major_ performance regression as well.

Edit, @ drewsus- nah, 260.1906 is the version in the repos for 10.10- 

[http://packages.ubuntu.com/maverick/nvidia-current](http://packages.ubuntu.com/maverick/nvidia-current)

173.xx drivers are for the FX series only (well, you can run 6XXX, 7XXX, some 8XXX a few 9XXX and GTX260/GTX280 cards on the 173.xx drivers, but its not a good idea)

---

### Post by drewsus on 2011-02-02
ps- I have to say, two EVGA gtx 460s seems a bit overkill seeing as I couldnt find a game that I couldnt max out with just one of those. Crysis (but not the only thing I tested) at full res and everything maxed ran no problem (albiet, in Windows 7).

---

### Post by Dans564 on 2011-02-02
yea my hole comp is overkill lol... anyways doing what i wrote above and then running this will get u the most upto date but not beta drivers.
```
sudo add-apt-repository ppa:ferramroberto/nvidia
sudo apt-get update
sudo apt-get install nvidia-current nvidia-current-modaliases nvidia-settings
```

---

### Post by Dans564 on 2011-02-02
ok i am up and running the 260.19.36 drivers and am going to test cod4 later today.  I'll report back with the results

---

### Post by Dans564 on 2011-02-02
back to amazing cod4 performance, so the beta drivers def have some issues that need to be worked out.

---

### Post by drewsus on 2011-02-02
Sorry, I wrote asking you to say what you did, but I missed your 3rd last (the last one of page 1) reply about that different PPA. Im not sure if I want to use that one over x-swat just yet. All it has is the "nvidia-graphics-drivers" package. Is that a meta-package? What of nvidia-current, nvidia-current-modaliases and nvidia-settings?

---

### Post by Dans564 on 2011-02-02
to tell u the truth... im not sure.  But, it is working just fine for me so who knowss.  all i know is im playing cod4 with it limited to 150fps so im happy :guitar::guitar::guitar:

---

### Post by Lejoni on 2011-02-02
> **Dans564 said:**
> back to amazing cod4 performance, so the beta drivers def have some issues that need to be worked out.

Hey Dans564
I have had a similar problem.
I upgraded my graphic card from a GF 8600GT 515MB
to a MSI Geforce 460GTX HAWK Tallon Attack 1GB

My native games and benchmarks (like Unigine Heaven) runs amazingly well. But my Wine games don't
EQ2 runs better than on the old card but not as much better as I would expect. And Fallout 3 runs worse on the new card making it unplayable.
I first tried the nvidia driver that comes with Ubuntu 10.10 default. and then added the x-swat ppa for the beta driver and now as surgested in this thread added the repo to get the latest stable driver. But for me it did not make any diffrence I have the same low fps in Fallout 3. And it dosent seam to matter at all what graphical settings I use for the game.

I wonder if you could post your HKCU Direct3D settings.
So I can see if there is a diffrence there.
Or if you have any other idea about what could help.

---

### Post by Lejoni on 2011-02-03
> **Lejoni said:**
> Hey Dans564
I have had a similar problem.
I upgraded my graphic card from a GF 8600GT 515MB
to a MSI Geforce 460GTX HAWK Tallon Attack 1GB

My native games and benchmarks (like Unigine Heaven) runs amazingly well. But my Wine games don't
EQ2 runs better than on the old card but not as much better as I would expect. And Fallout 3 runs worse on the new card making it unplayable.
I first tried the nvidia driver that comes with Ubuntu 10.10 default. and then added the x-swat ppa for the beta driver and now as surgested in this thread added the repo to get the latest stable driver. But for me it did not make any diffrence I have the same low fps in Fallout 3. And it dosent seam to matter at all what graphical settings I use for the game.

I wonder if you could post your HKCU Direct3D settings.
So I can see if there is a diffrence there.
Or if you have any other idea about what could help.

Ok nvm. somehow I got it to run fine now.
Not sure what I did though :/

---

### Post by drewsus on 2011-02-03
even still check out this post on the wine appdb about FO3 to see how to properly set it up with winetricks and such:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=14322](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14322)

---


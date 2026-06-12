---
title: "HDD upgrade, how to move ubuntu?"
date: 2010-08-07
forum: General Help
---

### Post by jinba.ittai on 2010-08-07
I have never done such a thing, with a windows box nor linux, but i just got a new hdd. And at the moment i have 2 HDD in my pc adding up to 1tb. a 750 and 250.

Just got a 350 from a friend and now i dont know what to do. This case can only fit 2 drives, so i want to get ridd of the 250 in exchange for the 350. Only problem is, i have a dual boot, windows on the 750 (bad idea -_-) and ubuntu on the 250. I need to move ubuntu from the 250 to the 350. I was hoping i could keep all my files intact and what not, maybe clone the drive? but then how do i compensate for the added memory?

If worst comes to worst, ill just wipe the 250, and reinstall ubuntu on the 350. only problem with this method is i dont know whats going to happen with the grub configuration. Will it still be fine with grub? or do i have to reinstall or modify grub?

This is gona be a long night

---

### Post by bergfly on 2010-08-07
My recommendation if you want to clone is to use [clonezilla]("http://clonezilla.org/")to do the cloning. From small to bigger normally works pretty well. I would clone the linux drive, putting the image on the windows drive, swap out the linux drive and write it back to the new bigger drive. Unfortunately there is a problem with this as drives are normally now addressed by UUID by Grub, and this will change for the new drive. Hence you will in all likelyhood need to edit your GRUB file, not an easy thing with GRUB 2 if that is installed....

I see a lot of pain at the boot prompt for now. You may be able to bring it up with some editing at the boot command, and then run the GRUB updater, but personally, if I was you I would copy everything you need onto the windows drive and start from scratch...

---

### Post by jinba.ittai on 2010-08-07
Hmmmm ok think im gona go with the second option. Seems a bit more simple. But there are still going to be problems with grub. If i get all the files i need, then install the 350 gig, i will still have the problem that grub still thinks there is another hdd with ubuntu on it. Will i just be able to edit that, or delete it from the menu.lst file? or re install grub completely?

Or will installing ubuntu again reinstall the grub loader? 

I was gona say something else, but my mind keeps getting confused when my friends wont stop talking! Tryin to get shiz done here! Wish they could read this =P

---

### Post by bergfly on 2010-08-07
Installing Ubuntu from scratch will reinstall GRUB configured for however you have the system setup during the install. Hence getting round all the UUID issue and the now no longer editable menu.lst

---

### Post by jinba.ittai on 2010-08-07
So im running on a live cd and havent had my pc up yet. I was up till 5 am last night, then gave up and im at it again!

I tried to install ubuntu 64 bit but i couldnt get the disk to boot, so i am on 32 bit at the moment. i cant install 32bit though! I tried installing 32 on the 350 and it wont boot into grub period. Read my 750 and the windows seems to still be intact. Checked the bios, and thats all normal. 

I dont know what to do anymore. I tried connecting the 250 back up, which i havent even wiped, but get an error on grub and then it says 

"grub rescue <"

Now what? Have so much work to do, and this is slowing me down so hard! Wasnt expecting a hard drive upgrade to hit me so hard!

---

### Post by oldfred on 2010-08-07
If you want to know what is where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

Can you manually boot from the rescue line?
[https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode)
Express Boot to the Most Recent Kernel
 Command Summary ls to see drive X & partition Y (hdX,Y) or sdXY:
      ls
      set root=(hdX,Y)
      linux /vmlinuz root=/dev/sdXY ro
      initrd /initrd
      boot

---

### Post by jinba.ittai on 2010-08-07
Got it working, installed 32 bit ubuntu, finaly booted after 6 tries of installing, and then burned 64 bit and reinstalled. Both windows 7 and ubuntu 64 bit work again with the new hdd! 

Man im glad im done with that!

---


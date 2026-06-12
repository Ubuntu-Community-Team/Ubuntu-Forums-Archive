---
title: "Before i install ubuntu."
date: 2010-05-22
forum: General Help
---

### Post by ferucci on 2010-05-22
Hi all! I would like to install ubuntu on my laptop and before than do that i would like to consult with you about some things...
I have Toshiba Satellite L40-13G with 1gb of ram,1.9ghz intel celeron,graphic card of 256mb and 100 gb of hard drive...
A quite old laptop and i have currently on it installed windows xp and just because of that i wanted to see if Ubuntu will work on my laptop properly...
I also wanted to ask whether there will be problems about the invention and installation of drivers for Ubuntu os.
This is maybe a stupid question but i wanted to make sure that everything will be ok before i install Ubuntu.
Thanks!

---

### Post by warfacegod on 2010-05-22
If you put the install CD in the drive it will give you the option of trying Ubuntu without installing. (Using a USB created with unetbootin would be much closer to how your system will behave in speed.) Generally if everything works in the Live (try without installing) then an actual install should be fine also.

If you do decide to install, I suggest creating a separate partition for Ubuntu, assuming you want to keep XP. In addition, a separate partition for your /home (data, music, etc.) is a very good idea.

---

### Post by jerome1232 on 2010-05-22
That should run Ubuntu just fine. The vast majority of drivers come included with the OS, the most likely trouble spot is wireless, do you know what wireless card it comes with?

You could always boot into a live cd and see if everything works. You can try Dual booting for awhile so that you have access to both XP and Ubuntu while you are getting familiar with Ubuntu.

---

### Post by suibhne on 2010-05-22
Can you test on this machine freely?

If so, go straight ahead - connect directy to your router via a cable though in case your wireless is a problem.

The driver scenario is usually fine, the only problems I had over five years and countless machines is wireless functionality.

There is a real improvment each release though, and until I installed 10.04 on a fujitsu siemens machine yesterday, I had forgotten how frustrating it can be when the wireless drivers are not avaiable.

I would make a good bet that you'll be fine. Just make sure you have a back-up machine to work on.

In fact, would you consider keeping this thread updated with a basic breakdown of what you are doing and what is going well, or is confusing?

It would be useful for any other new people going through the same process.

---

### Post by ssj6akshat on 2010-05-22
You can Install Inside Windows so if anything is not working you can uninstall ubuntu from Add/Remove Programs

                     or 

boot from CD and use Try Before Installing.


If everything is working fine then welcome to the club.

---

### Post by warfacegod on 2010-05-22
> **ssj6akshat said:**
> You can Install Inside Windows so if anything is not working you can uninstall ubuntu from Add/Remove Programs

                     or 

boot from CD and use Try Before Installing.


If everything is working fine then welcome to the club.

In theory this is exactly what WUBI was designed for. Testing on a temporary basis. In reality, people don't want to go through doing another install, especially after getting accustomed to their WUBI install, so they just keep using it that way. This can lead to problems with Ubuntu after updates and upgrades. A separate install is almost always best.

---

### Post by ferucci on 2010-05-22
Thank you for your comments and suggestions!
I have two partitions,on one is operating system while in the second i keep all data that i have in my machine.Im planing to format my C partition and instal Ubuntu directly on it.
As for the wireless for me will not be a problem because i do not use it at all.
I have just one more question where i can get "live CD"?
Thanks!

---

### Post by warfacegod on 2010-05-22
[http://www.ubuntu.com/getubuntu/download]("http://www.ubuntu.com/getubuntu/download") Burn as an .iso

---

### Post by jerome1232 on 2010-05-22
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

The big green button.

If you don't know how to burn an iso to disc, check this out [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by marbss on 2010-05-22
> **ferucci said:**
> Thank you for your comments and suggestions!
I have two partitions,on one is operating system while in the second i keep all data that i have in my machine.Im planing to format my C partition and instal Ubuntu directly on it.
As for the wireless for me will not be a problem because i do not use it at all.
I have just one more question where i can get "live CD"?
Thanks!

the ubuntu cd that you download; it's both an installation and livecd

step 1.  play around booting and trying the livecd (no install reqd), or install wubi (windows installation).

step 2.  I'd probably recommend dual booting.  No need to format your Windows partition just yet.  The Ubuntu installer has an option to dual boot by resizing the Windows partition.  You can resize your existing Windows partition by dragging the little bar side to side. I've assigned as little as 6GB to Ubuntu to try it out.  This way if Ubuntu isn't working (driver issue etc), at least you can still get into Windows.  Once you are totally comfortable I'd say remove Windows totally.  

If you have problems with Ubuntu 10.04, try version 9.10.  

Good luck and let us know how it goes.

---

### Post by sille777 on 2010-05-22
Another To DO: before a dual boot install is clean house in windows.  Remove unwanted files (Cache files, Temp files, etc), De-fragement the drive, and run error checks. Most importantly back up any data files you don't want to lose just in case something goes wrong.

---

### Post by ferucci on 2010-05-22
thank you so much!!! 
cheers! :)

---

### Post by fr0styfr0st on 2010-07-19
I know from experience if you wish to install ubuntu for a test run you can actually install it along side windows with out formatting and next time you boot up it will ask you which one you wish to use.

Its practical and safe you can also uninstall ubuntu if your not happy with it simply go to add/remove programs and remove it :D hope that helps

---


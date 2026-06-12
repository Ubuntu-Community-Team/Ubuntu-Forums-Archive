---
title: "Boot problem after pressing reset button due to wine app hangup."
date: 2010-03-26
forum: General Help
---

### Post by guy_in_sun on 2010-03-26
Hello,

       As this is my first post of forum, I like to introduce my capabilities so that the person who helps me could better understand me.

       I am working as system administrator for the past 5 years, but only on Windows XP systems, I recently moved to Linux, frankly speaking a few days ago, and i got many problems with it. may be as i am a beginner.

       My Problem started with Ubuntu 9.04 amd 64 and now with 10.04 beta.

       The main problem I installed the wine (I am aware that wine is not compatible with all softwares of microsoft) and Installed microsoft office 2007 and it installed successfully but after installation when I launched Microsoft Excel it got hanged (only the Microsoft excel) and loading logo stood on top of all applications, then I decided to restart and pressed the restart button from menu on the right top. but there was no further response, then I pressed the reset button after waiting for 3-4 minutes to get rid of that logo of Microsoft in the center of my screen.

        Now, when the Ubuntu was booting, 
        Text arrives and disappears fast saying dev/file system has errors   
 
the logo of Ubuntu 10.04 and dots of loading at the bottom arrived and text written in the bottom of that "on of the drives needs to be checked, please wait it may take some time"

          Press 'C' to cancel disk check up.

         Now, its checking for a long time maybe for 30 minutes and the bottom text disappears and the loading Ubuntu 10.04 logo still remains and nothing happening after that.

         I Pressed alt+crtl+del 2 times, it restarts saying that saving some alsa process, then again the same thing after restart. 

         If I press C, it displays in the bottom of Ubuntu 10.04 logo "/File system has errors" and the loading screen remains like that.

         Now what is the solution and what are the precautions to be taken while using Ubuntu, as I was interested in introducing Ubuntu to marketing managers of offices, who wonder on the Internet all the time finding stuff and getting attacked by viruses.

         If this type of problems continue in Ubuntu, it will not be safer to use it, as if it wont boot during sudden power failures, that could result in a big problem.

         I will be very thankful If any one share with me their valuable Ideas.

         Thank you

---

### Post by viralmeme on 2010-03-26
> **guy_in_sun said:**
>  Now, when the Ubuntu was booting,  Text arrives and disappears fast saying dev/file system has errors
Boot from the Ubuntu CD and run fsck on the drives ..

---

### Post by guy_in_sun on 2010-03-26
> **ymitchell said:**
> Boot from the Ubuntu CD and run fsck on the drives ..


Thank you very much, that was very helpful, I struggled with the commands a little bit as I said I am new to Linux :)

But with the help of live cd of Ubuntu 10.04 there was a program in SYSTEM>ADMINISTRATION> GPARTITION (can't remember the exact name) with that software i made the fs check all the drives and restrarted, it worked. :D

And now its working ALL-IS-WELL ;)

Thank you very much ymitchell

I appreciate that! 

Regards
  Ram

---


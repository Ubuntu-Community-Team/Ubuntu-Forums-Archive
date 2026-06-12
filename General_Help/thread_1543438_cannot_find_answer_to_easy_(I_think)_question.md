---
title: "cannot find answer to easy (I think) question"
date: 2010-08-01
forum: General Help
---

### Post by demonet on 2010-08-01
I have looked quite extensively around the web to try and address a problem with no luck.

Background:  I have had an AMD64 laptop for awhile, but always ran x32 OS's on it for compatability purposes mainly.  Now however -- it feels like the software market is coming around and there are a baseline number of applications which function on a 64 bit system without blinking.

SO the other day, I decided to back up my home directory and reinstall lucid, but use the 64 bit version. No problems, performance was snappier... everything was great.

But then...the other day while looking for something new and exciting, I added a whole slew of 3rd party repos (most are commented out and I plan to investigate them with caution), but one repository -- for a distro -- has only 32 bit versions of the software.  So everytime I try and update I get the error which you active readers have heard of before:

I.e,   "W: Failed to fetch [http://xxxxxxxx.xxxxx](http://xxxxxxxx.xxxxx) xxxxx xxxxx  Unable to find expected entry  macroverse/binary-amd64/Packages in Meta-index file (malformed Release file?)
"

I installed the 32 bit libs, and also have a copy of getlibs by Cappy which seems as it would be very helpful once I decided to install a 32 bit application and if I had any problems.

However, if this repository only has headers for 32 bit, and no other indication of 64 bit packages, can't I override this check done by synaptic -- or at least through apt/aptitude.

It seems strange that considering what I want to do, my problem does not have to do with strange dependencies, but rather actually even getting the packages into the cache, so they will show up and select one if I decide.

Interested to know if there is a switch in apt-get or something similar which will ignore AMD64 altogether **even if it is  my platform,** and let me deal with making sure I have all libraries or other dependent packages working properly.  

It feels a little strange, almost like windows.  My OS is looking out for me by restricting what I can and cannot do. :)

Thanks,
Paul!

---

### Post by P4man on 2010-08-01
I dont think this has anything to do with 32 vs 64 bit, but just a repository which isnt set up to work with ubuntu (and obviously doesnt work with it).

---

### Post by demonet on 2010-08-01
This error is occurring on more than one repository.  

And would your reply to my post apply to the backtrack repository, a 32 bit ubuntu based distro?  

There are 4 or 5 different repos with which I get this error.  One, as mentioned, is the backtrack repository, and the others (without opening up sources.list) are debian-based.

---

### Post by dcstar on 2010-08-02
> **demonet said:**
> 
........
But then...the other day while looking for something new and exciting, I added a whole slew of 3rd party repos (most are commented out and I plan to investigate them with caution), but one repository -- for a distro -- has only 32 bit versions of the software.  So everytime I try and update I get the error which you active readers have heard of before:
.......

Apps compiled for 32-bit kernels will not run on systems using 64-bit kernels, if those repositories had 64-bit versions available they would be listed in the appropriate area, since they have not compiled 64-bit versions your 64-bit system will not even bother to list them because the 32-bit versions are totally useless and there is no point listing them.

---

### Post by coldraven on 2010-08-02
I "downgraded" back to 32 bit because of the security and performance issues with Flash 64bit.
See: [http://www.theregister.co.uk/2010/06/11/64_bit_flash_for_linux_dead/](http://www.theregister.co.uk/2010/06/11/64_bit_flash_for_linux_dead/)
I will "upgrade" when Adobe sort it out................eventually!

---

### Post by demonet on 2010-08-05
OK, first  I am a relative newbie. So bear with me.

But let's take "aircrack-ng" (or now known as Backcrack-ng).  I can download this and install it from a different repository or from the website, install it, it works without a problem.

So why isn't (or why hasn't someone) created a workaround to enable these 32 bit apps to show up in a repository? Since apparently they will run (notwithstanding dependency issues and what not).

Is there a way I can download the packages in the repository and compile them after I have downloaded them so they will work in 64 bit?

---


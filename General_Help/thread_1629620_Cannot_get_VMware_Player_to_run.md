---
title: "Cannot get VMware Player to run"
date: 2010-11-23
forum: General Help
---

### Post by dutchgirl on 2010-11-23
p { margin-bottom: 0.08in; }  Hello, I am trying to ge my vm player to run. I have installed the program. Next, I go to shortcut location. upon startup of vm player it gives me this error:


Before you can run Vmware Player, several modules must be compiled and loaded into the running kernal.
 

 **Kernel Headers 2.6.35-22-generic**
 

  Kernel headers for version 2.6.35-22-generic were not found. If you installed them in a non-=default path you can specify the path below. Otherwise refer to your distribution's documentation for installation instructions and click Refresh to search again in default locations.
  

  Location:                      blank box                                                 			Browse   Refresh
                                                                                  							Cancel     Install






I have tried everything that I have found, but nothing works. Please help me out, I need this for work to run xp. Thanks in advance for your time and help.

---

### Post by dcstar on 2010-11-24
> **dutchgirl said:**
> p { margin-bottom: 0.08in; }  Hello, I am trying to ge my vm player to run. I have installed the program. Next, I go to shortcut location. upon startup of vm player it gives me this error:
..........

Please look in the Virtualization forum for the answer.

---

### Post by dutchgirl on 2010-11-24
I still cannot find a fix to solve my problem

---

### Post by dutchgirl on 2010-11-24
where would the virtulazation forum located? The forums I have searched through I have been unable to find a solution. Otherwise, I would not have posted a question.

---

### Post by dutchgirl on 2010-11-24
I gave up the effort, heh, I chose to install virtual box instead. ;)

---

### Post by dcstar on 2010-11-24
> **dutchgirl said:**
> where would the virtulazation forum located? The forums I have searched through I have been unable to find a solution. Otherwise, I would not have posted a question.

10 seconds of looking at the Ubuntu Forums home page would clearly find the Virtualization forum listed in the Other Community Discussions section, is that so difficult?

The Virtualization forum contains all VM issues, and you would have probably found you answer in a few minutes rather than waste days by posting in the wrong place.

---

### Post by wet-willy on 2010-11-25
According to the error message, you did not have kernel headers installed which are required for compiling vm modules. Installing package [linux-headers-2.6.35-22-generic]("http://packages.ubuntu.com/maverick/linux-headers-2.6.35-22-generic") would have solved that error.
Too bad we're on a tight time line.
Too bad we couldn't just answer the question.

---

### Post by dutchgirl on 2010-11-25
p { margin-bottom: 0.08in; }  I did try installing kernel headers. But, after installation it still gave me the same error. It seems to be linked to a recent update that vmware is currently trying to address, and that is directly from their help forums located on their website. In regards to the time line. . . . . i work from home at times and i had to get a vm program back up and running. in other aspects of non work related programs i am all about taking my time to try to solve an issue. believe me, I am still looking to fix vmplayer, i'm not such a big fan of virtual box, it just provided the fix for the time being, if you look at my other posts you will also note as to my level of patience, not trying to bicker here, just throwing that out there. once again, thank all whom have spent their time trying to help me as I am extremely grateful. I have now been using Ubuntu for a solid 6 months and I would never go back to windows :] thanks again

---

### Post by dutchgirl on 2010-12-04
VMware Player bug has been resolved. With the new release of VMware-Player-3.1.3 availible for download on their webistie ([www.**vmware](www.**vmware)**.com/products/**player**/) fixes the kernel headers bug.

---


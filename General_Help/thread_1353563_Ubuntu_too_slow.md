---
title: "Ubuntu too slow"
date: 2009-12-12
forum: General Help
---

### Post by 3dmatrix on 2009-12-12
I have a Acer aspire 4720. I have used Ubuntu 8.04 very successfully on it. and was very happy with it. I ungraded to Ubunty 9.04 and found it to be too slow. The windows open and close with jerks. The booting time is enormous. The HDD light keeps on for very long and makes all sorts of sounds. Inspite of the fact that I have not been able to switch on the Visual Effects. First of all i could not start it but lated when i found it so slow i gave up the idea of taxing my laptop so much. Takes ages for Firefox to close. At times the response to clicks is also delayed. There is a gnome error every other boot. Over all a very very bad experience. Now I have a 9.10 CD with me but I am wondering if I should upgrade to 9.10 or degrade to 8.04 or switch over altogether to some other distro like Mint (or any other). I am just looking for a very stable, fast and very secure Linux for me. Easy to use but without much gimmicks (if it makes things slow).

---

### Post by 3rdalbum on 2009-12-12
Is there a program that is using all your CPU power and causing the slow speed?

You can check this with the "top" command.

If there's a program that's using a lot of CPU time, then kill it and your system's speed should go back to normal.

---

### Post by sailthesea on 2009-12-12
Try Mint 7

---

### Post by 3dmatrix on 2009-12-12
Top command gives the following result :

PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND  

7293 user    20   0  402m 101m  27m R   19  5.1   0:35.61 firefox            
 2924 admin      20   0  358m  45m  16m S    7  2.3   4:58.63 Xorg               
 3504 user    20   0  156m 5444 4152 S    2  0.3   0:02.73 pulseaudio         
 3580 user    20   0 41412  19m  10m S    1  1.0   1:22.65 alarm-clock        
 7326 user    20   0 94964  13m 9620 S    1  0.7   0:00.82 gnome-terminal     
 3550 user    20   0 85168  11m 8552 S    1  0.6   0:06.18 metacity           
 3536 user    20   0 45496 7712 5744 S    1  0.4   0:07.37 scim-panel-gtk     
 7332 user    20   0  2448 1200  912 R    1  0.1   0:00.26 top                
    9 admin      15  -5     0    0    0 S    0  0.0   0:23.31 events/0           
   31 admin      20   0     0    0    0 S    0  0.0   0:00.57 pdflush            
 3581 user    20   0 97.8m  21m  11m S    0  1.0   0:25.05 python             
 3588 user    20   0 98.9m  21m  11m S    0  1.1   0:26.66 python             
    1 admin      20   0  3084 1884  564 S    0  0.1   0:01.45 init               
    2 admin      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 admin      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 admin      15  -5     0    0    0 S    0  0.0   0:00.16 ksoftirqd/0        
    5 admin      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0     

I dont know what the admin is doing there :) with so many programmes.
Can you locate any thing wrong here ?

Why Mint 7 why not 8 ? From my experience I have felt that Mint forum is very very poor in support. The best I found till now is Mepis Forum. But that is perhaps the only best thing they have :)

---

### Post by QIII on 2009-12-12
One thing that seems to be a frequent problem that does not show up in top (or indicates that it is using 0 resources) is remote desktop sharing -- vino.

System | Preferences | Remote Desktop and make sure sharing is not enabled.

You would be surprised at the number of times I have made this suggestion.  Often the user does not remember ever enabling it.  That may be forgetfulness, or some odd bug.  I don't know.

---

### Post by sailthesea on 2009-12-13
Why Mint 7 why not 8 ? From my experience I have felt that Mint forum is very very poor in support. The best I found till now is Mepis Forum. But that is perhaps the only best thing they have

 I've had no problems with Mint 7 I thought it may be worth your while to check it out with your machine 
 As far as the forums go I never stray from here If you use terminal the technical aspects are all the same Just be mindful of the different Repos you may have to use
 :D

---

### Post by 3dmatrix on 2009-12-13
Did any one find anything wrong in the TOP command result given above ?

---

### Post by keplerspeed on 2009-12-13
> **sailthesea said:**
> Try Mint 7
?? I disagree. Why would any Ubuntu (GNOME) derivative be faster than Ubuntu?

If Ubuntu is too slow, try #! crunchbang linux. If that is too slow try Arch, Puppy, Gentoo etc. These are much harder to set up however.

---

### Post by QIII on 2009-12-13
> **3dmatrix said:**
> Did any one find anything wrong in the TOP command result given above ?

Nothing leaps out at me.

There should be some information above the section you posted.  Can we have a look at that?

---

### Post by 3dmatrix on 2009-12-13
top - 16:12:53 up 8 min,  2 users,  load average: 1.20, 0.74, 0.40
Tasks: 143 total,   2 running, 140 sleeping,   0 stopped,   1 zombie
Cpu(s):  7.3%us,  3.2%sy,  0.0%ni, 89.3%id,  0.3%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2052624k total,   778824k used,  1273800k free,    27804k buffers
Swap:  1052216k total,        0k used,  1052216k free,   333440k cached


Why does it says two users and one zombie ?

Is there anything wrong in the above data ?

---

### Post by Sin@Sin-Sacrifice on 2009-12-13
89.3%id  There's your problem... try opening up system monitor to see if the process is listed there. I've found that top doesn't list a lot of processes especially when they use a lot of CPU.

---

### Post by 3dmatrix on 2009-12-13
Well, 89.3% is not my problem bcoz I never told my computer to do that :)
And I didnt change the default settings !
I checked again. Immediately after booting :
top - 18:11:35 up 6 min,  2 users,  load average: 0.68, 0.91, 0.44
Tasks: 143 total,   1 running, 141 sleeping,   0 stopped,   1 zombie
Cpu(s):  4.1%us,  2.3%sy,  0.0%ni, 93.6%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2052624k total,   816656k used,  1235968k free,    23064k buffers
Swap:  1052216k total,        0k used,  1052216k free,   411160k cached

And simultaneously checked in the system monitor but it did not display anything using that much CPU. The maximum that was being used was by Gnome system monitor but even that was not too much.

Hardware can not do anything abnormal on its own unless it is given instructions by the OS. If a recourse eating OS like Vista can run on my comp how come Ubuntu is running so slow. I have 2 gb of ram and a core 2 duo processor (1.5 + 1.5 GHz) and abt 40 gb of free HDD space. What more does Ubuntu needs ?

---

### Post by tpmevec on 2009-12-13
I have 4G RAM, 200G free disk space, 128M video, AMD64 x2 HP Laptop. Ran Ubuntu since 8.04. Decided with 9.10 to perform a full clean install. PC ran so slow after that, and I tried twice just in case I messed something up, I have since gone back to, yup, you guessed it, Vista. I disabled all fancy interface options on Ubuntu and still slow. Windows Vista is running faster than the latest Ubuntu version and it really hurts me to say this. I have professed to all my collegues the benefits of going to Ubuntu and now I am running Windoze. A friend also went with a clean install of 9.10 and is now running Windoze. I only hope others are having better experiences.

---

### Post by QIII on 2009-12-13
3d and tp --

In terms of resources, Ubuntu and other Linux distributions require much fewer resources than Windows.  I run one of my development installations of Lucid on a PIII with 750Mb of RAM without any difficulty at all.  Vista simply will not run on that spec.
 
 The problem is not the OS itself, but some ***process*** that is hogging the resources.  I suggested vino as a possible problem, because it is a known culprit.  Have you checked that?  I'm not saying that it is definitely the problem, nor that it is the most likely problem.

There could be many others. 

The fact that you still have 93.6% (id = idle.  I don't think sin realized this when he made his post.  89.3 id is not a problem.) of your processor capacity available and more than half of your memory available leads me to believe that something like this is occurring.

That, or you are having issues with your display configuration, which can often lead to similar symptoms.

Your zombie is either caused by a parent process that spawned a child and did not clean it up (not necessarily the OS's issue, since the process might be something other than the OS, such as an application you installed) or a parent process spawned a child process that it wants to hold on to until it is needed again.  In any case, the odds are good that the zombie is not the ultimate cause of your grief.

I would also check to see what processes you have flagged to run at startup and be sure you want them to.

The only way to discover what that might be is by troubleshooting.  "Ubuntu sucks" does little to solve the problem.

---

### Post by 3dmatrix on 2009-12-14
I also think that there is something wrong with the display config or the Xorg. How do we deal about it ? The start up applications are as it was in the default installation. Just couple of things like screenlets etc are added.

---

### Post by 3dmatrix on 2009-12-17
3 days and still no reply :)
If Ubuntu ppl cant suggest a solution then its surely a problem with Ubuntu ! Think its time to switch over to some other distro. Thanx friends.

---


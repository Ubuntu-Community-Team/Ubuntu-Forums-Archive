---
title: "Modprobe: Fatal: Could not load ... after 10.10 Install"
date: 2010-10-10
forum: General Help
---

### Post by Aydos on 2010-10-10
Hello all I did a clean install of 10.10 today with the official finished version after it went live. I did a full format so there was nothing left. After installing I get the following error found at the bottom of this post. It pops up twice and then the OS boots up and runs fine after that. It is just annoying and slows my boot time. 

I did a google search and found where people were having this problem all through beta and I guess it made it to the finished version.

Anyone have a fix for this?

modprobe: Fatal: Could not load /lib/modules/2.6.35-22-generic/modules.dep: no such file or directory

---

### Post by skyjacker on 2010-10-10
> modprobe: Fatal: Could not load /lib/modules/2.6.35-22-generic/modules.dep: no such file or directory
Same here.. ran thread for two days, got one solution... Did not solve.:confused:

---

### Post by arrimapirate on 2010-10-10
I get this error too. It doesnt seem to hurt anything on my system either. It loads plymouth right after then i log in as usual.

---

### Post by Aydos on 2010-10-10
Yeah everything seems to run fine for me as well afterwards, but it is annoying having to watch that screen and having the slowed down boot time.

---

### Post by Aydos on 2010-10-11
Bump for sanity! Would like to mark this one as solved at some point.

---

### Post by warakawa on 2010-10-11
bump, I have the same problem.

---

### Post by Gabliver on 2010-10-11
I have the same error too. 

10.10 64 bit .

But so far ok. Perhaps some modules werent loaded. 

With previous kernel looks better . 

gabliver

---

### Post by Aydos on 2010-10-11
Early Morning Bump for good measure. I want the 45-60 seconds of my boot time back.

Have a good day all.

---

### Post by eynestyne on 2010-10-11
Same problem here. New installation. Haven't noticed any problems after login

---

### Post by petrasflorin on 2010-10-11
Go here: [http://ubuntuforums.org/showthread.php?t=1592062](http://ubuntuforums.org/showthread.php?t=1592062)
L2Search before posting.

---

### Post by Aydos on 2010-10-11
I did search and I did not see that post.

However, the problem is still unsolved in that post and many of us are having this issue and would like to find a resolution to the problem.

L2Social Skills

Even though you were quite rude in your reply at least you pointed me to a valid link. Thanks for that.

---

### Post by beast2k on 2010-10-20
Same issue here to, then login screen freezes for about 30 seconds or so. then all seems fine.

---

### Post by markofealing on 2010-10-24
> **beast2k said:**
> Same issue here to, then login screen freezes for about 30 seconds or so. then all seems fine.

Same here after upgrading from 10.04 to 10.10 using 32-bit Ubuntu.

---

### Post by beast2k on 2010-10-24
> **markofealing said:**
> Same here after upgrading from 10.04 to 10.10 using 32-bit Ubuntu.
I solved the problem using this thread  
[http://ubuntuforums.org/showthread.php?t=1592311&page=2](http://ubuntuforums.org/showthread.php?t=1592311&page=2)
Scroll down to post #12 Follow the instructions in the post, it works like a charm.

---

### Post by Craigus on 2010-11-26
What you really mean there is "it works like a charm, sometimes", because this is caused by a race condition and that fix will not work on all hardware - it doesn't on mine.

---

### Post by Athanasius on 2010-12-10
*sigh* It is things like this that drive me back to Debian...  Better luck next release Ubuntu.

---

### Post by beast2k on 2010-12-10
This issue came back after an update about a week or 2 ago. The solution at the link I posted earlier fixed it the first time then after the update the problem came back and no solution I found so far has been able to fix it. The solution is beyond me so I am living with it. I am also looking seriously at Debian, as well as Mint.

---

### Post by robmus on 2010-12-13
Mark me down for this same problem. Installed 10.10 _64 on a MacTel 3,1, all worked beautifully; Then I installed the suggested update, now I get the same modprobe: Fatal message. Everything boots fine after the message. No problems, just irksome.

---

### Post by thelugnut on 2010-12-28
I am having the same silly problem.

Also, if you look in System>About Ubuntu, you'll see another goof up. 
It says "You are using Ubuntu 11.04 - the Natty Narwhal - released in April 2011 and supported until October 2012."
That's wrong.
Now if you download Ubuntu 11.04 Alpha and look in the same place, it tells you you are using Ubuntu 10.10.
That shouldn't be too hard to fix.

---

### Post by Trogladyte on 2010-12-28
I loaded 10.10 as a clean install on a formatted drive.I had this problem, although when the system finished booting everything was fine. I have solved the problem by doing  a full reinstall - it solved the boot issue, but ever since I have been having problems with software-center refusing to load. Also been having periodic problems with update manager and synaptic- more details in my software-center thread.

---

### Post by pileup on 2011-01-19
[http://t.co/S4hVFlW](http://t.co/S4hVFlW)

It works! :p

---

### Post by n411303 on 2011-02-16
Worked for me too!  Thanks

---

### Post by karmila on 2011-03-02
> **n411303 said:**
> Worked for me too!  Thanks

Yes, It works! :D

---


---
title: "how do I find out how much ram/cpu I am using?"
date: 2010-06-01
forum: General Help
---

### Post by Zerocool Djx on 2010-06-01
Is there an add-on in the software center?

---

### Post by xfearxnxloathing on 2010-06-01
> **Zerocool Djx said:**
> Is there an add-on in the software center?

System>Administration>System Monitor

---

### Post by harrismh777 on 2010-06-01
There are several ways to do this easily, depending what you want.

You may use the System Monitor tool:
     System -> Administration -> System Monitor

Click the Resources tab;  memory and swap history are in the center.

However, system monitor does not always report consistently (various bugs) the actual memory usage, nor the correct total memory installed. This is (I think) because the formula for calculating the memory useage from the kernel stats is complicated---there are many forms of used and free memory and cache, so you really need to know what you want...

So, you can also take a look at memory useage directly from the kernel using your terminal:
   Applications -> Accessories -> Terminal

   then enter :

   cat /proc/meminfo

   The memory useage information is complicated... which is why system monitor does
not always calculate the values "correctly" whatever I mean by that.

   Remember something else... unlike windows... linux utilizes memory better. What I mean by that is that the system will "use" much of available memory resources one way or the other... caching, buffers,  etc...  so things will look like more memory is being "used" as what you might be thinking about.  The system balances this useage allowing your apps the resources they need.  Accounting for this is what system monitor is trying to do... just doesn't do it consistently ---especially between releases.

[sigh]

---

### Post by Ozymandias_117 on 2010-06-01
Or if you're into terminal apps, I like htop

---

### Post by Zerocool Djx on 2010-06-01
Gracias!!

I don't need to know exact numbers, ball park will do,... A few programs were sucking up power and needed to know what was up is all...

---

### Post by harrismh777 on 2010-06-01
> **Ozymandias_117 said:**
> Or if you're into terminal apps, I like htop

I use "top" frequently... and usually it is consistent and correct (as well, it shows how much memory each process is actually using...)

I have not used htop... I'll check it out.

---

### Post by Ozymandias_117 on 2010-06-01
> **harrismh777 said:**
> I use "top" frequently... and usually it is consistent and correct (as well, it shows how much memory each process is actually using...)

I have not used htop... I'll check it out.

The problem I have with top is the total memory usage at the top shows cached memory too, and while yes, the system IS using the memory, it doesn't NEED to be, so I don't like it counted.

Notice how top shows 2.5 gigs of RAM used htop shows 796 MB

---

### Post by Spr0k3t on 2010-06-01
htop ftw.  I generally run htop from a tty session when I'm debugging.  Allows for quick glancing at the apps in question.

---

### Post by inso_741 on 2010-06-01
or you can use conky

---

### Post by harrismh777 on 2010-06-01
Thanks for the tip guys. Its in my tool box now. Its a nice little ncurses tool (as was noted, great for use in ttys) and I like the ways it can be customized... and that I can use it to send various signals to a process (like SIGHUP for instance) from a menu while I'm watching htop run... very nice. 
That's why I love linux... infinitely configurable and always something new to learn... how much fun is that!

OOPS   :oops:

Should point out for the first poster that the htop package is not installed by default... at least it wasn't on my system. So, if you want to try htop, then use:
     System -> Administration -> Synaptic Package Manager

  Then search for htop....   check the package box, and then apply.

   Follow the yellow brick road... 

   run htop from your terminal, or you could setup a launcher...

---

### Post by harrismh777 on 2010-06-01
> **inso_741 said:**
> or you can use conky

... I can now.  :neutral:

This little tool has the advantage of being not only highly configurable, but also very tiny... 

Now for the fun... take the outputs from /proc/meminfo; conky; top; htop; and System Monitor.... and compare their outputs for memory useage...

... sorry.   :-\"

---

### Post by sdennie on 2010-06-01
> **harrismh777 said:**
> There are several ways to do this easily, depending what you want.

You may use the System Monitor tool:
     System -> Administration -> System Monitor

Click the Resources tab;  memory and swap history are in the center.

However, system monitor does not always report consistently (various bugs) the actual memory usage, nor the correct total memory installed. This is (I think) because the formula for calculating the memory useage from the kernel stats is complicated---there are many forms of used and free memory and cache, so you really need to know what you want...

So, you can also take a look at memory useage directly from the kernel using your terminal:
   Applications -> Accessories -> Terminal

   then enter :

   cat /proc/meminfo

   The memory useage information is complicated... which is why system monitor does
not always calculate the values "correctly" whatever I mean by that.

   Remember something else... unlike windows... linux utilizes memory better. What I mean by that is that the system will "use" much of available memory resources one way or the other... caching, buffers,  etc...  so things will look like more memory is being "used" as what you might be thinking about.  The system balances this useage allowing your apps the resources they need.  Accounting for this is what system monitor is trying to do... just doesn't do it consistently ---especially between releases.

[sigh]

This is a very good description of how free memory calculations work on linux.  It's complicated enough that the idea of "used" and "free" aren't really relevant for most people.  With page creation happening on demand, shared memory being counted as cache, etc, unless you are using swap, chances are that all is well.

---


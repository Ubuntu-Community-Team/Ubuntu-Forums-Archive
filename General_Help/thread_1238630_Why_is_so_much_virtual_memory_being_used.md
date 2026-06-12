---
title: "Why is so much virtual memory being used?"
date: 2009-08-12
forum: General Help
---

### Post by nmaster on 2009-08-12
This was the output of "top"
```


  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5423 neal      20   0 85532  35m  16m S    4  1.2   0:49.22 skype              
 5698 neal      20   0 69588  18m 9928 S    3  0.6   0:52.39 npviewer.bin       
 4913 root      20   0  461m  58m  20m S    1  2.0   2:33.37 Xorg               
 5624 neal      20   0  687m 175m  27m S    1  5.9   3:33.78 firefox            
 6648 neal      20   0 19116 1320  988 R    1  0.0   0:00.08 top                
 6445 neal      20   0  185m  16m 9768 S    0  0.6   0:01.65 gnome-terminal     
    1 root      20   0  4104  920  632 S    0  0.0   0:01.16 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.01 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.01 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.39 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.04 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.09 events/1           
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper   

```why is so much virtual memory used?  wouldn't ram be used first?  system monitor shows the same thing. look at the screenshot showing my swap space.  i have 3gb ram and 3.45gb swap. 

thanks for the help.

---

### Post by nmaster on 2009-08-12
MORE INFO:

actually, the System Monitor "Processes" tab shows the same info as "top", but the "Resources" tab shows that no swap is being used.  i included another screenshot.

---

### Post by lisati on 2009-08-12
As I understand it, virtual memory is a behind-the-scenes "trick" that a system uses to make it appear to your programs as if there's more RAM available than there really is. I wouldn't worry about it too much, unless your system performance is suffering.

---

### Post by nmaster on 2009-08-12
there isn't any noticeable lag in performance so you're right that its nbd.  but wouldn't ram still be faster than swap?  also why is there a discrepancy between the various System Monitor tabs and "top" ?

---

### Post by dfreer on 2009-08-12
In this case, the results shown by top can be misleading. It is showing the total amount of virtual memory used by that single application, including shared libraries. As the name suggests, these libraries are only loaded into memory *once*, regardless of the number of programs using them. 

So application foo at 30 MB's may be using library bar consisting of 15 MB's of memory, but application barfoo at 40 MB's is also using library bar. In this case you are only using 85 MB's of memory. Yet top will show foo using 45 MB's and barfoo using 55 MB's.

This should help explain it better:
[http://www.linuxquestions.org/questions/linux-software-2/top-shows-virtual-memory-use-by-proccess-more-than-physical-ram-help-664104/#post3254912](http://www.linuxquestions.org/questions/linux-software-2/top-shows-virtual-memory-use-by-proccess-more-than-physical-ram-help-664104/#post3254912)

EDIT: IIRC virtual memory actually is defined as the total amount of available memory, including swap/RAM. It is not just limited to swap. So if it's using 150 MB's of virtual memory, it could still be entirely in RAM.

---

### Post by nmaster on 2009-08-12
> **dfreer said:**
> 
EDIT: IIRC virtual memory actually is defined as the total amount of available memory, including swap/RAM. It is not just limited to swap. So if it's using 150 MB's of virtual memory, it could still be entirely in RAM.


hmmm... i guess that's a little misleading.  btw, what exactly is "IIRC"?

---

### Post by DGortze380 on 2009-08-12
> **neal.m.master said:**
> but wouldn't ram still be faster than swap?  

Yes, it is ... that's why it's often reserved for current and intensive processes. For example, firefox uses swap to cache web data regardless of RAM available. An instance of gimp may be move to swap by the OS if inactive for a period of time and loaded back to RAM while cropping an image.

(That's a simplistic explanation, but you get the idea).

---

### Post by dfreer on 2009-08-12
> **neal.m.master said:**
> hmmm... i guess that's a little misleading.  btw, what exactly is "IIRC"?

[http://tinyurl.com/n5y48k](http://tinyurl.com/n5y48k)

---

### Post by blueridgedog on 2009-08-13
> **dfreer said:**
> [http://tinyurl.com/n5y48k](http://tinyurl.com/n5y48k)

I can't believe you took the time to create the tinyurl, versus simply stating "IIRC stands for If I recall correctly".

The forums here discourage the use of acronyms for exactly the same reason you demonstrated - it leads to confusion (and mild sarcasm in this case).  [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)  It is item 9, fifth bullet point.

---

### Post by nmaster on 2009-08-13
> **blueridgedog said:**
> I can't believe you took the time to create the tinyurl, versus simply stating "IIRC stands for If I recall correctly".

The forums here discourage the use of acronyms for exactly the same reason you demonstrated - it leads to confusion (and mild sarcasm in this case).  [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)  It is item 9, fifth bullet point.


Ah thanks!  yeah i didn't want to sound ungrateful but the tinyurl was kind of a jerk move, especially since i did google IIRC. I found that page but didn't want to sift throgh the two pages of results and thought it would be easier to just have someone tell me.  I've never found those online chat acronyms useful, I guess I'm kind of an old man at heart. lol

Thanks everyone!

---

### Post by P4man on 2009-08-13
virtual here doesnt mean its being swapped. As you can see in gnome system monitor, your system isnt using any swap at all (and i bet never will), everything is in ram.

In top 'virt" stands for virtual image size. From top man page:

VIRT -- Virtual Image (kb)
The total amount of virtual memory used by the task. It includes all code, data **and shared libraries** plus pages that have been swapped out.

RES -- Resident size (kb)
The non-swapped physical memory a task has used.


Want to know more ? 

```
man top
```

---

### Post by nmaster on 2009-08-13
> **P4man said:**
> 

VIRT -- Virtual Image (kb)
The total amount of virtual memory used by the task. It includes all code, data **and shared libraries** plus pages that have been swapped out.

RES -- Resident size (kb)
The non-swapped physical memory a task has used.


Want to know more ? 

```
man top
```

thanks.  i had looked at the man page, but i guess i didn't understand what a virtual image was.  i thought that just refered to the virtual memory which seems to not even be precisely the same thing as swap.

---

### Post by dfreer on 2009-08-13
> **blueridgedog said:**
> I can't believe you took the time to create the tinyurl, versus simply stating "IIRC stands for If I recall correctly".

Eh, I meant it as a joke, not as a flippant remark. The tinyurl is part of the site, so as not to spoil the punchline I'd imagine. I never noticed the "Was that so hard?" part before, in retrospect it does seem rather sarcastic/harsh. 

Apologies all around.

---

### Post by philinux on 2009-08-13
This might explain things since linux utilises memory diferently than windows. i.e more efficiently.

[http://forums.gentoo.org/viewtopic.php?t=175419](http://forums.gentoo.org/viewtopic.php?t=175419)

---

### Post by nmaster on 2009-08-13
> **dfreer said:**
> Eh, I meant it as a joke, not as a flippant remark. The tinyurl is part of the site, so as not to spoil the punchline I'd imagine. I never noticed the "Was that so hard?" part before, in retrospect it does seem rather sarcastic/harsh. 

Apologies all around.

its no big deal.  i do the same thing all the time without realizing it.  apology accepted.

---

### Post by nmaster on 2009-08-13
> **philinux said:**
> This might explain things since linux utilises memory diferently than windows. i.e more efficiently.

[http://forums.gentoo.org/viewtopic.php?t=175419](http://forums.gentoo.org/viewtopic.php?t=175419)


this is a really good link.  i have 3gb ram and 3.5 gb swap though so those modifications wouldn't make a difference.  the info was really good though.  thanks.

---

### Post by blueridgedog on 2009-08-13
> **dfreer said:**
> Eh, I meant it as a joke, not as a flippant remark. The tinyurl is part of the site, so as not to spoil the punchline I'd imagine. I never noticed the "Was that so hard?" part before, in retrospect it does seem rather sarcastic/harsh. 

Apologies all around.

Bravo...Don't get me wrong though...I have used the site for some of my search resistant friends and family members...

---


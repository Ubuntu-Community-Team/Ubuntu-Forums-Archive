---
title: "Graphics issue please help"
date: 2010-10-11
forum: General Help
---

### Post by Dans564 on 2010-10-11
Hey guys,

just installed a fresh 10.10 on my comp.  I already had 10.10 rc at one point.  On the rc i had a problem with Ubuntu only seeing one of my two gtx 460's.  I fixed it with help from the internet, but forgot what i did exactly.  All i remember is it had something to do with allocating more ram to a boot process of some sort.  Point is I'm having the same problem on my fresh install and forgot what I did!  Any thoughts??

---

### Post by sendblink23 on 2010-10-11
> **Dans564 said:**
> Hey guys,

just installed a fresh 10.10 on my comp.  I already had 10.10 rc at one point.  On the rc i had a problem with Ubuntu only seeing one of my two gtx 460's.  I fixed it with help from the internet, but forgot what i did exactly.  All i remember is it had something to do with allocating more ram to a boot process of some sort.  Point is I'm having the same problem on my fresh install and forgot what I did!  Any thoughts??

Since I'm on plans of buying 2 x 460... and i want to learn from users who have it already.... Did installing the the driver from System > Administration > Additional Drivers (its suppose to be  the newest driver version 260.19.06)- did it still do the same not detecting the SLI?

---

### Post by Dans564 on 2010-10-11
well sadly, no, only one card is detected.  Don't get me wrong once they are in sli the performance in tremendous.  I recommend them 100%.  Its just i forget how to fix this problem.

---

### Post by sendblink23 on 2010-10-11
> **Dans564 said:**
> well sadly, no, only one card is detected.  Don't get me wrong once they are in sli the performance in tremendous.  I recommend them 100%.  Its just i forget how to fix this problem.

hehe Its an upgrade for me - I am going to buy them :P

Anyways did you try this:
[http://www.darraghverschoyle.com/2009/03/enabling-sli-on-ubuntu-810/](http://www.darraghverschoyle.com/2009/03/enabling-sli-on-ubuntu-810/)

no clue if that still works on 10.10

**SCRATCH THAT*** that doesnt work
I'm gonna keep surfing

---

### Post by Dans564 on 2010-10-11
although it is true once detected you run

```
sudo nvidia-xconfig --sli=AFR
```

its just that right now its like the second card doesn't exist :-k

Idk if this will help but im remembering a bit more now...  It had to do with allocating more memory to hardware when grub2 boots.

---

### Post by Dans564 on 2010-10-11
i found the answer but forget where it goes if that makes sense...
i change something to this in the grub cfg
```
vmalloc=256
```
but now i cant find that anywhere.  This problem is starting to make me feel dumb.

---

### Post by Dans564 on 2010-10-11
FOUND IT!!!!!!!!!!

1) Back up /etc/default/grub:
```
sudo cp /etc/default/grub /etc/default/grub-backup
```

2) Open /etc/default/grub in a text editor:
```
sudo nano /etc/default/grub
```

3) Find the GRUB_CMDLINE_LINUX_DEFAULT line. Add options to the end of this line inside the quotation marks (leaving one space between each added option) as follows:

4)increase virtual memory allocation:
Add ```
vmalloc=256MB
```

Save and reboot.

then run
```
sudo nvidia-xconfig --sli=AUTO
```
to enable sli

---


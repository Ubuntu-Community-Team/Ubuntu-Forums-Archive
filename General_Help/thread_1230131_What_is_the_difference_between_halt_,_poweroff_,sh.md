---
title: "What is the difference between halt , poweroff ,shutdown"
date: 2009-08-03
forum: General Help
---

### Post by rsiddharth on 2009-08-03
What is the difference between the 'halt' , 'poweroff' and shutdown commands ?. 

I 'manned' these commands in terminal , but wouldn't get what I was looking for - the difference , nor could I infer  . I also googled ,hoping to find something that might clear the ambiguity . I did come across a thread in linuxforums.org  dealing with the same topic and one of the posts there read :
> 
I am using red hat 5
I guess i understood the use( plz correct me If I am wrong)
shutdown - is for shutting down the server
poweroff- is for shutting down the client
I wouldn't understand what this would mean to a Desktop Computer . 
Can anyone here explain me precisely what this means - What is the Difference ? . 
I Thank you :D .

---

### Post by HermanAB on 2009-08-03
Same difference - They all transition to runlevel 6.

---

### Post by rsiddharth on 2009-08-03
> **HermanAB said:**
> Same difference - They all transition to runlevel 6.
Thank you HermanAB , but can you explain it in a way that a lay user may understand - what is 'runlevel 6' ??

---

### Post by wojox on 2009-08-03
[http://en.wikipedia.org/wiki/Runlevel#Ubuntu](http://en.wikipedia.org/wiki/Runlevel#Ubuntu)

shutdown -r now = to reboot the system
shutdown -h now = to close the system

halt -p = shut and turnoff the system
halt = to close the system

reboot = to reboot the system

---

### Post by rsiddharth on 2009-08-03
Thank you wojox for making me understand what Runlevels actually are . 

I think i am slowly getting the answers ,but my ambiguity over the difference still remains . 

the difference between halt and shutdown -h now is made clear by wojox's post here , but what is the difference between 'closing the system' and ' shut and turn off the system ' .

---

### Post by shanxk8 on 2009-08-11
Hello all,

New user to Ubuntu here. :)  I've found the posts and contributors on this forum very helpful in getting an old box up & running with Ubuntu.  (Ubuntu actually was up and running well on its own, Impressively)  I've been able to sort out some issues with mounting an external HDD and setting up a share of that drive.

I have noticed issue with shutdown on that computer though.  Ubuntu seems to shutdown to an Ubuntu screen with an empty (all black) progress bar, but the computer does not power off (leaving a fan, or two, still whirring away inside the case and LEDs on the front still on).

What operation does the shutdown button on the upper panel perform? (halt, shutdown, etc.)

Ideas?

I tried the command shutdown -H based on another thread i found,  with the same end result.  
Next time I'm on there I will have to try halt to see if that is the solution.

Thanks,
David

---

### Post by unutbu on 2009-08-11
Older machines sometimes do not work completely with acpi. The old way of shutting down was to use a module called apm. The module is still available, you just have to set it up. Here are instructions on how to do that:

[http://ubuntuforums.org/showpost.php?p=6289063&postcount=5](http://ubuntuforums.org/showpost.php?p=6289063&postcount=5)

---

### Post by shanxk8 on 2009-08-11
I did some reading about acpi as well, a post i came across suggested adding acpi=force to grub/menu.lst 
[http://ubuntuforums.org/showthread.php?t=1213834&highlight=incomplete+shutdown]("http://ubuntuforums.org/showthread.php?t=1213834&highlight=incomplete+shutdown")

I will look into that apm module.

Thanks

---

### Post by unutbu on 2009-08-11
There are a couple of different reasons why shutdown doesn't work for some people. This leads to a couple of different possible solutions. Here is a catalog of various solutions that have worked for certain people:

[http://ubuntuforums.org/showpost.php?p=6176637&postcount=28](http://ubuntuforums.org/showpost.php?p=6176637&postcount=28)

---

### Post by dcstar on 2009-08-12
> **HermanAB said:**
> Same difference - They all transition to runlevel 6.

Runlevel 6 reboots a Linux/Unix system, runlevel 0 shuts it down:

```
man telinit
```

---

### Post by shanxk8 on 2009-08-17
> **unutbu said:**
> Older machines sometimes do not work completely with acpi. The old way of shutting down was to use a module called apm. The module is still available, you just have to set it up. Here are instructions on how to do that:

[http://ubuntuforums.org/showpost.php?p=6289063&postcount=5](http://ubuntuforums.org/showpost.php?p=6289063&postcount=5)

This solution has solved my shutdown problem thank you!

---

### Post by Akhnatoun on 2010-12-20
If you'd like to just understand the meanings of these terms, here is it:

A halt will just bring the OS down whereas a Power Off will bring the OS down and then send an ACPI power off command to the power supply.

by other words; If the machine does not have power management capabilities, there isn't a difference. If it does, the difference is power off will send the signal to power the machine off, while Halt will shut everything down and wait at a "Power Off" prompt, meaning it is safe to hit the power switch.

However, you can halt the system without powering it off. So you issue a halt, wait for it to say "You can turn the computer off now" and then you can hit the power button without worrying that something is going to unmount weirdly.

But in most modern unix's halt, shutdown, init 0, poweroff, etc, etc all do about the same thing. Halt, for example, is mapped to "shutdown -h" when the system isn't in runlevel 0 or 6.

---

### Post by rsiddharth on 2010-12-20
> **Akhnatoun said:**
> 

If the machine does not have power management capabilities, there isn't a difference. If it does, the difference is power off will send the signal to power the machine off, while Halt will shut everything down and wait at a &quot;Power Off&quot; prompt, meaning it is safe to hit the power switch.


Thank you Akhnatoun  for your reply. How do I know if my computer has power management capabilities ?.

---

### Post by Akhnatoun on 2011-01-02
> **rsiddharth said:**
> Thank you Akhnatoun  for your reply. How do I know if my computer has power management capabilities ?.

At most, your computer has a power management capabilities, unless you are using an old desktop or server, as all new desktops and laptops have this capabilities. 

To test it, halt your system by typing:
```
$ halt -p
```

If your system stopped, but the power light of your computer is still flashing "and perhaps you find the fan is still running, so you don't have a power management capabilities.

hope this be helpful.

---


---
title: "Shutdown problem for Kubuntu 9.04"
date: 2009-07-15
forum: General Help
---

### Post by Vinger on 2009-07-15
Hello,

I have a problem when i shutdown my laptop.
I get the message: 
> will now halt
 *halt: unable to iterate IDE devices: no such file or directoy'
[ 199.565466] Power down.


I searched the forum, but all the threads that i read proposed the same solution: (changing /etc/modules and /boot/grub/menu.lst)

That solution does not work for me...

Is there any other solution? It's a realy nasty bug!

grz.

---

### Post by cwbar_1 on 2009-07-15
Do you have any ide devices?  Ubuntu is set up to work with all sorts of hardware.  If you really want to get rid of those type of messages, make a note of all of your hardware and custom build the kernel that will load _only_ those devices you have. Otherwise, ignore the messages.

---

### Post by Vinger on 2009-07-16
Hello,

Thanks for the help, but I'm not planning to build the kernel my own... I'm a simple user of the Kubuntusystem...

I don't care about the warning i get, but i care about it because my computer is not shutting down... 

Anyone another idea?

grz.

---

### Post by cwbar_1 on 2009-07-16
I did not read in the original post that your system would not shut down. However, check the information at [http://ubuntuforums.org/archive/index.php/t-776036.html](http://ubuntuforums.org/archive/index.php/t-776036.html).  Hope this helps.

---

### Post by Vinger on 2009-07-19
Tx but it didn't helped...

I tried the command /sbin/shutdown -P
This didn't halt my laptop anymore. i just got a black screen and had to push the laptop out.
then i tried /sbin/shutdown and then /sbin/poweroff

All tree had the same problem. Now i just putted /sbin/halt again, and i have the problem of before...

Anyone an idea?
Allready thanks.

---

### Post by Vinger on 2009-07-25
I tried the commandline 
" sudo shutdown now -P "
and even then i get the message [ 199.565466] Power down. 
but the laptop is not powering down...

What can i do? 
no one an idea?

grz

---

### Post by Fixman on 2009-07-27
For some reason, that also happens to me only when I am charging the power to the notebook, and the computer shuts down in the instant I remove the power cable. My guess was that that was somehow a feature, since (to my understanding) this Laptop won't charge when its fully shutted down.

Anyway, you can shut down the notebook with that message by pressing the shut down button once that message appears.

---

### Post by Vinger on 2009-07-29
Hello,

i tried it without the power plug, but that didn't helped... 
I know that i can shutdown with the button, but that's annoing...

Anyone a suggestion?

grz.

---

### Post by tau88 on 2009-07-30
just a suggestion (i suppose you're using a compaq 610 from reading your post regarding audio issues): try changing your BIOS setup (F10 when starting). Go to system configuration / device configurations and change the SATA device mode parameter

---

### Post by Vinger on 2009-07-30
ok, tx!

That did the trick. I adjusted the sata device mode parameter to 'disable' and my laptop is shutting down :-)

grz.

---


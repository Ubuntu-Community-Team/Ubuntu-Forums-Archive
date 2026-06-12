---
title: "Ubuntu 11.10 live cd not booting"
date: 2011-10-20
forum: General Help
---

### Post by bimaljr on 2011-10-20
Hello,

I am going to try to install Ubuntu 11.10 via Ubuntu 11.10 Desktop CD on my system but the cd cannot boot.

I have also downloaded Alternate CD but it also stops after showing first menu screen.

Both just shows blank screen with blinking cursor at top. No message or anything else.

---

### Post by bimaljr on 2011-10-22
Anyone?
Still waiting for answer.

---

### Post by Quackers on 2011-10-22
Have you checked the md5sum of the downloaded iso file?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If that's ok then you can check the cd for errors following the method mentioned in the above.

You may need to use a boot option, such as nomodeset, as described here

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by bimaljr on 2011-10-22
Thanks for reply,

I have checked MD5SUM before creating both Desktop and Alternate CDs.
Also I have tried with different options like nomodeset but still not loading.

Any other help/step to load CD?

---

### Post by ashirviskas on 2011-10-26
Same thing happening, i can't install ubuntu from cd. when im booting from cd after a minute i see only black screen and i can just type text, but NOT COMMANDS.
I also checked md5 and disk from errors, i've even burned few more cds at lower speeds, still same issue. Any help ?

---

### Post by ashirviskas on 2011-10-26
heres the video: [http://www.youtube.com/watch?v=o6CThObBCn4](http://www.youtube.com/watch?v=o6CThObBCn4)

---

### Post by xtremo on 2011-10-26
Have you got another machine you can check the CD in?

---

### Post by oldfred on 2011-10-26
Often you actually are booting thru the grub boot, but Ubuntu has video issues. Some systems also need additional parameters in addition to the nomodeset parameter.

Natty Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)
Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line
[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

---

### Post by anddan on 2011-10-28
Just to confirm, i have this live-dvd boot problem also.

System starts the first gui-step with language/boot selection, after that it halts with a lot of messages.
I have tried every boot option with F6 without any success. Also tried the livedisc in another pc where it boots without any problem, and checked md5 just to be sure.

My rig is an MSI MB with AMD Athlon2 X4, and a Sapphire 5850 1Gb graphics card.

Im a little puzzled where to start searching for a sollution, could it be changes in graphic drivers in 11.10? (since it worked just fine in 11.04)

---

### Post by oldfred on 2011-10-28
Have you changed any BIOS settings? Not sure what else to suggest.

---

### Post by oldtimer7777 on 2011-10-29
Create a Live stick of Ubuntu 11.10 on a Flash Thumb Drive. Boot from that to install.

Here is a nice guide too.

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

> **bimaljr said:**
> Hello,

I am going to try to install Ubuntu 11.10 via Ubuntu 11.10 Desktop CD on my system but the cd cannot boot.

I have also downloaded Alternate CD but it also stops after showing first menu screen.

Both just shows blank screen with blinking cursor at top. No message or anything else.

---

### Post by anddan on 2011-10-29
Here's a photo of the output  at halt:
 [http://s1225.photobucket.com/albums/ee394/anddanphoto/?action=view&current=errormsg.jpg](http://s1225.photobucket.com/albums/ee394/anddanphoto/?action=view&current=errormsg.jpg)

---

### Post by OttoMann on 2011-10-29
Sorry for jumping in this thread, but I seem to have the exactly the same problem.

The Ubuntu 11.10 Live CD gets stuck. All I get is the purple start screen (the one with the rectangle and circled man), the screen then goes dark (with CD still spining) and after a few moments it starts printing some messages (like in the above post).

What could be wrong?

I get the same result with Ubuntu 11.10 Live CD, Ubuntu 11.10 64 bit Live CD, OpenSuse 11.4 DVD, the only one working is Fedora 15 Live CD wich boots to Gnome3.

---

### Post by anddan on 2011-10-29
I apologize to the threadmaker since i did sort of jump in too,  but if its a general problem perhaps its good to discuss ideas in one  thread.

> **OttoMann said:**
> 
The Ubuntu 11.10 Live CD gets stuck. All I get is the purple start screen (the one with the rectangle and circled man), the screen then goes dark (with CD still spining) and after a few moments it starts printing some messages (like in the above post)..

Thats exactly what happends if i just wait it out. If i push some button i  get option screen for language, boot settings etc. After that - the result is the same. Is there any switch i could set to make boot logged or something, or is the output shown in my example a typical indication on some kind of known problem? The latter would make it easier to pinpoint the problem and perhaps work around it.

---

### Post by oldfred on 2011-10-29
For all those just jumping in, it is best to start your own thread. It gets too confusing with different users posting similar but different results and suggestions to solve.

You have booted thru grub but may need nomodeset and/or other parameters. See post #8.

---

### Post by OttoMann on 2011-10-29
**Re: Ubuntu 11.10 live cd not booting**
 		I apologize to the threadmaker since i did sort of jump in too,  but  if its a general problem perhaps its good to discuss ideas in one   thread.

 	Quote:
 	 	 		 			 				 					Originally Posted by **OttoMann** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=11405762#post11405762") 				
 				*The Ubuntu 11.10 Live CD gets stuck.  All I get is the purple start screen (the one with the rectangle and  circled man), the screen then goes dark (with CD still spining) and  after a few moments it starts printing some messages (like in the above  post)..*
 			 		 	 	 
Thats exactly what happends if i just wait it out. If i push some  button i  get option screen for language, boot settings etc. After that -  the result is the same. Is there any switch i could set to make boot  logged or something, or is the output shown in my example a typical  indication on some kind of known problem? The latter would make it  easier to pinpoint the problem and perhaps work around it.

Thanks for the tip. I was just waiting but now I get at least the usual options screen with the same results....  
But following oldfred's tip and selecting nomodeset Ubuntu boots and works in Live session mode using Unity2d. 

Thank you both!!!!!!  :P:P

---

### Post by anddan on 2011-10-31
Ok, here's an update on my testing. I opened my case and removed the ATI Sapphire card, since the MB (MSI 890gxm-g65) has onboard graphics, and booted again, and i still have the exact same error messages, so the external graphics cards is not causing the problem. I also went through all BIOS settings and tried once with most things set to disabled, and also tried loading MB preset "failsafe mode" but no success :(

Another test i did was to insert radeon.modeset=0 into the bootstring but still the errors.(incase the internal graphics is causing problems)

I have no other addon-card, a regular optiarc dvdr and one 500gb drive, so it appears to be my MB that is the issue here unless there's something i missed. Since 11.04 works, could it be caused by kernel changes?
[I]
Edit:I have started reading linked info from post #8 but not the entire 79-page thread yet, there is alot to digest, and honestly much work just to get the installation cd to start :/[/I]

---


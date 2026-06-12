---
title: "Power Management"
date: 2010-08-23
forum: General Help
---

### Post by jose1986 on 2010-08-23
So, I have noticed this for some time but never really dealt with it.  Basically, I have a dual boot with Windows 7 and Ubuntu 10.04.  Windows 7 with a never dimmed light gives me 3 hours of battery but when it is dimmed, seems I can get like 5 hours!  However Ubuntu kills my battery, I get maybe 2 hours whether I am dim or bright, probably less than 2 hours.  Lately I have tryed to install some fixes but I keep getting error messages.  

[http://samwel.tk/laptop_mode/packages/debian](http://samwel.tk/laptop_mode/packages/debian)

I have tryed this for a little while now.  And I keep getting the error message in my terminal, that says, "su: authentication failure"   strange because I know my password and am the administrator, I even went to turn off the laptop not to prompt for my password at startup but it prompts for a password once I have logged in, anyhow.


I tryed to download laptop-mode-tools from ubuntu's package website and it gives me the error message "Error: Breaks existing package 'pm-utils-powersave-policy' conflict: laptop-mode-tools ( )" and the install package is dimmed out.  


To me, I could care less what does it, I just want normal battery power when I use ubuntu.  I also would like my password prompt to not prompt me, after I log in.  I returned it now to the prompt for password at startup but it still gives me that extra password screen.

---

### Post by Quackers on 2010-08-23
For password prompt at login try System > admin > Users and Groups then the Password entry should have "Not asked on Login" next to it. If it doesn't click on change to the right of it enter your password and tick the bottom box that says "Don't ask for password on Login".
System > Preferences > Power Management should sort your power problems.

---

### Post by murphycc on 2010-08-23
If Power Management options don't work (previous post), download and install powertop to see what apps are waking up your processor too often.

Note that 'powertop' is only designed for Intel based processors (not AMD).

-Chris

---

### Post by n.l.o on 2010-08-24
I am trying to get this right as well, there is a short discussion during lucid testing here: [http://ubuntuforums.org/showthread.php?t=1450501](http://ubuntuforums.org/showthread.php?t=1450501)
But it seems as they just points out that pm-utils-powersave-policy is a light version of laptop-mode-tools and that more elaborate settings is not implemented as in laptop-mode-tools... great.

Aside from attempts at getting to grips with laptop-mode-tools vs. pm-utils-powersave-policy I have successfully set my NVidia GPU to downclock when on battery and to run in adaptive mode when on AC.

Mainly from [http://tutanhamon.com.ua/technovodstvo/NVIDIA-UNIX-driver/#power-saving](http://tutanhamon.com.ua/technovodstvo/NVIDIA-UNIX-driver/#power-saving) (and [http://linux.aldeby.org/nvidia-powermizer-powersaving.html](http://linux.aldeby.org/nvidia-powermizer-powersaving.html))

Since posting final settings promote copy-paste behaviour, I will just note that looking at "Configuration examples" after reading some about how it works in the main source is good.

I do not really now how to measure the change, but it feels as if I got a bit longer run time...

Cheers

---

### Post by n.l.o on 2010-08-24
> **jose1986 said:**
>  I also would like my password prompt to not prompt me, after I log in.  I returned it now to the prompt for password at startup but it still gives me that extra password screen.

Is this not due to nm-applet or something like that?

look at:

[http://ubuntuforums.org/showthread.php?t=603265](http://ubuntuforums.org/showthread.php?t=603265)
and
[http://ubuntuforums.org/showthread.php?p=9093778#post9093778](http://ubuntuforums.org/showthread.php?p=9093778#post9093778)

---

### Post by n.l.o on 2010-08-24
> **n.l.o said:**
> 
Aside from attempts at getting to grips with laptop-mode-tools vs. pm-utils-powersave-policy I have successfully set my NVidia GPU to downclock when on battery and to run in adaptive mode when on AC.

Mainly from [http://tutanhamon.com.ua/technovodstvo/NVIDIA-UNIX-driver/#power-saving](http://tutanhamon.com.ua/technovodstvo/NVIDIA-UNIX-driver/#power-saving) (and [http://linux.aldeby.org/nvidia-powermizer-powersaving.html](http://linux.aldeby.org/nvidia-powermizer-powersaving.html))

Since posting final settings promote copy-paste behaviour, I will just note that looking at "Configuration examples" after reading some about how it works in the main source is good.


hmm.. after some further digging I found this page
[https://blueprints.launchpad.net/ubuntu/+spec/desktop-lucid-powermanagement-tweaks](https://blueprints.launchpad.net/ubuntu/+spec/desktop-lucid-powermanagement-tweaks)

and there it says
>    "The driver already enables PowerMizer by default, and will connect to
   acpid to try to determine the system power state to adjust the
   PowerMizer strategy accordingly. These PowerMizer policies are
   carefully chosen by the laptop manufacturers, and setting the various
   RegistryDwords options overrides them which could lead to poor
   performance, system instability, or in the worst case, overheating. I
   recommend not ever setting any options using RegistryDwords."

Sooo. I am removing my settings as it is already appropriately implemented..

---

### Post by n.l.o on 2010-08-27
> **jose1986 said:**
> So, I have noticed this for some time but never really dealt with it.  Basically, I have a dual boot with Windows 7 and Ubuntu 10.04.  Windows 7 with a never dimmed light gives me 3 hours of battery but when it is dimmed, seems I can get like 5 hours!  However Ubuntu kills my battery, I get maybe 2 hours whether I am dim or bright, probably less than 2 hours.  Lately I have tryed to install some fixes but I keep getting error messages.  


This could be what is wrong..there is probably nothing wrong with pm-utils-laptop-policy, but a kernel bug ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/524281](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/524281) )
Run sudo powertop (with it installed), and check if "load balancing tick" is high on your list...

Cheers

---

### Post by 3rdalbum on 2010-08-27
Ubuntu does not use 'su' to give you root access. Instead it uses 'sudo' - you can either prefix your chosen command with 'sudo', or write "sudo su" whenever you'd just type "su".

The password prompts when you try to gain root privileges are important. They not only stop malicious users from gaining root permission when you're away from your computer, but they also stop viruses and other malicious programs from gaining those permissions. In addition, most Linux programs will assume that your security system is intact and might not work properly if you've bypassed some of its protections.

I'm sorry I can't help with the power management issue, but at least I can fill you in with permissions.

---

### Post by jose1986 on 2010-09-05
sudo powertop, once I got it installed gave me a huge boost in my battery but how do I get it, so that it runs my suggestions from powertop as a startup program, so I will automatically start with a better battery, rather than going into terminal?

---


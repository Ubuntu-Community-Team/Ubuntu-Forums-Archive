---
title: "How I got 11.10 running YMMV"
date: 2011-10-23
forum: General Help
---

### Post by Fred Doolie on 2011-10-23
It took many hours of screwing around but I got it to install and boot up. I hope my adventures will help others.

Installed 11.10 and did the first boot. Nothing. Black screen. Ubuntu has always done this and sooner or later it boots but NOT 11.10. I waited 15 minutes!

Checked the forums and Google. No joy. Every "help" started out with "Hold down the left shift key to display Grub" or "Edit grub.cfg and remove/add...". My Monitor is in a "Out Of Range" mode. I cant see the grub menu and I cant boot Ubuntu to edit anything. 

Further playing around showed that I *AM* in the grub menu. I just cant see it. Using the arrows and enter showed that there are four options: 1) Does nothing. 2) Partly boots, shows a repair menu and then drops to a CLI. 3) Memory test.  4) Windows. 

Using #2 I found some options. The ones that helped (after a LOT of playing around and rebooting) were "Mount all partitions read/write" and "Rebuild Grub" or something like that.

After doing this more playing around showed that I now had more hidden choices.  Number 3 (Down-down-enter) is now another kernel and BOOTS UP UBUNTU!!!!!

After it booted and I logged in I used the crummy software manager to install Synapic and used Synapic to install "Startup-Manager".  Startup-Manager lets me set the grub resolution to something my monitor can handle; 1024x768. Now I can see the options.

Number one (the dead one) is a PAE Kernel. Option three is a regular kernel. That's the one that works for me so I used startup-manager to set that as default. Now I have Ubuntu joy!!!

OK, How to do it:  YMMV
These steps are not exactly in order. The fixer thing doesn't come up with the same options each time. What you want to do is:
Reboot the computer and when you get the black screen press down-arrow the enter to bring up the fixer thing. Choose an option then choose "Resume the boot" or whatever it is and drops to a CLI. Log in and enter "sudo reboot". Do this as many times as you need until you have chosen "Mount all partitions as read/write" and "Rebuild Grub".

After this at the black screen press down-arrow TWICE and then enter. If you get the memory test you didnt do all the steps. Press escape to reboot fromn the memory test and try again.

After you get a good boot install Synapic and startup-manager.  Use startup manager to change your grub resolution to 1024x768 in BOTH locations!! Change the grub default to the OTHER Ubuntu kernel! The non-PAE one.

Questions:
What's a PAE Kernel?
How do I totally remove the PAE kernel options from grub?

*Picks up all the torn-out hair from the floor and tries to glue it back onto my head.

---

### Post by Fred Doolie on 2011-10-23
Update. After all that work it turns out that 11.10 is sloooooooow. Windows take 15-20 seconds to respond to mouse clicks and open after long pauses. Videos run jerk-jerk-jerk and sometimes things just stop running for a while and the windows and screen turn grey. Yes, I installed the updated video drivers.

So....I went back to 10.04. 

Here's the weird thing. 10.04 also installs a pae kernel but THAT one boots up just fine. :shock:
-----------------------------
11.10 boots up right away after install and runs great on my under-powered netbook :shock::shock::shock:

---


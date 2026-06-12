---
title: "desktop shutdown"
date: 2010-05-28
forum: General Help
---

### Post by katzman2 on 2010-05-28
I have used UBUNTU consistently for about 5 months now, but have used Linux in one form or another for about 10 years. Never had a problem with automatic power shut down until now.
The PC is not a laptop and could not be construed as one. It is a home built desktop unit in a small server case (from Antec) built from a Soyo SY-P41S2 board. The keyboard is an old Gateway 2000 programmable which I never programmed and the video is from ATI and the network card is from Zyxel. Never had a problem before, but these auto logoffs started after Ubuntu 10.4 was set up.  The linux partition is set up in a 40 gig hard drive and the partitions are in ext 4 format.  
When working (not sitting still and looking), I have received a black screen suddenly (full screen terminal window-like the screen if working in DOS with no window manager) and a message that the system is checking the battery state and then loggs me off of the machine (back to the login window). No message that the battery is low and thus need to save work and log off like you would get from a lap top.
Tried checking the power settings but have not been able to find any settings out of line with what you would expect with a desktop.
This problem has continued for more than two weeks and is getting worse (more frequent). The text message that comes on the screen is "checking battery state" This is a desk top-I have not installed any laptop software and have not engaged any of the power down features or battery monitoring. I left that all alone since that is no concern to me. Now it will log me off due to battery state several times in an hours time.
Posted this in hardware/laptops and got noooo response at all.
[email]katzman2@excite.com[/email]:(:icon_frown:

---

### Post by jobix on 2010-05-28
How old is your computer? Maybe the little coin battery on the motherboard is getting old? I'd try to replace that and see if it helps. Also, I hope you have a backup of important stuff on your hard drive in case something goes wrong given that you mentioned that the problem seems to be getting worse.

---

### Post by akakingess on 2010-05-28
Just a shot in the dark, but have you created a new user with default settings to see if it behaves the same way?  I'm sure if you have been using Linux that long that you have, so, what about a clean install (after backing up, of course) and all the usual troubleshooting? Has it happened since you first put Linux on that computer, or just since you upgraded or put on 10.04? I'm just looking for a direction to head in, because I haven't heard of anything of that sort, but I am not nearly as experienced as you are, just sometimes a second pair of eyes and all that.

Actual, jobix makes a good point, don't know if it's still called the CMOS battery, but that's what it was called about 15 years ago, when I used to have to replace 'em ;)

---

### Post by katzman2 on 2010-05-28
FYI:
The last set up of Ubuntu was with 10.4 just after that came out.  Downloaded it using 9.1, burned a disk and set it up.  All upgrades pushed out have been installed.
Why would the software look for the system board battery.  Battery software was not installed at all.  Is there a place to go to remove any power related software since that seems to be what is kicking this off.  The log-offs seem to be at an interval;
I have looked at the logs, but there are so many I am not sure which one to look at since that may tell me where the problem is.
Thanks
katzman2

---

### Post by jobix on 2010-05-28
> Why would the software look for the system board battery.  

It might be the kernel especially since you say that you see a black screen. I've seen that happen before when I took out the CMOS battery on an embedded device.

> Battery software was not installed at all.  Is there a place to go to remove any power related software since that seems to be what is kicking this off.  

Try these. Maybe you can find something there:
[https://wiki.ubuntu.com/PowerManagement](https://wiki.ubuntu.com/PowerManagement)
[http://ubuntudemon.wordpress.com/2007/10/30/ubuntu-is-not-causing-aggressive-power-management/](http://ubuntudemon.wordpress.com/2007/10/30/ubuntu-is-not-causing-aggressive-power-management/)

> The log-offs seem to be at an interval;
Did you check the system temperatures - CPU? HD?

> I have looked at the logs, but there are so many I am not sure which one to look at since that may tell me where the problem is.
Search for keywords - battery, or power - in your log files.

---


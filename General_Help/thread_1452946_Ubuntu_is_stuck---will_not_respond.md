---
title: "Ubuntu is stuck---will not respond"
date: 2010-04-12
forum: General Help
---

### Post by tperwez on 2010-04-12
I am running Ubuntu 8.10. I just ran into this problem. I clicked the Firefox icon in the top panel (Firefox was already running but window minimized) to maximize the window and the mouse cursor got stuck. Now the Firefox is like half open (the window outline is there but nothing more). No matter what trick I try, the system does not get unstuck. I have tried

ALT + F2

as well as

ALT+CTRL+ESC

etc. Even the keyboard does not seem to be responding.

What solution would you suggest? I have Synaptic Package Manager, Terminal as well as Emacs open but none of them can be accessed.

I am kind of afraid that if I just turn the darn computer off, it
could cause some damage to software/hardware.

Any solution will be appreciated. Regards,

Tariq

---

### Post by colorlessprism on 2010-04-12
you could try CTRL+ALT+F2 login and type "ps aux" find the FF id and type "kill XXXX" and then go back by CTRL+ALT+F7. if your still not going you could restart gnome by going back to tty2 and type "sudo /etc/init.d/gdm restart"

---

### Post by tperwez on 2010-04-12
Thanks for responding. I forgor to mention this earlier. I have already tried 

ALT+CTRL+F2

yet no response at all. 

How do you

CTRL+ALT+F2 login

I m not sure I understood your advice very well? Could you please explain it a bit?


Regards,

Tariq

---

### Post by doas777 on 2010-04-12
have you tried Ctrl + Alt + F1? does it respond? (you can get back to the desktop with Ctrl + Alt + F7). if Alt + F2 is not working, then that likely means that gnome-panel is locked up.

first, in terms of shutting down safely, try this:
```

Hold Alt + Prntscrn (you will hold them through all the following keystrokes)
and slowly type 

r e i s u b

```after each letter you type, make sure that the hard disk access light goes out before hitting the next key. 
this command will shut your PC down gracefully, even if much of the system is locked.

if this happens again, we can look into the cause. there are some weird mouse bugs that seem to come up only with FF.

[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

---

### Post by tperwez on 2010-04-12
Hi doas777

I have tried CTRL+ALT+F as well as CTRL+ALT+F7. Nothing.

I have also tried the code you suggested: ALT+PRNTSCRN and then SLOWLY typed r e i s u b

I did not see the hard drive red light coming on at all. 

Any other suggestion? 

Regards,

Tariq

---

### Post by doas777 on 2010-04-12
> **tperwez said:**
> Hi doas777

I have tried CTRL+ALT+F as well as CTRL+ALT+F7. Nothing.

I have also tried the code you suggested: ALT+PRNTSCRN and then SLOWLY typed r e i s u b

I did not see the hard drive red light coming on at all. 

Any other suggestion? 

Regards,

Tariq

did the PC shutdown as you finished entering the letters? if not, then the lockup extends down to the kernel, and there is little to be done but pull the power. hopefully fsck will be able to correct any file system oddities that result (I'd guess that you have a 95% likelyhood of avoiding egregious consequences.)

does this happen often or is it the first time?

---

### Post by ajgreeny on 2010-04-12
After shutting down, depending on what stage synaptic had got to, be prepared to repair the install system which may have unconfigured packages or even broken packages.

You may need to run ```
sudo apt-get install -f
```and ```
sudo dpkg --configure -a
```to repair things.

---

### Post by tperwez on 2010-04-12
No the PC did not respond at all. It did not shut down, neither did the red light for hard disk come on when I pressed the keys.

Also, this has never happened before. I have had Ubuntu for the past three years on theis PC.

No application was active at that time as such excpet that I was trying to maximize the Firefox window. the computr was on the wireless network.

Tariq

---

### Post by tperwez on 2010-04-12
Hi ajgreeny

Thanks for the suggestion. I am ready to physically turn the computer off.

The Synaptic Package Manager was not doing anything that I know of. I had just opened it to look if certain script was available on the Ubuntu repository and that is it.

I will follow your instructions after I have physically turned the computer off. 

Regards,

Tariq

---

### Post by cdenley on 2010-04-12
You can try ctrl+alt+backspace to kill the xserver. I would suspect some kind of hardware failure. Are all the fans spinning on your power supply, video card, CPU, and chipset? Also, run memtest86 from the grub boot menu.

---

### Post by blueridgedog on 2010-04-12
When firefox gets out of hand, I just go to a terminal and type killall firefox.

---

### Post by blueridgedog on 2010-04-12
> **cdenley said:**
> You can try ctrl+alt+backspace to kill the xserver. I would suspect some kind of hardware failure. Are all the fans spinning on your power supply, video card, CPU, and chipset? Also, run memtest86 from the grub boot menu.

I believe that Ctrl+Alt+Backspace is deprecated.  I am not certain what replaced it though...if anything.

---

### Post by tperwez on 2010-04-12
Hi cdenley

I am not sure if I tried that key combination. I did try many others, though. Well, I have rebooted the computer and ran

sudo apt-get install -f

and 

sudo dpkg --configure -a

as was suggested by ajgreeny. The first command reported that no new packages etc were removed or installed. The second command ran silently.

As far as I can tell, the fans seem to be running fine and I do not see any other hardware problem.

How do I run memtest86 from the grun menu? I have never done anything like that before. How do I acess the grun menu? What does it mean? Regards,

Tariq

---

### Post by cdenley on 2010-04-12
> **tperwez said:**
> How do I run memtest86 from the grun menu? I have never done anything like that before. How do I acess the grun menu? What does it mean? Regards,

When you boot, before ubuntu loads, you should see a menu for a couple seconds. This is the GRU**B** menu If you hit an arrow, it should wait for you to select an option. One of the options should be memtest86.

---

### Post by tperwez on 2010-04-12
cdenley

Thanks. I will certainly run that command when I reboot after this session. Regards,

Tariq

---

### Post by doas777 on 2010-04-12
> **cdenley said:**
> You can try ctrl+alt+backspace to kill the xserver. I would suspect some kind of hardware failure. Are all the fans spinning on your power supply, video card, CPU, and chipset? Also, run memtest86 from the grub boot menu.

just fyi, Ctrl + Alt + Backspace does not work anymore unless you specifically enable it at your own risk. additionally, since the Ctrl + Alt + F1 didn't work, X is not the problem nor is the lockup happening within X. if the magic sysreq keys don't work, then your kernel isn't even listening for keyboard input.

if this is the first incidence of issue, it is way too early to consider hardware, unless there is already reason to believe that it is failing.


@Op :  memtest86 is just a diagnostic tool for checking ram to make sure it is fit. you can select it from the grub boot menu. if you dont see the menu at boot, press esc when prompted to enter the grub menu.

---

### Post by blueridgedog on 2010-04-13
> **doas777 said:**
> just fyi, Ctrl + Alt + Backspace does not work anymore unless you specifically enable it at your own risk.


Where do you enable it?

---

### Post by tperwez on 2010-04-13
Hi doas777

Thanks for your suggestion. When I rebooted the computer, I pressed ESC key to enter GRUB, but all I saw was a menu with things like:

Ubuntu  kernel #### (generic)


etc

The very first was already selected. I just pressed ENTER key and the system restarted. 

Where is the diagnostic menu? I am a bit confused about the memtest86. Could you please be a bit more specific as to what exactly I should be doing? I would appreciate your help. Regards,

Tariq

---

### Post by cdenley on 2010-04-13
> **tperwez said:**
> 
The very first was already selected. I just pressed ENTER key and the system restarted.

And what was the very last option?

---

### Post by doas777 on 2010-04-13
> **tperwez said:**
> Hi doas777

Thanks for your suggestion. When I rebooted the computer, I pressed ESC key to enter GRUB, but all I saw was a menu with things like:

Ubuntu  kernel #### (generic)


etc

The very first was already selected. I just pressed ENTER key and the system restarted. 

Where is the diagnostic menu? I am a bit confused about the memtest86. Could you please be a bit more specific as to what exactly I should be doing? I would appreciate your help. Regards,

Tariq
shoudl be the bottom most entry unless you dual boot. something like "memtestx86"

---

### Post by doas777 on 2010-04-13
> **blueridgedog said:**
> Where do you enable it?
this is for jaunty, but shoudl work fine in karmic -> .
[http://www.ubuntugeek.com/howto-enable-ctrl-alt-backspace-in-ubuntu-jaunty.html](http://www.ubuntugeek.com/howto-enable-ctrl-alt-backspace-in-ubuntu-jaunty.html)

be sure you understand that by quiting X in this manner you can lose data. once in a very blue moon, it might corrupt a configuration file, but this is far from common. when used wisely it can be handy, but I usually just reboot when I need to, and if it's locked I use the magic sysreq.

---

### Post by ajgreeny on 2010-04-13
It seems to me that all this talk about Ctrl+Alt+Backspace etc etc is completely pointless. The OS has already said that the keyboard accepts no input, that is to say, no key presses are seen by the system.  There is no point giving lots of different keyboard options to the OP, his keyboard is dead.

Regrettably the only way out from that is simply to use, and hold in the power switch/button, until the machine powers off, or if a desktop rather than a laptop, just pull the plug.

---

### Post by blueridgedog on 2010-04-13
> **ajgreeny said:**
> It seems to me that all this talk about Ctrl+Alt+Backspace etc etc is completely pointless

My bad...I did not mean to hijack the thread, but wanted to know.  20 years of Ctrl+Alt+Backspace is hard to break.

---

### Post by wiebe de haas on 2010-04-13
Hello Tarig,

When you start up the pc and get to the GRUB menu, by default Ubuntu (or another OS)
will be highlighted. That is the default boot-up. If you do nothing at this point GRUB counts down
the default number of seconds before proceeding with this boot. It you clicked the up or down
keys before the default time is up you will stop the timer and can choose another boot from the
list. Ubuntu, when installing GRUB adds to this list a memory check; usually third third or fourth item.

An idea is to install STARTUP-MANAGER into your applications. It's a great app, giving you control over what boots up.

---

### Post by tperwez on 2010-04-14
Hi wiebe de hass

Thanks for your comments. First, I do not have the system set up for any dual boot etc. This computer runs Ubuntu 8.10 only. Now when I press ESC to enter GRUB at start-up, I see a box that has the following kind of entries:

Ubuntu 8.10, kernel 2.6.27.17-generic
Ubuntu 8.10, kernel 2.1.27.17-generic (recovery mode)
:
:
:
Ubuntu 8.10, kernel 2.6.27.12-generic
Ubuntu 8.10, kernel 2.6.27.12-generic (recovery mode)


After the box, it says:

Use the Up or Dn key to select which entry to highlight.
Press ENTER to boot the selected OS, 'e' to edit commands before boot, ot 'c' for commandline.


I do not see memtest86 or anything like that anywhere. 

I would appreciate if someone could give any poinyers as to what I should do for memory check. Also, what can I do to install STARTUP-MANAGER into my applications. What does this mean? Regards,

Tariq

---

### Post by doas777 on 2010-04-14
> **tperwez said:**
> Hi wiebe de hass

Thanks for your comments. First, I do not have the system set up for any dual boot etc. This computer runs Ubuntu 8.10 only. Now when I press ESC to enter GRUB at start-up, I see a box that has the following kind of entries:

Ubuntu 8.10, kernel 2.6.27.17-generic
Ubuntu 8.10, kernel 2.1.27.17-generic (recovery mode)
:
:
:
Ubuntu 8.10, kernel 2.6.27.12-generic
Ubuntu 8.10, kernel 2.6.27.12-generic (recovery mode)


After the box, it says:

Use the Up or Dn key to select which entry to highlight.
Press ENTER to boot the selected OS, 'e' to edit commands before boot, ot 'c' for commandline.


I do not see memtest86 or anything like that anywhere. 

I would appreciate if someone could give any poinyers as to what I should do for memory check. Also, what can I do to install STARTUP-MANAGER into my applications. What does this mean? Regards,

Tariq

weird. well the easiest answer is to just download the livecd then:
[http://www.memtest.org/](http://www.memtest.org/)


Startup-Manager was a usefull tool in grub1, but I have been told by one of the devs on it, that it is not quite ready for grub2 yet, so I have been waiting until it is. 

to install startupmanager, you would simplly run:
```
sudo apt-get install startup-manager
``` and then it will appear in system -> Administration (or is it preferences...?).

---


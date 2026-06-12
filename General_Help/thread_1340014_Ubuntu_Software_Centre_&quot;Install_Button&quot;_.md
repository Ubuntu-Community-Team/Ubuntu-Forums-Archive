---
title: "Ubuntu Software Centre &quot;Install Button&quot; not working"
date: 2009-11-28
forum: General Help
---

### Post by ssj6akshat on 2009-11-28
Ubuntu Software Centre Button not working even after clicking 4-5 times(it used to work earlier).Website Button Still Works please help me solve this problem.:cry:

---

### Post by ssj6akshat on 2009-11-29
Someone Help Please

---

### Post by oxf on 2010-01-31
I have the same problem and have posted a seperate thread. For me its both the Install and Remove buttons. When I click nothing happens at all!
HELP PLEASE!!!

---

### Post by howefield on 2010-01-31
Are you able to install software via Synaptic Package Manager or using apt-get in the terminal ?

---

### Post by djchandler on 2010-01-31
> **oxf said:**
> I have the same problem and have posted a seperate thread. For me its both the Install and Remove buttons. When I click nothing happens at all!
HELP PLEASE!!!

Check your **Software Sources** under **System>Administration**. Some of the repositories are disabled performing a version upgrade, particularly software that is restricted, from third-parties or from the Medibuntu repository. Those need to be re-enabled.

There's a disconnect to the **apt-get** application that actually does the work. **Ubuntu Software Center** is simply a GUI front end less complex than **Synaptic Package Manager**. See if you can search in **Synaptic** for the package you are trying to to manipulate .

Please tell us what package you are trying to install or un-install through **Ubuntu Software Center**.

---

### Post by oxf on 2010-01-31
> **djchandler said:**
> Check your **Software Sources** under **System>Administration**. Some of the repositories are disabled performing a version upgrade, particularly software that is restricted, from third-parties or from the Medibuntu repository. Those need to be re-enabled.

There's a disconnect to the **apt-get** application that actually does the work. **Ubuntu Software Center** is simply a GUI front end less complex than **Synaptic Package Manager**. See if you can search in **Synaptic** for the package you are trying to to manipulate .

Please tell us what package you are trying to install or un-install through **Ubuntu Software Center**.

OK I was trying to install Startup Manager. I have just managed to install it in Synaptic without problem though.

FYI I just done a clean install of Karmic not an upgrade. However, the weird thing is that the same problem seems to occur when I try to remove something in Software Centre too. i.e clcking on the button doesnt do anything

Mike

---

### Post by djchandler on 2010-02-01
There's some dependency missing somehow. That's very strange. You may want to try re-installing the meta package **[B]ubuntu-desktop**[/B] in **Synaptic**. That's a shotgun approach as we say on our side of The Pond.

---

### Post by oxf on 2010-02-01
> **djchandler said:**
> There's some dependency missing somehow. That's very strange. You may want to try re-installing the meta package **[B]ubuntu-desktop**[/B] in **Synaptic**. That's a shotgun approach as we say on our side of The Pond.


Shotgun or not I'll take it! since no one else has come up with an answer. I assume theres no downside to trying that method?
I'm convinced theres nothing wrong with software centre per see because both apt-get in terminal and Synaptic work just fine.. So must be somethng to do with the "click" part .

Thanks!

---

### Post by oxf on 2010-02-02
Well nice try! Unfortunately that made no difference. I dont know?

Granted I can use Synaptic or apt-get instead but it would be nice to have the Software Centre functional. Given that the button to "Unlock" in System/Admin/loging Screen doesn't work either I have to assume its a button issue and not the Software Centre per se.

Annoying as everything else seems to work well

---

### Post by oxf on 2010-02-02
Any more ideas? I'm stumped..!

---

### Post by Atzu on 2010-02-02
Try reinstalling software center from synaptics (search for software center and right click then reinstall and then apply) :p good luck

---

### Post by djchandler on 2010-02-04
> Given that the button to "Unlock" in System/Admin/loging Screen doesn't work either I have to assume its a button issue and not the Software Centre per se.


Ah-ha!

This could be a keyring access issue. Try running software-center by striking the key combination "**Alt-F2**" and then enter "**gksu software-center**" in the dialog box. See if those buttons work then.

Have you changed your log-in password? If so, you may want to look at [this thread]("http://ubuntuforums.org/showthread.php?t=192281"). It seems you are actually getting the opposite of the original issue, but if after running software-center from the command line and it works, we may have a clue to solving your problem.

Here's what I posted on page 13 of that thread:

> Changed my login password, only to find I need to change it in two places. I had Evolution bugging me for access to the keyring in Jaunty. The fix was to change the password for login in seahorse.

I wonder why that does not happen automatically, or at least give you a warning if seahorse is installed.

Anyway, thanks to all above who discussed seahorse.

To change the login password in seahorse that is packaged with jaunty, open seahorse (2.26.1) at the command line, either by pressing alt-F2 or in the terminal, and typing in seahorse. Go to the Passwords tab (the far right), and right-click on Passwords login. Select change passwords, type in your old login password, then enter the new login password twice. 

Problem solved.


---

### Post by oxf on 2010-02-05
> **djchandler said:**
> Ah-ha!

This could be a keyring access issue. Try running software-center by striking the key combination "**Alt-F2**" and then enter "**gksu software-center**" in the dialog box. See if those buttons work then.

Have you changed your log-in password? If so, you may want to look at [this thread]("http://ubuntuforums.org/showthread.php?t=192281"). It seems you are actually getting the opposite of the original issue, but if after running software-center from the command line and it works, we may have a clue to solving your problem.

Here's what I posted on page 13 of that thread:

Ah-Ha indeed!!! :)
Yes when I launch Software Center  that way via the command line the buttons DO work! 

I only did this fresh install of Karmic last weekend (was using 9.04 before)  and have not changed password from the one I provided on install.

---

### Post by djchandler on 2010-02-06
I found a bug in the Gnome Keyring Daemon that could be causing a problem. There's also 277 known bugs in software-center, most not critical. Something about your installation has caused a convergence perhaps that most don't experience.

Here's access to the list of known bugs:

[https://bugs.launchpad.net/ubuntu/+source/software-center](https://bugs.launchpad.net/ubuntu/+source/software-center)

See if you can discern which may apply to you. Since I don't know what other programs you may have open when this occurs, hopefully you have a little time to vet this list and see if any apply to your situation.

Since we have a couple of work-arounds, it may not be worth your time.

---

### Post by colinjones on 2010-02-06
I had the exact same problem... both those buttons didn't work, and worked fine when I ran that command... realised that a few hours ago I had temporarily disabled the Policy Kit Authentication Agent in Startup Applications (as I am having a number of massive memory leak issues with it and a couple of other processes!) Re-enabled it, and logged back in... buttons work again just fine :)

---

### Post by oxf on 2010-02-06
> **djchandler said:**
> I found a bug in the Gnome Keyring Daemon that could be causing a problem. There's also 277 known bugs in software-center, most not critical. Something about your installation has caused a convergence perhaps that most don't experience.

Here's access to the list of known bugs:

[https://bugs.launchpad.net/ubuntu/+source/software-center](https://bugs.launchpad.net/ubuntu/+source/software-center)

See if you can discern which may apply to you. Since I don't know what other programs you may have open when this occurs, hopefully you have a little time to vet this list and see if any apply to your situation.

Since we have a couple of work-arounds, it may not be worth your time.

Thanks! 
I'll mess with that tomorrow, its late here now and I'll cause more trouble than its worth! I'll report back. Again thanks for the link!

---

### Post by oxf on 2010-02-07
> **djchandler said:**
> I found a bug in the Gnome Keyring Daemon that could be causing a problem. There's also 277 known bugs in software-center, most not critical. Something about your installation has caused a convergence perhaps that most don't experience.

Here's access to the list of known bugs:

[https://bugs.launchpad.net/ubuntu/+source/software-center](https://bugs.launchpad.net/ubuntu/+source/software-center)

See if you can discern which may apply to you. Since I don't know what other programs you may have open when this occurs, hopefully you have a little time to vet this list and see if any apply to your situation.

Since we have a couple of work-arounds, it may not be worth your time.

Well I found that I had policykit disabled in startup applications too.
 [https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/499937](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/499937)
Now that I have it enabled it seems to have resolved the problem both in Software Center and also Login Screen. 
Thanks!!

---

### Post by colinjones on 2010-02-08
oxf - could you please watch your polkitd, console-kit-daemon and the gnome authentication one (can't remember the exact process name!) over a few days and let me know if there memory allocations start to tread upwards?

eg my console-kit-daemon starts (after a reboot) at around 3.7MB, but slowly leaks and gets to several hundred MBs before I have to reboot!!

btw are you running cairo-dock? 

Col.

---

### Post by oxf on 2010-02-08
> **colinjones said:**
> oxf - could you please watch your polkitd, console-kit-daemon and the gnome authentication one (can't remember the exact process name!) over a few days and let me know if there memory allocations start to tread upwards?

eg my console-kit-daemon starts (after a reboot) at around 3.7MB, but slowly leaks and gets to several hundred MBs before I have to reboot!!

btw are you running cairo-dock? 

Col.

Sure.. I will keep an eye on them. However. I've not noticed anything odd so far. I'm not running cairo. If I notice anything I'll report back :)

---

### Post by ssj6akshat on 2010-04-28
This is a problem with Software Centre when used in Failsafe-Gnome.Switching back to normal gnome solves this.:guitar:

---

### Post by ssj6akshat on 2010-04-29
USC uses PolicyKit for privileges,In failsafe-gnome the PolicyKit daemon isn't started on startup.So software centre doesn't work,running it with root privilages(i.e. sudo,gksu) works,Manually starting policykit-daemon also works.

---

### Post by ceasefire066 on 2010-12-16
> **djchandler said:**
> Ah-ha!

This could be a keyring access issue. Try running software-center by striking the key combination "**Alt-F2**" and then enter "**gksu software-center**" in the dialog box. See if those buttons work then.

Have you changed your log-in password? If so, you may want to look at [this thread]("http://ubuntuforums.org/showthread.php?t=192281"). It seems you are actually getting the opposite of the original issue, but if after running software-center from the command line and it works, we may have a clue to solving your problem.

Here's what I posted on page 13 of that thread:

ya it worked!!!great,, thnx

---


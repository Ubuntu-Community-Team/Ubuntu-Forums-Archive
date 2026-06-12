---
title: "Keyboard disabled after sleep"
date: 2009-09-18
forum: General Help
---

### Post by CuddlyCombine on 2009-09-18
Greetings, everyone.

As a university student, my laptop is my best friend during class. However, as some professors like to go on long asides during note-taking, I put my computer into sleep mode while they rant for ten minutes (only when there isn't a plug nearby, of course).

Now, I recently switched to SuperOS (9.0.4, basically) from Vista, given Microsoft's incompetence and a desire to not have to struggle with Vista anymore. Everything is going fine, except for one thing: if I wake the laptop after I've put it to sleep, the keyboard stops responding. All of the buttons stop working. The touchpad works fine, and the power button responds, but I'm confused as to why the keyboard would stop working.

Any help is appreciated. This is a Sony VAIO PCG 3E2L.

EDIT: I'm completely unexposed to Ubuntu, so I have no idea how to do anything that doesn't involve the GUI. So, if you're going to give me a bunch of commands to type into a terminal, I'd appreciate basic info on how to do that first. Thanks much!

EDIT 2: Found potential workaround - shutting laptop lid and then opening will successfully run suspend/resume cycle, though without the password protection. I'll live with it.

---

### Post by CuddlyCombine on 2009-09-20
Bump.

So, after two days, I've stalked the Internet looking for anything to help me out. I've gone through dozens of similar-sounding problems, but all of them have different solutions which haven't worked for me; I've used xorg to set my layout, set it through preferences, and used a wireless keyboard without trouble. However, the laptop keyboard continues to not be detected after waking up from sleeping. Literally, none of the keys work. It isn't the connection, and it will work if I restart it and log in for the first time.

---

### Post by scrooge_74 on 2009-09-20
The powersaving modes has always being a problem with Linux, you should post the brand and model of your laptop since each one suffers from different problems.

Example I have an old compaq nx6110. With ubuntu 6.04 it would sometimes come back from hibernation, but not from suspend mode. With Ubuntu 7.10 there were some fixes that allowed me to use hibernation, but suspend mode will mess up the laptop. WIth Ubuntu 8.04 at least hibernation would work 99% of the time, suspend still did not work.

Now with Debian Lenny both suspend and hibernation work every time and will not be a problem for me. There were tweaks speciffically for my brand and model so you need to post yours so others can help out.

---

### Post by CuddlyCombine on 2009-09-20
> **scrooge_74 said:**
> The powersaving modes has always being a problem with Linux, you should post the brand and model of your laptop since each one suffers from different problems.

Example I have an old compaq nx6110. With ubuntu 6.04 it would sometimes come back from hibernation, but not from suspend mode. With Ubuntu 7.10 there were some fixes that allowed me to use hibernation, but suspend mode will mess up the laptop. WIth Ubuntu 8.04 at least hibernation would work 99% of the time, suspend still did not work.

Now with Debian Lenny both suspend and hibernation work every time and will not be a problem for me. There were tweaks speciffically for my brand and model so you need to post yours so others can help out.

As I said in my opening post, it's a Sony Vaio PCG 3E2L (at least, that's what the label on the bottom says).

---

### Post by scrooge_74 on 2009-09-20
Crap sorry, I guess I did not read all the way to the end :p


From what I being seeing and read before those problems relate to proprietary stuff that VAIOs have, I guess it aint going to be easy to fix your issues if ever possible.

Some bugs have being filled at [https://bugs.launchpad.net](https://bugs.launchpad.net) you can search see if there are solutions or work arounds, sorry cant help

---

### Post by CuddlyCombine on 2009-09-20
> **scrooge_74 said:**
> Crap sorry, I guess I did not read all the way to the end :p

That's ok, I appreciate any help in any case :) 

It works when I lock it, but the keyboard just doesn't get detected at all if I suspend... this is so puzzling!

---

### Post by scrooge_74 on 2009-09-20
Mine used to dissable the keyboard some times, it was frustrating, you can say it took 3 years of Linux moving forward for this issue to go away for my brand and model. Maybe you could check Debian 5.0 (Lenny) see if it fixes your problem

---

### Post by P4man on 2009-09-20
Its possible the keyboard controller needs a reset after waking up. You can set a kernel parameter to achieve that. Open a terminal (applications > accessories > terminal).

Then type (or copy/paste) the following command:

```
sudo gedit /boot/grub/menu.lst
``` 

(type your password, it won't show up, but thats normal, hit enter after the password).

You should now see your "grub" (bootloader) configuration file. Scroll down and find the newest (top) kernel line. it will look somewhat like this:

> title   Ubuntu jaunty, kernel 2.6.28-11-generic
root    (hd0,3)
kernel  /boot/vmlinuz-2.6.28-11-generic root=UUID=c8253db2-ac0b-4664-9e3c-837ce469a95d ro quiet splash
initrd   /boot/initrd.img-2.6.28-11-generic

change it to;
> title   Ubuntu jaunty, kernel 2.6.28-11-generic
root    (hd0,3)
kernel  /boot/vmlinuz-2.6.28-11-generic root=UUID=c8253db2-ac0b-4664-9e3c-837ce469a95d ro quiet splash **i8042.reset**
initrd   /boot/initrd.img-2.6.28-11-generic

(note that is a lowercase letter i followed by 8042.reset)
Save the file, reboot, cross fingers :)

---

### Post by CuddlyCombine on 2009-09-20
> **P4man said:**
> Its possible the keyboard controller needs a reset after waking up. You can set a kernel parameter to achieve that. Open a terminal (applications > accessories > terminal).

Then type (or copy/paste) the following command:

```
sudo gedit /boot/grub/menu.lst
```(type your password, it won't show up, but thats normal, hit enter after the password).

You should now see your "grub" (bootloader) configuration file. Scroll down and find the newest (top) kernel line. it will look somewhat like this:



change it to;


(note that is a lowercase letter i followed by 8042.reset)
Save the file, reboot, cross fingers :)

Still the same after reboot; after suspend, keyboard stops functioning (even though, strangely enough, I can use the keyboard to get to the login screen). Even the numlock etc. buttons don't do anything. 

This bug has been around since Hardy, apparently, and is hardware-dependent (a lot of Vaios seem to suffer from it). However, nobody really has a fix.

I stumbled upon /etc/acpi/resume.d/, which manages what gets initiated when the system resumes - I was wondering if, maybe, there's a keyboard file to add to that list?

EDIT: Strangely enough, suspending then shutting the lid and opening it will resume the system fine enough (everything still works).

---

### Post by scrooge_74 on 2009-09-20
lol 

magic solution

problem resides with the fact the equipment has propietary hardware and Sony dont want us to know all their trade secrets

Glad to hear you found a work around

---

### Post by CuddlyCombine on 2009-09-20
> **scrooge_74 said:**
> lol 

magic solution

problem resides with the fact the equipment has propietary hardware and Sony dont want us to know all their trade secrets

Glad to hear you found a work around

Seems like it! :D I guess I'll mark this solved, and just hope that I never suspend the comp. I'm probably going to wear out the lid hinges in a week this way... :P

Thanks for the help though, you two. Long live open-source! :guitar:

---

### Post by P4man on 2009-09-21
Id file a bug report on that in launchpad.

But perhaps you can work around it. Post the output of:

```
cat /etc/acpi/events/lidbtn
```

Thats the script that gets executed when you close the lid. It probably just calls this script "/etc/acpi/lid.sh". If it does, post the contents of that script: 
```
cat /etc/acpi/lid.sh
```

The script that gets called when you suspend from the menu I *think* is /etc/acpi/sleepbtn.sh. you can run either script from the terminal by putting sudo in front of it, so for instance:

```
sudo /etc/acpi/sleepbtn.sh
```

You can find out which one works and which one doesn't, and change accordingly.

---

### Post by CuddlyCombine on 2009-09-21
> **P4man said:**
> Id file a bug report on that in launchpad.

But perhaps you can work around it. Post the output of:

```
cat /etc/acpi/events/lidbtn
```Thats the script that gets executed when you close the lid. It probably just calls this script "/etc/acpi/lid.sh". If it does, post the contents of that script: 
```
cat /etc/acpi/lid.sh
```The script that gets called when you suspend from the menu I *think* is /etc/acpi/sleepbtn.sh. you can run either script from the terminal by putting sudo in front of it, so for instance:

```
sudo /etc/acpi/sleepbtn.sh
```You can find out which one works and which one doesn't, and change accordingly.

This is where me being a newbie kicks in.

I ran the first script, and basically all it said was that it runs the second script. 

So, I ran the second, and it gave me a lengthy output of functions that it does.

Then, I ran the third, and it went to sleep as if I'd pressed the button, then failed to resume. 

Where do I go from here?

EDIT: It did resume, but it just went to the login screen (as always) and the keyboard was unresponsive. Same as always.

---

### Post by P4man on 2009-09-21
"cat" shows the script, it doesn't run it. You can run it with "sudo" (sudo lets you execute something with root or admin privilidges). So to try running the script that (I think) runs when you close the lid, run

```
sudo /etc/acpi/lid.sh
```

See if that suspends and resumes properly.

---

### Post by CuddlyCombine on 2009-09-21
> **P4man said:**
> "cat" shows the script, it doesn't run it. You can run it with "sudo" (sudo lets you execute something with root or admin privilidges). So to try running the script that (I think) runs when you close the lid, run

```
sudo /etc/acpi/lid.sh
```See if that suspends and resumes properly.

It goes through, but nothing happens. I'm assuming that's because the lid is still open.

---

### Post by P4man on 2009-09-21
yeah you're right. It tests for the lid status (which i don't have as Im on a desktop now)
I dont think im familiar enough with the acpi scripts to tell you what to change where, perhaps someone else can chime in.

---

### Post by CuddlyCombine on 2009-09-21
> **P4man said:**
> yeah you're right. It tests for the lid status (which i don't have as Im on a desktop now)
I dont think im familiar enough with the acpi scripts to tell you what to change where, perhaps someone else can chime in.

Would it be possible to SSH into the laptop from my PC and get it to feed the PC a log of events when I type in said commands? 

I'm assuming I'd have to find out a way to keep the wireless connection om, as that's one thing that gets suspended while the laptop is sleeping.

That's the only idea I have, though. I really appreciate everyone's help, though - you're all amazing! C:

---

### Post by CuddlyCombine on 2009-09-21
> **P4man said:**
> yeah you're right. It tests for the lid status (which i don't have as Im on a desktop now)
I dont think im familiar enough with the acpi scripts to tell you what to change where, perhaps someone else can chime in.

Sorry to double-post, but, I ran xinput in the terminal and there are three keyboard devices. One is device-specific (Sony Vaio keys, apparently), while another is virtual and the last I can't figure out. Maybe there's some way to initialize one at resume?

---

### Post by scrooge_74 on 2009-09-21
> **CuddlyCombine said:**
> Would it be possible to SSH into the laptop from my PC and get it to feed the PC a log of events when I type in said commands? 

I'm assuming I'd have to find out a way to keep the wireless connection om, as that's one thing that gets suspended while the laptop is sleeping.

That's the only idea I have, though. I really appreciate everyone's help, though - you're all amazing! C:

In past before suspending laptop I used to first disable the wifi card cause when it came back it would do all kind of weird stuffs on me.

I'm also not very familiar with the acpi scripts so sorry cant help on that

---

### Post by CuddlyCombine on 2009-09-23
Bump, and this user is sad.

I've just upgraded to Karmic, and the same problem - suspension, even if there's no login required, kills my keyboard. 

Urgh!

---

### Post by scrooge_74 on 2009-09-23
Propietary hardware, that will always be your problem with that laptop. Keep at it hopefully a solution will present either in this forum or in one of the others like linuxquestions.org

---

### Post by CuddlyCombine on 2009-09-23
> **scrooge_74 said:**
> Propietary hardware, that will always be your problem with that laptop. Keep at it hopefully a solution will present either in this forum or in one of the others like linuxquestions.org

I can only hope so!

---

### Post by opex on 2009-10-23
I have a HP and not a VAiO but I had similar problems with keyboard being none responsive after hibernation.

Following a few threads I found a solution working for me.
First of all you can check if this applies to you by running the following command```
cat /proc/bus/input/devices
```and locate something looking like this:
```
I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio2/input/input14
U: Uniq=
H: Handlers=kbd event5 
B: EV=120013
B: KEY=20000 20 0 0 500f02100003 3803078f900d401 feffffdfffefffff ffffffffffffffff
B: MSC=10
B: LED=7
```What we hope to find is i8042 in the Sysfs line.

The next step would be to create a script in /etc/pm/sleep.d/
So run the command
```
sudo (your text editor by choice) /etc/pm/sleep.d/25-i8042
```and paste the following
```
#!/bin/bash

case "$1" in
	hibernate|suspend)
	# Unbind the AT keyboard interface.
		if [ -f /sys/bus/platform/drivers/i8042/unbind ]; then
			echo -n "i8042" > /sys/bus/platform/drivers/i8042/unbind
		fi
	;;
	thaw|resume)
	# Rebind the AT keyboard interface.
		if [ -f /sys/bus/platform/drivers/i8042/bind ]; then
			echo -n "i8042" > /sys/bus/platform/drivers/i8042/bind
		fi
	;;
	*)
	;;
esac

exit $?
```The last thing to do is make the script executable by running
```
sudo chmod +x /etc/pm/sleep.d/25-i8042
```

And we're happy hybernating

---

### Post by P4man on 2009-10-23
You could also try adding 

```
i8042.reset
```

to your kernel boot options,. If you're not sure how, here is how:
[https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation](https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation)

edit: damn, In repeating myself, sorry...

---

### Post by CuddlyCombine on 2009-10-23
> **opex said:**
> useful stuff

Thanks a lot for the help! However, it didn't get my machine working; the same problem persists. :( I think Sony hates me.

---

### Post by salvatore25 on 2010-01-19
Hallo!
This is my first post.
I have the same problem with a VAIO VGN-Cs11S.

I noticed that in /dev/input/ event 4 (the one associated to the keyboard i8042) ha disappeared.

Hope this can help to the discussion.
Bye

---

### Post by levis lover on 2010-06-03
i have a similar model and the same problem.
I am using Ubuntu 9.10
When running on battery it goes into sleep mode after ten minutes of keyboard inactivity. And after wake up keyboard stops responding. Is there any way i can stop it from going into the sleep mode when on battery ? I tried the GUI way but same problem persists.

---

### Post by levis lover on 2010-06-06
anyone??

---


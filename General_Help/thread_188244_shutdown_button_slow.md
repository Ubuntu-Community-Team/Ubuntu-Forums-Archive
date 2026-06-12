---
title: "shutdown button slow"
date: 2006-06-03
forum: General Help
---

### Post by frizzl on 2006-06-03
well my system was running great and still is, except one thing

when i click th eshutdown button... it doesnt do anything. about 5 mins later the shutdown menu appears. (im talking about the menu with logout, restart etc)

and after that initial 5 mins, it will load up instantly (as it should)

however, no other programs are this slow... what could be the problem?

my system is DEFINENTLY fast enough to handle the OS...

---

### Post by rbo83 on 2007-11-06
This may be a different problem but if you have disable the 'Power Management' options in the 'Sessions' preferences (as some would if they do not use a laptop), the power management daemon is dead and the shutdown is waiting for an answer from the daemon until it times out. This can take between 30 seconds to 5 minutes. You MUST enable the Power management for now. This problem also exists in Gutsy.

---

### Post by SyL on 2007-11-07
I've got the same issue but the power management seems to don't change anything.

Someone else??

---

### Post by minus198 on 2007-11-07
> **SyL said:**
> I've got the same issue but the power management seems to don't change anything.

Someone else??

That is the only answer.. 
But you got to do the command: "gnome-power-manager" so that is starts.

---

### Post by habtool on 2007-11-10
I am also having this problem.

Its like Gutsy does not want us to leave  :)

For what its worth if i click the exit button it takes say 60 seconds to respond.

But once it does and I click cancel, then if i click exit again its then instant with no further delays

---

### Post by Psykotik on 2007-12-28
Any news?

I have same issue, and I was thinking about logging the call "gnome session" process; anyone knows how to achieve this?

---

### Post by eeefresh on 2008-02-21
Any updates on this?

  I am having the same problem.  If I click the power button, I have to wait at least a full minute before the options appear.  I can't use anything else during this time, either.  The weird thing is that if I cancel the shutdown, then click the power button again, it pops right up without a delay!

---

### Post by link0007 on 2008-04-29
There is a brute work-around for this, which is using the shutdown command.

Add a new launcher to the panel, and give it this command:

sudo shutdown -h -P now

You can drag this launcher next to the quit icon, if you unlock all special stuff (date, volume, etc)


Edit: another fix I just found:

> **dysphasi said:**
> Basically, from what I gather, you should be doing as follows:

[1] In a terminal enter: ```
 sudo gedit /etc/modules 
```

[2] At the very bottom of the file opened, add the following line:
```
apm power_off=1
```save and exit.

[3] Back in the terminal, enter ```
 sudo gedit /boot/grub/menu.lst 
```

[4] Maximize the window to better see everything and search for the line: ```
End Default Options
```

[5] Just below this line you will see paragraphs listing: title, root, kernel, initrd to the left side, something like below:
```

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=419086cc-9136-45e9-9369-d7fe44edff76 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic

```
Each of these paragraphs represents one of your login options at the grub boot menu when you power on. It is the first one (the one that you log into ubuntu with) that you'll need to add any options to.

[6] At the end of the line beginning "kernel" add the text:
```
acpi=off apm=power_off
``` 
Using my example above, my paragraph would now appear as follows:
```

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=419086cc-9136-45e9-9369-d7fe44edff76 ro quiet splash [color=red]**acpi=off apm=power_off**[/color]
initrd		/boot/initrd.img-2.6.22-14-generic

```
(nb...this is where you add any of the lines you might find, from the info you found for example, you'd want to add [color=red]**acpi=force**[/color] instead)
Save, exit, power off, restart, log in and try it out.

ps: Doesn't work for me and I've tried all the options I could find! :(
Hope it helps you out!

Worked fine here:popcorn:

---

### Post by pip182 on 2008-05-01
I am also having this same problem. On TWO computers running Hardy, they both do the exact same thing. I will try out your fix and see if it works. 

I hope the ubuntu devs can get this fixed soon, this is a really annoying bug. It also seems to come and go on my machine. Sometimes it works fine, other times it takes forever to show up.

---

### Post by kosak on 2008-07-02
Check with Boot-up Manager (or sysv-rc-conf, etc.) if you have disabled ACPI & ACPI-SUPPORT. I disabled them and the lag began, now I re-enabled them and shutdown GUI works as it should. :guitar:

---


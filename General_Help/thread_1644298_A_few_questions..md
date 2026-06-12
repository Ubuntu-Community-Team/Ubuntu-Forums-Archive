---
title: "A few questions."
date: 2010-12-13
forum: General Help
---

### Post by ppnl on 2010-12-13
I'm playing with a new install of Ubuntu and I have a few questions about how things are working.

1)I used update manager to update the system. I didn't expect many updates given that it was a new install of v10.10 but there was like 209 megs of updates. When I rebooted it crashed but did reboot the second time after the disk checked itself. Everything seems to be working correctly. But I noticed the grub boot menu has an extra entry. I am now booting 2.6.35-23-generic. I still have an option to boot 2.6.35-22-generic which is what was booting before the update. Can someone explain what is going on here?

2)I would like to remove the timer to choose what to boot on startup. I understand that I must edit a line in etc/default/grub to do this. It is a read only system file and the way I can figure that might do it is open a terminal and run "gksudo gedit" which I think will open gedit with the permission it needs to wright changes to the system file. Will this do it or am I gonna trash my system if I do that? Is this the preferred method for changing system files? 

3)I ran the "gksudo gedit" command and it asked for my password. Cool. I closed out gedit and ran gksudo command again and it opened gedit without asking for my password. Not so cool. Is the permissions it grants to gedit persistent? That would kinda be bad. Um, I just thought, is it persistent for as long as the terminal window is open? Didn't check that...

Anyway just trying to reduce the number of time I have to reinstall as my fatal mistakes accumulate. Learning is fun but can be destructive. Thanks for any help.

---

### Post by squaregoldfish on 2010-12-13
1) Updates to Ubuntu tend to come much more frequently than other OSes. This is a function of the fact that most of the programs and components are managed by different groups who all release updates and patches on their own schedule, and since there's so many groups it means updates happen more or less constantly.

The two entries in the grub menu are as a result of these updates. Whenever a Linux kernel update is released, it's installed alongside the existing version so you have the option of going back a step if the new version doesn't work as expected - if the kernel breaks you have no OS. If you're happy that the new kernel is working OK, you can manually remove the old kernel packages via synaptic.

2) As long as you trust the instructions you've been given, and follow them closely, you have the right approach to editing the grub config file. You'll only screw up your system if you do it wrong!

3) gksudo remembers your password for a short time for convenience, in case you're running multiple sudo commands close together (which is frequently the case). It will ask for your password again after a while. I'm afraid I don't know what the time limit is, or how you'd adjust it.

HTH
Steve.

---

### Post by rotave on 2010-12-13
If you install StartUpManager it will allow you to adjust the timer at boot.

---

### Post by QLee on 2010-12-13
[QUOTE=ppnl]...
3)I ran the "gksudo gedit" command and it asked for my password. Cool. I closed out gedit and ran gksudo command again and it opened gedit without asking for my password. Not so cool. Is the permissions it grants to gedit persistent? That would kinda be bad. Um, I just thought, is it persistent for as long as the terminal window is open? Didn't check that...
...[/QUOTE]

As squaregoldfish already explained this correctly, I'll just add this. 

It can be changed by adding a timestamp_timeout line to the sudoers file, /etc/sudoers. For example timestamp_timeout=2, for a two minute timeout. The best way to edit that file is with the command, sudo visudo. Other editors can work but they don't check what you are trying.

For more information and explanation, enter, man sudoers, in a terminal window to see the manual page for sudoers.

---

### Post by ppnl on 2010-12-13
1) I'm not surprised that Ubuntu preserved a previous state. Having the previous state as a boot option is unexpected and interesting. I like it.

2)I'm not following instructions on how to change system files. I just figured out how I maybe could do it but chickened out of doing it until I asked. Linux can be unforgiving compared to windows. But then it lets you do so many cool things.

3)The persistence of permissions of gksudo is a surprise and I'm not sure it is a good idea. In any case it is good to know about it. 

Anyway thanks guys.

---

### Post by marin123 on 2010-12-13
> **ppnl said:**
> 1) I'm not surprised that Ubuntu preserved a previous state. Having the previous state as a boot option is unexpected and interesting. I like it.

2)I'm not following instructions on how to change system files. I just figured out how I maybe could do it but chickened out of doing it until I asked. Linux can be unforgiving compared to windows. But then it lets you do so many cool things.

3)The persistence of permissions of gksudo is a surprise and I'm not sure it is a good idea. In any case it is good to know about it. 

Anyway thanks guys.

2) startup manager or grub-customizer are good ways of customizing boot and not messing up the whole system :)
i added a background picture and removed old kernels with grub customizer, and of course, shortened timeout.

---

### Post by QLee on 2010-12-13
[QUOTE=ppnl]...
3)The persistence of permissions of gksudo is a surprise and I'm not sure it is a good idea. In any case it is good to know about it. 
[/QUOTE]

The persistence of sudo permissions can be a fine idea if the user wants those permissions again before the timeout, and that seems to be the case fairly often. New users make mistakes and have to redo what they have just tried to do. People coming from a less secure operating system often complain about having to type a password even once to do something on the system they "own". 

It could easily be a bad idea if you use sudo with a long timeout and then go away and leave your terminal for someone else to use. However, you wouldn't do that without locking the screen or logging off, would you? A default install locks the screen when the screensaver is activated, thus requiring a password to get back in. 

But if someone has physical access to your system, enough time, enough knowledge and skill, your system isn't safe anyway. Well, maybe an encrypted system would be safe enough, they could just delete everything though.

---

### Post by cascade9 on 2010-12-13
> **QLee said:**
> But if someone has physical access to your system, enough time, enough knowledge and skill, you're system isn't safe anyway. Well, maybe an encrypted system would be safe enough, they could just delete everything though.

Physical access = root access. The number of times I've told people that and not been believed is insane. It was really funny when my old boss told me 'thats BS, you cant see my files without my password' then went to lunch....the look on his face when he came back to find I'd imaged his HDD and was browsing his files was priceless.  BTW, NOT a good idea to keep your porn collection on a work computer (and if your going to, think of your sysadmin, and please make it good porn at least) 

Though you are right, encryption would at least slow somebody down.

---


---
title: "Default Runlevel 10.10"
date: 2010-12-20
forum: General Help
---

### Post by 2handband on 2010-12-20
How do you change the default runlevel in Ubuntu 10.10? I need a solution that I can execute by editing text files; right now I'm accessing the Ubuntu filesystem by mounting it to another OS on a different hard drive. 

The long and the short of it is that I'm getting a blank screen at login time. I suspect it's a driver issue (I have an Nvidia card) and it shouldn't be hard to fix... but I need a console. And no, I can't get in via Grub... my main OS is Slackware and Lilo is controlling the bootloader. So I need to be able to change the runlevel, and thus far a Google search has proved unenlightening.

---

### Post by WorMzy on 2010-12-20
Doesn't lilo have a boot prompt? You just need to add "text" or "single" to the kernel options. If it doesn't have a boot prompt, maybe you can reconfigure lilo somehow?

That's the easiest option I can think of. Other than that, all I can suggest is messing with [upstart]("http://www.linux.com/archive/feature/125977").

---

### Post by 2handband on 2010-12-20
Oh, dear god. I thought Ubuntu was supposed to be the most user-friendly OS on the planet... I just read the article you linked, and this Upstart thingy is now going to make it about ten times harder to modify the system's default behaviors. And as near as I can tell there isn't a multi-user console mode. What the heck? Is the assumption being made that no user is ever going to want to do anything but boot into a graphical desktop?

---

### Post by efflandt on 2010-12-20
During a normal boot there are the normal Alt (or Ctrl+Alt from X) F1-F6 consoles, if your graphics are not totally screwed.

Did you install grub on a partition and chainload that from lilo, or don't you have grub at all?

The (recovery) grub menu entries include **ro single** kernel boot parameters which bring you up into a menu to **resume** (normal login console), fix packages automatically, **netroot** (root console with networking), or **root** console, etc.  Something there should allow you to check what is going on.

If you use **resume** and login as yourself, once you fixed whatever you think needs fixing using sudo, you can start X using **startx** command or **sudo start gdm** (assuming gnome) probably goes to gui login.

PS: I have not used lilo for many years.  Looking at an old drive that dual booted Mandrake 7.0 and FreeBSD 5.x, if you were trying to boot Ubuntu recovery directly, you would likely need to include the following in that lilo.conf entry:

```
append="single"
read-only
```

---

### Post by 2handband on 2010-12-20
I think I've got it sorted out, actually... I created a /etc/inittab in the Ubuntu installation. I can't test it yet cus I have a couple of large builds going on in the Slack install, and I have to wait for them to finish before I reboot. I'm still a little miffed about the lack of multi-user console, however.

---

### Post by WorMzy on 2010-12-20
> **2handband said:**
> Oh, dear god. I thought Ubuntu was supposed to be the most user-friendly OS on the planet... I just read the article you linked, and this Upstart thingy is now going to make it about ten times harder to modify the system's default behaviors. And as near as I can tell there isn't a multi-user console mode. What the heck? Is the assumption being made that no user is ever going to want to do anything but boot into a graphical desktop?

I guess so. I think Ubuntu is new-user friendly, rather than advanced-user friendly. It cuts down your options and makes it harder to do certain things so that it's harder to bork it (or easier, considering the horror stories with false dependencies removing half the system). There's far better distros out there for advanced users; personally, I use Arch - no false dependencies, rc.conf and inittab rather than upstart, grub legacy rather than grub2, single config files for apps rather than twenty config config files and a script to generate the real one.

---


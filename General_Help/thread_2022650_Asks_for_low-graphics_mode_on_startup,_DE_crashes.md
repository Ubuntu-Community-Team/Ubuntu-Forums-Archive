---
title: "Asks for low-graphics mode on startup, DE crashes"
date: 2012-07-11
forum: General Help
---

### Post by compiz addict on 2012-07-11
I was typing this out as I was trying a few things, and I solved the problem myself. I'll post this in case anyone else has a similar problem (and so you all can laugh at me :P). I ran update-grub (well, update-burg for me) and encountered a graphics problem. It turns out that updating grub (burg) added Kernel 3. It seems that 3 has some issues with my installation where 2.6 does not. Booting to kernel 2.6 instead solved the problem.

Here's what I was typing in here before I fixed it:
:popcorn:

A little while ago I thought it would be fun to set my computer not to start x automatically (that way I could go to a console first, and type /etc/init.d/gdm start or startx when I want to use graphics). I tried a couple of things:
1. sudo update-rc.d -f gdm remove (I forget if I actually used the "-f" switch. Maybe I tried both.)
2. changing GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" in /etc/default/grub to GRUB_CMDLINE_LINUX_DEFAULT="quiet splash text" and running update-grub (also did the same thing with burg [I'm running a grub alternative], because doing it to grub didn't change anything)

... there's a possibility I tried something else in the mix too, but not to my recollection.

2nd thing worked, and my bootscreen changed (big blue "Kubuntu" boot-screen to regular "Ubuntu" with dots below). When I tried to start x though, I'd always get the dreaded "low graphics mode" message. Choosing "restart x" worked fine, but I didn't like it, so I changed it back (to "quiet splash"). Rebooted, and it still popped up. Also, the boot-screen never changed back. Oh well, I restarted X and everything worked fine.

Until the next morning... (dramatic music start)

I wake up and turn on my computer, restart x and all, and everything crashes - gnome-panel freezes and so do all my applications. Everything was crashing or running extremely slow (everything graphical?) but my mouse (what a shame - it's funnier when the mouse freezes too). 

Tried rebooting twice after that. No change in this strange behavior (even gdm laggs).

Choose to go into a terminal the next time I got the dreaded low-graphics message. Entered the following command in attempt to fix it:

```
$ sudo update-rc.d -f gdm defaults
update-rc.d: warning: /etc/init.d/gdm missing LSB information
update-rc.d see <http://wiki.debian.org.LSBInitScripts>
 System start/stop links for /etc/init.d/gdm already exist.
```

...and then in case GDM was the problem:
```
$sudo dpkg-reconfigure kdm
```

Now the boot-screen doesn't go away - it's like my desktop is booting forever! Hilarious!

Changed it back to GDM (using dpkg-reconfigure kdm again) and everything is back to slow and crashing and low-graphics message.

Low graphics message I'm getting:
```

Ubuntu is running in low-graphics mode

The following error was encountered. You may need to update your configuration to solve this.

(EE) NVIDIA: Failed to load NVIDIA kernel module. Please check your
(EE) NVIDIA:    system's kernel log for additional error messages.
(EE) Failed to load module "nvidia" (module-specific error, 0)
(EE) No drivers available.

```

---


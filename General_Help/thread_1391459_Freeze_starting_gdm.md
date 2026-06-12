---
title: "Freeze starting gdm"
date: 2010-01-26
forum: General Help
---

### Post by quatchi on 2010-01-26
I'm running Ubuntu 9.10 (x86-64) and, about a week ago, my machine has started freezing up while booting at the point of loading gdm and I could use some help diagnosing the problem.

If I boot normally, I get to the screen with the ubuntu logo (white logo on black background).  After this, the screen switches to the splash screen with a brown-ish background and a progress bar.  The freeze-up happens in this transition and all I'm getting is a black background with the wait curser (which is also frozen up).

I checked my logs and the only thing that jumps out at me is a block of unprintable characters in messages.log  Not sure what that's about, but I can attach my log files if that would help.  I'll also note that dpkg-reconfigure gdm (and xserver-xorg) didn't seem to reconfigure anything.  And, while I can get a login shell prompt if I boot to recovery mode, it freezes up if I try to start gdm from there the same way.

Anyway, I'd appreciate any help with this.  Thanks.

---

### Post by Muscovy on 2010-01-26
I had a problem exactly like this after messing with my kernel. Did you do anything there?

---

### Post by quatchi on 2010-01-26
I suppose it could have happened after an update.  I sometimes get kernel-related updates shown in the update manager but grayed out.  I think I updated the kernel since via apt-get update since the problem began.  Maybe I'll have to wait for another round of kernel updates.  How did you solve your problem?

---

### Post by abh83 on 2010-02-04
> **quatchi said:**
> I'll also note that dpkg-reconfigure gdm (and xserver-xorg) didn't seem to reconfigure anything.

I'm having the same issue after installing banshee and some updates.

How do I dpkg-reconfigure gdm and xserver?

---

### Post by quatchi on 2010-02-08
See here:
[http://ubuntuforums.org/showthread.php?t=187177](http://ubuntuforums.org/showthread.php?t=187177)

You might have to use 'sudo' with those commands (e.g., sudo dpkg-reconfigure gdm).  I didn't read the whole thread-- there might be more useful hints there.

I still don't have a fix.  I ended up partitioning my hard drive and reinstalling until I get things sorted out.  I'd used a repository to get the most up to date kernel releases (in order to get my graphics card working, I think).  I'll try disabling that and waiting for a kernel update or the next Ubuntu release and see what happens.

> **abh83 said:**
> I'm having the same issue after installing banshee and some updates.

How do I dpkg-reconfigure gdm and xserver?

---

### Post by quatchi on 2010-04-06
Just a quick status update.  I updated my ubuntu to the lucid development release and that fixed this particular problem.  It's a development release (Beta 1) with some unresolved issues of its own, but I have successfully booted.  Instructions for updating a 9.10 system to 10.04 from the command line (which I did by booting to the recovery console) are below.  It says Ubuntu Servers, but I did this on a Desktop version of Ubuntu (64 bit).
[B][SIZE=2]
[https://help.ubuntu.com/community/LucidUpgrades](https://help.ubuntu.com/community/LucidUpgrades)[/SIZE]
[/B]

**Network Upgrade for Ubuntu Servers (Recommended)**

 
[LIST=1]
[*]Install update-manager-core  if it is not already installed: 
 sudo apt-get install update-manager-core
[*]edit  /etc/update-manager/release-upgrades and set Prompt=normal
[*]Launch the upgrade tool: 
sudo do-release-upgrade --devel-release
[*]Follow the on-screen instructions.
[/LIST]

---


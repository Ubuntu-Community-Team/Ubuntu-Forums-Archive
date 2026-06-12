---
title: "Restore admin rights"
date: 2010-07-04
forum: General Help
---

### Post by alfh on 2010-07-04
Some of my admin rights are suddenly gone, probably because of accidentally deleting a folder or settings file. Now I cannot access network seetings or even shut down the machine except through sudo commands in the terminal.

I'm still able to run synaptic and other programs, but synaptic cannot access internet. Neither can firefox or other applications, but vuze is connecting fine. I guess this has to do with proxy settings, but who knows...

How can I restore full admin rights to my user?

Edit: So internet connection is mysteriously back, eliminating one headache! Question remaining is how to restore full admin rights to my user?

---

### Post by alfh on 2010-07-05
Since I can sudo stuff through the terminal, it seems like it's just gnome who thinks I'm no admin anymore. So instead of reinstalling completely, could I remove and reinstall gnome-desktop? Is this possible to do without messing up my programs and settings?

Bringing up the dialog for user administration is almost fun, it says I'm the computer admin, but trying to click any admin buttons just produces no result. What's worse is I can't even auto-mount DVD's or my music player anymore.

Thankful for any input on this issue!

Alf

---

### Post by -humanaut- on 2010-07-05
I'm not entirely sure what you could have deleted to lose rights on everything are you sure your proxy is valid? you can change individual rights with chmod but I don't know exactly what you'd change them to do you just not have Network permissions?

---

### Post by alfh on 2010-07-06
Through gui I cannot manage internet settings, cannot manage users & groups, cannot mount DVD's or music players (no permission), cannot shutdown or reboot (only log out). Possibly there are more issues.

Through the terminal I can issue sudo commands to shut down and power off, but running gksudo nm-connection-editor still brings up a dialog with greyed-out options to edit connections. I do not know how to administrate internet settings, users, etc by command line tools.

I tried resetting gnome's defaults by renaming .gconf - no luck.

Seriously considering complete reinstall of my system ](*,)

---

### Post by sisco311 on 2010-07-06
Hmm, lets see if sudo and polkit are configured correctly. Please post the output of:
```
groups
```
```
sudo cat /etc/sudoers
```
```
cat /etc/polkit-1/localauthority.conf.d/*
```
and
```
pkexec echo polkit
```

---

### Post by alfh on 2010-07-06
Thank you for posting!

output of groups:
> myuser adm dialout fax cdrom floppy tape audio dip video plugdev fuse lpadmin netdev admin sambashare

Output of cat /etc/sudoers:
> 
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL

# Allow members of group sudo to execute any command after they have
# provided their password
# (Note that later entries override this, so you might need to move
# it further down)
%sudo ALL=(ALL) ALL
#
#includedir /etc/sudoers.d

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

Output of cat: /etc/polkit-1/localauthority.conf.d/*:
> No such file or directory

Output of pkexec echo polkit (without sudo):
> Segmentation fault

Output of pkexec echo polkit (with sudo):
> User of caller (1000) does not match our uid (0)

So from the last message I gather it's possible my user ID changed?

---

### Post by sisco311 on 2010-07-06
> **alfh said:**
> 
So from the last message I gather it's possible my user ID changed?

Nope, the problem is that pkexec segfaults. Try to reinstall PolicyKit. Which version of Ubuntu are you using?

---

### Post by alfh on 2010-07-07
So I tried to reinstall policykit-gnome, which didn't help. I'd try to remove it before reinstall, but then synaptic is ready to let brasero, rhytmbox and a bunch of other programs go as well.

Why does dependencies work this way? Doesn't make sense that I have to remove a lot of programs when I only want one to go :-k

Oh, and I'm running Lucid Lynx on an IBM netvista pentium IV - quite old stuff, though working well as long as I stay away from rendering DVD's and other processor-demanding tasks...

---

### Post by alfh on 2010-07-08
Fixed my problem!

After gksudo nautilus I had deleted my etc/polkit-1 folder. I didn't remember the name of the deleted folder, and clicking the Trash folder took me nowhere - so I thought the files were gone for ever and started this thread. Then it occurred to me to check where root actually hides the trash.

I found the deleted folder in /root/.local/share/Trash and copied it back to original location.

Now everything works like before - and I'm just a little bit wiser. Do. Not. Delete. Files. Unless. You. Are. Sure. Really. Sure. Especially. As. Root. :D

---


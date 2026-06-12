---
title: "Changed Hostname and now it doesn't boot"
date: 2009-07-19
forum: General Help
---

### Post by hatecrewdeathroll on 2009-07-19
Right so i'm a Ubuntu noob using Jaunty and i changed the hostname file without changing the host file also (at least i think that's what i did wrong)and now it won't boot. Luckily, i have my Vista partition. Is there any way to change the file back? I only installed ubuntu to play around with and i'm using wubi, so i can just uninstall ubuntu like i would a normal program. Should i kill it or is there a way to fix it?

---

### Post by CatKiller on 2009-07-19
> **hatecrewdeathroll said:**
> Should i kill it or is there a way to fix it?

In a normal install, you could just boot in Recovery mode, which would give you a root shell, to enable you to change the hosts file without having to use sudo (which gets broken by changing one file but not the other). I've never used Wubi, so I don't know what options are available.

---

### Post by angry_johnnie on 2009-07-19
After selecting Ubuntu from your Windows bootloader, click Esc.  Just make sure to click Esc immediately before Ubuntu actually starts booting (before you see the Usplash image).  Once you do that, it should take you to Grub4Dos (or whatever it's called), where you'll find a few options, the first one being your regular boot, and the second one being the recovery mode.  Boot with recovery mode.  It will take you to a root prompt, which should allow you to fix your hosts file.

---

### Post by mavis311 on 2009-07-20
> **CatKiller said:**
> In a normal install, you could just boot in Recovery mode, which would give you a root shell, to enable you to change the hosts file without having to use sudo (which gets broken by changing one file but not the other). I've never used Wubi, so I don't know what options are available.

What is the proper way to change the hosts file?  

I've attempted to change my hostname a couple of different ways, but every time I reboot, its back to what it used to be.  I've tried on a standard install and an install under wubi with the same results.  I have not manually edited any file, however.  

The methods I've seen say to use "hostname newhostname" at the command line and then reboot.  One also said after changing with hostname to "/etc/init.d/networking restart" which should finalize changes.  

I've seen some things that say to edit a HOSTNAME file, and now this says to edit the "hosts" file.  

Exactly what file needs to be edited and where is it located?

---

### Post by CatKiller on 2009-07-20
The old networking tool had the means to do it graphically. NetworkManager doesn't yet have this functionality, unfortunately.

The problem is that sudo uses the hostname for verification purposes in a way that I don't understand, and if you change one file but not the other sudo doesn't work. Which means that you can't change the contents of the other file. The trick is to open them both as root before you save either of them.

The two files are /etc/hostname (which should **just** contain the hostname) and /etc/hosts (which has the hostname at the same address as localhost and any DNS-style aliases that you want to use).

The *hostname* command only changes the hostname until the computer is rebooted. **man hostname** will tell you more about that command.

---

### Post by slakkie on 2009-07-20
See this thread [http://ubuntuforums.org/showthread.php?t=1055393](http://ubuntuforums.org/showthread.php?t=1055393)

---

### Post by mavis311 on 2009-07-20
Sounds like slakkie is on to something with that other thread.  I'm using 9.04 and don't have any problems booting.

I booted into recovery mode, and as root, removed hostname and did "echo newhostname > hostname" then reboot.  That worked with no problems.  Interestingly, I did not have to change the hosts file, but decided I probably should anyway.

After a normal boot, I opened a terminal window and issued "sudo gedit /etc/hosts & sudo gedit /etc/hostname"  This opened both files in gedit... sometimes.  I tried it again and it would only open one file and the other process was stopped.  I'm still learning the linux lingo.  Anyway, then I just modified the hosts file and then closed gedit which then asked me to save open files.  Everything is working fine.

Don't know why it was so difficult to get the changes to stick.  Also, I've searched "change hostname" and variants on this forum numerous times and haven't come up with much that was helpful.  Lots of hits, but few that were useful.  I guess it's just me.

---


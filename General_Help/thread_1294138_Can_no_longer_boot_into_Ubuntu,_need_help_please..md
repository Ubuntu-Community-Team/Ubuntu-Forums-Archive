---
title: "Can no longer boot into Ubuntu, need help please."
date: 2009-10-17
forum: General Help
---

### Post by jukingeo on 2009-10-17
Hello all,

I have been having trouble with Ubuntu for the past few days that seeming started with my wanting to gain access to the .wine folder without having to constantly uncheck the "hidden folders" file in my main (home) directory.  The trouble is that I think I may have inadvertently changed some permissions and at first I wasn't able to get into Gnome and I was bounced back to another gui I have on board, which is LXDE.

From there I attempted to solve the problem via this post I made:

[http://ubuntuforums.org/showthread.php?t=1291676](http://ubuntuforums.org/showthread.php?t=1291676)

I followed the suggestions made by the individuals here and now I cannot get into Ubuntu at all...even with using sudo at the prompt in recovery mode.

Needless to say, I think something is royally screwed up and I am wondering if anything can be done to save it, or do I have to reinstall Ubuntu.

When I start up the system in recovery mode, I have made note of some of the lines that came up as "failed" and I will write them down here:

Start-Stop Daemon: Unable to start /sbin/klogd: Permission Denied (Failed)

Starting Avahi mDNS/DNS-SD Daemon  Time out reached (Failed)

Starting Hardware abstraction layer hald (The system hangs here for about 7 to 10 mins before moving on)

Starting Gnome Display Manager--Failed

Sudo can't open /etc/sudoers: Permission Denied (Failed)

Then comes the prompt and when I put my login and password in, it seems to be accepted, but then it loops back to the login.  Intentionally typing in anything will say login failed.  So it seems that the prompt is acknowledging my password but isn't doing anything.

If I try to log in to recovery mode prompt only using root I get the sudo can't open /etc/sudoers: Permission Denied message.

That is basically what is happening when I go into recovery mode.  In a normal boot, I get taken right to the prompt after the very long delay at "hardware layer abstraction hald".  Of course my login doesn't work.

I didn't realize that trying to set the permissions for one folder would end up completely knocking my system out.  However, I need to get Ubuntu working again as soon as possible because I am working on a video presentation for Halloween and I am in the midst of it.

Thank you,

Geo

---

### Post by stinger30au on 2009-10-18
if you boot from the live cd can you access you hdd

if so back up you data and fasa

format
and
start
again

---

### Post by jukingeo on 2009-10-18
> **stinger30au said:**
> if you boot from the live cd can you access you hdd

if so back up you data and fasa

format
and
start
again

So you are saying that I am screwed? (at least partially).  I have set up Ubuntu into a directory structure and I do have separate boot and home partitions.  So is there a way to just reload the OS and still have my settings and information intact?

Thanx,

Geo

---

### Post by jlh68 on 2009-10-18
I believe that with a separate Home and Boot partitions that you should be able to reload the OS into the Boot partition without touching your Home partition data.

---

### Post by cariboo on 2009-10-18
Use the manual partition option when you get to the partitioning section, and tell the installation to use your /home directory, but not to format it. You may have to repair the permissions in your  home directory, you can do that once the installation is finished:

```
sudo chmod -R 755 /home/<user>
```

where <user> is your username. You will get an error about .gvfs, but just ignore it.

---

### Post by jukingeo on 2009-10-19
> **jlh68 said:**
> I believe that with a separate Home and Boot partitions that you should be able to reload the OS into the Boot partition without touching your Home partition data.

Hello,

Yes, I do recall that I DID follow the advice and set up my machine on multiple partitions. I think it was boot, Home(root), programs, and swap (if I recall correctly).

So how do I just reload the boot information and keep all my settings intact?

---

### Post by jukingeo on 2009-10-19
> **cariboo907 said:**
> Use the manual partition option when you get to the partitioning section, and tell the installation to use your /home directory, but not to format it. You may have to repair the permissions in your  home directory, you can do that once the installation is finished:

```
sudo chmod -R 755 /home/<user>
```

where <user> is your username. You will get an error about .gvfs, but just ignore it.

Will this will keep all my settings and stored info intact?
What do I do to repair the permissions?

Thanx,

Geo

---


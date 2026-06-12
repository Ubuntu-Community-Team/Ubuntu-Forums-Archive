---
title: "network-manager service prevents PC from sleeping"
date: 2012-03-07
forum: General Help
---

### Post by rage_311 on 2012-03-07
After a recent package upgrade, my Kubuntu 11.10 (with KDE 4.8.1) installation is no longer able to sleep -- whether I do it manually or after the configured inactivity time has elapsed.  In /var/log/pm-suspend.log I get the messages:
```
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.
```
I get something similar for the resume messages too.  So, I manually unloaded the driver for my only network card via
```
sudo modprobe -r r8169
```
with no success.  Then I manually stopped the network-manager service with
```
sudo service network-manager stop
```
and was able to make the PC sleep successfully.  My question is... where do I go from here?  I can't think of any other network-related configurations that have changed.

Any help is greatly appreciated!  Thanks.

---

### Post by Arathon on 2012-03-08
This isn't a solution, per se, but a workaround - since you seem to have successfully isolated the problem, you could at least automate the successful sleep scenario that you found.

In particular, I'd suggest creating an executable bash script in the /etc/pm/sleep.d directory, called 56_network_manager_stop, containing the following code:
```
#!/bin/bash
case $1 in
     suspend)
	 service network-manager stop
	 ;;
     resume)
	 service network-manager start
 	 ;; 
esac

```

If it's executable, that hook will run more or less right after 55NetworkManager (which is in /usr/lib/pm-utils/sleep.d/). 

If you find that you ALSO need the r8169 module unloaded, that could go into an executable file /etc/pm/config.d/modules with the line
```
SUSPEND_MODULES="r8169"
```

For what it's worth, I found your post because I was having my own suspend issues as of recently.... I did a bunch of fooling around with a lot of different things, and even tried your suggestions here, and nothing worked. Eventually the problem turned out to be an older external USB storage device that I had been using off and on recently. When it's not plugged in, things seem to go off without a hitch. It's still a bug (Windows sleeps fine with this thing plugged in), but at least I finally figured out how to get around it. Ubuntu without sleep is mostly useless for my needs.

---

### Post by rage_311 on 2012-03-08
Thanks for the reply!  It looks like that script didn't do the trick, even though it appears to successfully stop (and restart on resume) the network-manager service.  It must have to do with the timing of events during suspend and resume...

I found something else that's interesting -- if I use 
```
sudo pm-suspend
```
everything suspends and resumes as normal; even when I don't use any workarounds to stop/start the network-manager service.  So, what's the difference between using the Application Launcher > Leave > Sleep and doing a ```
sudo pm-suspend
```?  I noticed that I don't get a login screen when I resume after doing the pm-suspend.  The system just comes back up to where I left it.

So, a recap of my successful methods right now:

1. Manually typing "sudo service network-manager stop", then using the Sleep option in the Application Launcher.  (I also have to manually start the network-manager after resume.)
2. Typing "sudo pm-suspend" in the console.  This is manual and doesn't provide a locked/login screen upon resuming.

Any ideas?

---

### Post by Ardetus on 2012-03-09
Just to confirm symptoms - I met exactly problem after upgrade to the KDE 4.8.1 (Sony VAIO with Kubuntu 11.10)...

---

### Post by rage_311 on 2012-03-09
Thanks for the additional information.  It might be related to the newest KDE version(s) then.  I will try to roll back my KDE version (to 4.7.x) when I get home tonight and report back.

Ideally though, I'd still like to keep KDE 4.8.1 and create a fix for this, if anyone has any more ideas on what I could do.  Please let me know if I can provide any additional info to help with troubleshooting this problem.

---

### Post by Ardetus on 2012-03-13
Looks like after unmounting all NFS mounts suspending works normally, at least on my laptop.

---

### Post by rage_311 on 2012-03-14
Manually unmounting my NFS mounts before sleeping fixes my problem too.  I can't get it to happen via script though (by trying a "umount /mnt/server" variation of Arathon's script example).  Very frustrating...

Any suggestions?  I'd just stick with samba, since that seems to function properly with sleep/resume still, but for some reason, transfer rates to and from my server's samba shares are about 1/5 of the speed of the same share via NFS -- and the same share via samba on my Windows 7 partition.

EDIT: Also, any help on an easy way to revert my KDE packages back to 4.7.x?  I followed instructions on this page [http://www.webupd8.org/2012/01/kde-48-released-install-it-in-kubuntu.html]("http://www.webupd8.org/2012/01/kde-48-released-install-it-in-kubuntu.html") to upgrade via the Kubuntu backports ppa.

---

### Post by rage_311 on 2012-03-15
Indeed, it seems like that should work.  But, in my reply to Arathon's original message suggesting that, I mentioned that it didn't actually work as planned for some reason.  I ended up getting exactly the same results as I did without that script in place (and yes, it was executable).  If I ran it manually, however, with "/etc/pm/sleep.d/56_network_manager_stop suspend", then clicked the Sleep button, it worked just fine.  Do I need a delay somewhere?  The messages in pm-suspend.log didn't indicate any problems with the 56_network_manager_stop suspend or resume calls.

---


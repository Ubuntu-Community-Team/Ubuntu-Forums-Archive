---
title: "FTP will not function until ipchains is disabled/re-enabled via Firestarter"
date: 2010-04-01
forum: General Help
---

### Post by Ntr0s on 2010-04-01
FTP Server OS: Ubuntu x64 9.10
Client OS: Ubuntu x64 9.10

I have an FTP server on my home network.
FTP Server: VSFTPD with TLS

My FTP server is running with iptables configured using firestarter.   Firestarter Inbound Traffic Policy "allow Service / Port contains the FTP service with the appropriate port range, vsftpd.conf port range is identical, as is the port range on my router.

My Client system, only after reboot or  system power on, absolutely will not connect to the FTP server unless the firewall is disabled then re-enabled by way of firestarter then re-enabled.  

Only then will my client successfully connect and continue to connect until my client reboots or powers on.  At which point I need to disable/re-enable iptables through firestarter.

Others can connect to my FTP server, but they use a mixture of Mac and Windows with default firewall settings.

Has anyone experienced this with firestarter and ubuntu 9.10?
I never had this problem using Ubuntu 9.04.

Thanks.

---

### Post by Ntr0s on 2010-04-01
One of my main concerns is how do I know if by disabling/re-enabling iptables through firestarter, if other protocols are being unintentionally enabled.

---

### Post by Ntr0s on 2010-04-01
I found a workaround to my problem.

OK first, I've been reading quite a bit of ipchains and iptables documentation over the past few days; the names have become one and the same in my mind.  In my previous post I meant "iptables" not "ipchains" - edited the previous posts.

 I mentioned that I could only connect to my FTP server if I restarted iptables via firestarter.  I was wrong.  I can only connect to my FTP server after reboot or power on if I first launch the firestarter GUI

So, I added "sudo /usr/sbin/firestarter --start-hidden" to Startup applications and "username ALL= NOPASSWD: /usr/sbin/firestarter" to /etc/sudoers.  Rebooted, Firestarter GUI launches and now I can access my FTP server immediately after reboot or power on.

WTF?  This should not be happening. I made no changes to the firestarter config.  I'm trying to determine what has changed, if anything, and why this is happening now.

---

### Post by 3rdalbum on 2010-04-02
1. Why are you using Firestarter? It's buggy and unmaintained, and I'm sure I've had a similar problem to yours in the past. If all you're doing is using it as a personal firewall, then you might as well use gUFW.

2. You mention you have a router with a firewall... why have you got a personal firweall on the server? The router's firewall is protecting the server (and your clients) already.

I don't think you need Firestarter OR gUFW. You're already firewalled by your router. And by the way, unless you want people online to be able to access your FTP server, you shouldn't be forwarding the FTP port on your router.

---

### Post by Ntr0s on 2010-04-03
Yes, port forwarding is enabled on my router intentionally.

I did not specifically mention a firewall on my router in my previous posts, unless you were referring to my port forwarding comment, but your right.  Except the firewall on my router is not stateful.  That's what I want, a stateful firewall.

I had decided that I was going to build a stateful firewall appliance based on Linux / IPTABLES.  But, I found out today that DD-WRT and OpenWRT are now compatible with my router.  I think I'm going to go that route for now and see how well is suits my network and servers.

I had never tried firestarter but read so many good reviews about it, I had to give it a try.  I only saw that it was not maintained until you mentioned it, and the after I ran a search for "firestarter no longer maintained".

Honestly I had no idea that Firestarter was no longer maintained until you mentioned it.  It was my own undoing.  It took me many many hours to finally remove Firestarter and return my network connections to their original state.  Damn.  Well, you live and you learn.  An application that can wreak havoc on system security and network connectivity should not be available for public use or download.  Open source or not.

Anyway, thank you for the info.

This is what I had to do to remove Firestarter.

1. open the Firestarter GUI.
2. disable the firewall through the GUI.
3. exit firestarter.
4. command sudo apt-get purge firestarter
5. command  locate firestarter
6. Remove all existing firestarter files in the following loacations if they exist:

ran command  sudo locate firestarter:  this is what was listed.

/etc/firestarter
/etc/init.d/firestarter
/etc/network/if-down.d/50firestarter
/etc/network/if-up.d/50firestarter
/etc/ppp/ip-down.d/50firestarter
/etc/ppp/ip-up.d/50firestarter
/etc/rcS.d/S65firestarter
/home/ballisox/firestarter-events.txt
/home/ballisox/Documents/firestarter-events.txt
/root/.gconf/apps/firestarter
/root/.gnome2/firestarter
/usr/sbin/firestarter
/usr/share/firestarter
/usr/share/app-install/desktop/firestarter.desktop
/usr/share/app-install/icons/firestarter.png
/usr/share/applications/firestarter.desktop
/usr/share/doc/firestarter
/var/lib/update-rc.d/firestarter

The only files / dirs where firestarter existed, after the uninstalling / purging firestarter, at least on my system were:
I Manually deleted these:
/var/lib/update-rc.d/firestarter
/root/.gconf/apps/firestarter  - deleted the entire folder
/root/.gnome2/firestarter - deleted the entire folder

7. ran command as root  iptables -F    ***"--flush  -F [chain] Delete all rules in  chain or all chains"***
8. ran command as root  iptables -Z  ***"--zero -Z [chain] Zero counters in chain or all chains"***
9. reboot.

After reboot, samba, FTP protocol, SSH, vsftpd and internet connectivity was all restored.

---


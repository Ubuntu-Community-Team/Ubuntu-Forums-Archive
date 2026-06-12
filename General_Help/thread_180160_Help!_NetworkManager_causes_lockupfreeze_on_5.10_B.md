---
title: "Help! NetworkManager causes lockup/freeze on 5.10 Breezy Badger"
date: 2006-05-21
forum: General Help
---

### Post by munckfish on 2006-05-21
Hi

I have quite a serious problem which I think is linked with NetworkManager. 

Last Wednesday night I experienced a complete system lockup - all apps on the screen suddenly froze, the keyboard appeared to accept no input at all I couldn't even Ctrl+Alt+F1 into a pseudo terminal. I had to hard reboot.

After initial heart-break at having experienced something like this on my Linux system ;), I set about trying to diagnose the problem. 

My first thoughts were that it must be related to X and my graphics card/drivers. But I don't think this is the case. I have an ATI Mobility Radeon X700 and I'm using the ATI provided binary drivers. I can't see any errors in Xorg.0.log, and I can run fgl_glxgears without any issue. 

After a couple of days of believing it was random I remembered when I first noticed the problem I was using Firefox and I think I was fiddling with nm-applet. When I fiddled with nm-applet again I realized I could consistently recreate the lockup by following these steps:

  a. After the connection to the wireless access point is up, right click on nm-applet and select 'Stop all wireless devices'
  b. Now as quickly as possible right click on nm-applet again and select 'Start all wireless devices'. IMPORTANT: if you leave too much time before carrying out this step the freeze doesn't occur.
  c. At this point the system freezes.

I don't think the problem has anything to do with the recent known issue with DRI as I have tried the fix on [http://ubuntuforums.org/showthread.php?p=201964](http://ubuntuforums.org/showthread.php?p=201964) and the problem still occurred.

I've checked /var/log/syslog for NetworkManager messages but I can't see any errors at the point just before the system locks and is restarted. I know NetworkManager makes use of dbus/hal could it be that sending messages via nm-applet too quickly is sending either of these two systems into an error state and consequently locking up all Gnome/GTK/X apps? Searching on Google for 'hal freeze lockup' shows up older mailing list posts which indicate this sort of scenario did occur in earlier development versions.

I've now exhausted my knowledge of how to debug Linux issues with this and am now not sure what I can do next, can anyone assist me in debugging this problem?

I've attached files containing system information and an excerpt of the syslog messages logged while I recreated the lockup.

Thanks.

---

### Post by tribaal on 2006-05-21
Try "killall NetworkManager", then start Networkmanager from the terminal. 
Maybe some of the terminal output isn't copied in the logfiles?

Just a thought.

- trib'

---

### Post by munckfish on 2006-05-21
Doesn't appear to be anything new in the output from NM. Final message before the lockup is:

NetworkManager: <information>	Deactivating device eth1.

and then it locks.

There is a warning message at an earlier stage though:

NetworkManager: <WARNING>	  (): get_ip4_string(): error calling 'domain_name', DHCP daemon returned error 'org.freedesktop.DBus.Error.UnknownMethod', message 'Method "domain_name" with signature "" on interface "com.redhat.dhcp.dbus.get" doesn't exist
'.

Although I don't think this is related as I've seen it in syslog before: it occurs frequently but the net connection does come up ok.

Attached NetworkManager output anyway in file nm.log.txt. I went three times through the steps to recreate - the first two times are slower successful restarts of the network, the third time features the lockup.

---

### Post by munckfish on 2006-05-25
Update: I've now noticed it locking my system as I log onto the desktop. It hangs just after putting the keyring password into the prompt. It did this 2 times in a row, 3rd time I put the network cable in so it didn't use the wireless connection by default, and that got me on successfully. Nothing obvious in the logs, no similar problems running under XP so I'm (hoping) presuming this isn't a hardware problem.

I'm going to have to try to find time to dig deeper into the workings of NetworkManager and it's dependencies and hopefully learn something on the way even if I don't manage to solve it. :-?

---

### Post by munckfish on 2006-07-21
May have been due to this: [Re: NetworkManager and vmware bridged network?]("http://mail.gnome.org/archives/networkmanager-list/2006-March/msg00257.html")

---


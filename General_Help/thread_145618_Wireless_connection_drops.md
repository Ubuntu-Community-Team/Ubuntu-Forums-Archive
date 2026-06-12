---
title: "Wireless connection drops?"
date: 2006-03-16
forum: General Help
---

### Post by Robor on 2006-03-16
I've got Ubuntu 5.10 installed on my T42 laptop with the Intel 2200BG Pro wireless adapter.  I'm using the standard Network Manager that came with Gnome to manage the adapter and I'm connecting to a Linksys WRT54G with Talisman firmware on it.

I've got WEP turned on and usually (but not always) the wireless card starts and I've got network access.  However, sometimes the system will come up and my wireless card doesn't have an IP address.  Other times I'll be working fine then walk away for a bit and come back to see Evolution couldn't access my mail and Gaim has dropped connection.  

I've tried doing a deactivate and activate on the wireless.  When I do that sometimes it will come back with an IP but I can't ping anything.  Other times it stays at 0.0.0.0.  Either way, I always have to reboot to get back on the network.

Other than the obvious (problem with card or router) is there some reason my connection is dropping?  My wireless works fine in Windows.  Is there a better wireless adapter manager I should be using?  If so, do I have to disable or uninstall the current manager?

Thanks for any help!

---

### Post by dpaint4 on 2006-03-16
Yep. Me too. I just go to the network manager, disable, and then enable again. That always works, but hopefully this will be ironed out.

The only reason I landed on Ubuntu at all is because I tried and tried and tried every distro that I could find, and none of them could support wireless like I needed until now, with Ubuntu, so I just accept this as a big step up, and a tollerable distraction.

---

### Post by Hangetsu on 2006-03-16
<posted to wrong thread, oops!>  :rolleyes:

---

### Post by Robor on 2006-03-20
Ah, so I'm not the only one with this problem?  What type of laptop are you using?  What wireless adapter does it have?  

I had the drop-off happen to me overnight on Friday then when I came home that night it had dropped again.  I must confess that for the first time in months I booted my dual boot setup to WinXP out of frustration.  I left it there night and no drop-off.  I booted back into Ubuntu Sunday morning and it dropped again during the day.  I rebooted to Ubuntu and it was still up this morning.  No rhyme or reason to the drops but I'm a Linux/Ubuntu noob so I couldn't begin to know where to look for clues.  :confused: 

I guess I'll put up with this annoying network drop-off since Ubuntu Dapper should be just around the corner.  Hopefully it's got a better built-in wireless management utility.

---

### Post by jimrz on 2006-03-23
Install NetworkManager for effortless networking

Do not use the network monitor applet on the upper right Gnome menu panel; instead, right-click on it and select Remove from Panel. (You can always put it back by right-clicking on the panel and choosing Add to Panel.) After enabling additional repositories for the update manager, use Synaptic to dowload and install network-manager (notice the spelling, which includes the hyphen between the two words). You will see no visible change in your system after the program has been installed; close Synaptic. Use System | Preferences | Sessions, go to the Startup Programs tab, and use the Add button to add the following command:

nm-applet

Assign it an order of 10 or some other low number so that it runs soon after you log in. Close the dialog. Log out and log in again.

When your Gnome session begins, you will see the NetworkManager icon on the Gnome panel at the top. If you have a wired network, your network should be working perfectly. If you want to use a wireless network, click on the NetworkManager icon and select the network you want. You will be prompted to create a password for the default keyring; choose a brief, easy-to-type password, because you may be prompted to enter it often. Follow the prompts to connect to your preferred network.

With NetworkManager running, your system should automatically switch between wired and wireless networking whenever you attach or detach an ethernet cable; the changeover typically requires five seconds. In some instances, you may need to click on the NetworkManager icon to remind it to make the switch, but it normally works perfectly.

To turn off the wireless radio, right-click on the NetworkManager icon and choose Stop All Wireless Devices. The same menu lets you restart wireless devices.

Borrowed from [[COLOR="Sienna"]**_this_**[/COLOR]]("http://www.columbia.edu/~em36/ubuntubreezythinkpadt42.html#intro") excellent how to for breezy on a T42  (thanks Edward) that I have had great success following.

---

### Post by Robor on 2006-03-31
Thanks jimrz...  After I upgraded the kernel it broke my wireless so I upgraded the ieee80211, firmware, and driver and so far everything has been totally stable.  I'm going to use the, 'if it isn't broke, don't fix it', motto until I start having problems.  Then I'll give that wireless manager a try.  I've got it book marked and Emailed to myself.  

Thanks again!

---

### Post by underwater on 2006-03-31
I experience the same problem with my ipw2200bg so I almost am beginning to think that it is some problem with the drivers.  I can get around it by using the hardware on off switch on my dell, FN+F2.

---

### Post by Robor on 2006-04-10
[QUOTE=underwater]I experience the same problem with my ipw2200bg so I almost am beginning to think that it is some problem with the drivers.  I can get around it by using the hardware on off switch on my dell, FN+F2.[/QUOTE]

Have you tried reloading it with the latest kernel, firmware, driver, and ieee80211 stuff?  It's been several weeks since I did mine and so far so good - no more connection drops even over the weekends.

---


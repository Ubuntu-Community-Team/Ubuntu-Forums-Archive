---
title: "Drivers Issue"
date: 2011-04-10
forum: General Help
---

### Post by liro87 on 2011-04-10
Hi all,

I'm new to ubuntu and after being shown by a lot of my fellow IT friends and associates on what it can do, I was eager to try it out and after trying it from a live CD I decided to partition my HD to dual boot Windows 7 and Ubuntu with the Windows bootloader managing OS selection at boot. So far it's been a good experience with the exception of one issue I can't seem to figure out.  Some of you may see this as a Windows issue while others may not, but I find many ubuntu users to be better versed in Ubuntu AND Windows which is why I'm asking my question here.

So basically since using the live cd of ubuntu 10.10 and also since installing it, whenever I would restart or shutdown ubuntu and then log onto Windows, my mouse most of the time would stop working and wouldn't respond at the Windows logon screen as well as my resolution would be changed often to 800x600.  Once in Windows by using the keyboard to navigate around, I went to device manager and receive a code 10 error for the mouse that it either could not be started or the drivers could not be initialized.  For the display adapter, it would usually be code 10 as well but only that the drivers for the device could not be initialized.  

The way I would get everything back to normal is uninstalling the mouse and display adapter through device manager, restarting the machine and booting into windows, and upon restart they would be detected again and the drivers for them would be reinstalled and everything would be working correctly then.

This, as anyone can imagine, can get very annoying when needing to use Windows again after using ubuntu.  Just to give some background information, this is a Dell Latitude D430 laptop and the video adapter is onboard from the Intel 945GM mobile chipset.
The way I have Ubuntu setup is I have Grub 2 installed on the /boot partition and used EasyBCD in Windows to add a boot entry for Ubuntu using the Windows bootloader.  Then I have the obvious root, swap, and home partitions.  Upon installing Ubuntu I didn't have to install any drivers -- it recognized everything since this laptop has mostly generic intel hardware.

Does anyone potentially know why this is or a solution?  Again, this happened even when I was using the live cd and not actually installing ubuntu on it's own partition.  I would just restart the machine after using ubuntu and what I described happens everytime and I have to go through the process of uninstalling the devices and restarting the machine once or twice afterwards.  Thank you in advance for your responses!

---

### Post by tredegar on 2011-04-10
Windows sometimes leaves hardware in a configuration that linux cannot use at the next linux "warm" boot, so devices "disappear". The solution is to _completely_ power down the laptop (remove AC cable, remove battery, press power on button, wait 2sec., re-connect, then boot).

Perhaps linux is learning and now doing the same to windows (joke).

Seriously, try _completely_ powering down your laptop before you boot to windows. I'd be interested to hear if this works for you.

---

### Post by liro87 on 2011-04-10
tredegar, Thank you for your reply!

Just to ensure I understood you correctly, the following is what I did.

1.  Had the drivers for the mouse and display adapter reinstalled and working in Windows.
2.  Shut the machine down normally from Windows (Start>Shutdown).
3.  Started up the machine and booted into Ubuntu 10.10.
4.  Removed the ac adapter and then battery from the system while it was running in Ubuntu thus causing it to shut down?
5.  With the battery and power adapter out, I pressed the power button as well as pressed it once and held it for 5-10 seconds.
6.  Put the battery back in and powered up the laptop and booted into Windows.

Did I follow your steps correctly or was there something I missed?  The steps above are what I did in detail and upon getting to the Windows login screen, the resolution change happens as well as the mouse can not be moved.  Going to device manager then shows me the same errors described in my first post.

---

### Post by tredegar on 2011-04-11
> Removed the ac adapter and then battery from the system while it was running in Ubuntu thus causing it to shut down?
No, that was not a good idea, but the system will probably recover from it.

Just shut down the computer normally in linux, *then* completely power it off, then boot to windows. Set up the things that are broken in windows.

Shutdown windows normally, boot to linux, then shut down normally.
Now completely power it off, then boot to windows again. Is windows working normally this time?

---

### Post by liro87 on 2011-04-11
Tredegar, thank you everything seems to be working now!  I followed most of what you said but tried something a little different:

1.  Booted into Linux first, shut down normally, completely powered it off and then booted into Windows.
2.  Booted and logged into Windows, experienced the issue I always have, went into the device manager and removed the display adapter and mouse, and then reinstalled their drivers via the setup applications which include the drivers.  Then shut down Windows normally.
3.  Booted into Linux and shut down normally.  Then did a complete power off.

Here's where there was kind of an unexpected deviation -- Powered the machine back on and selected Windows 7 from my boot menu and waited for it to boot up.  Heard the Windows 7 music that is normally heard at the log on screen, but I waited and waited and it just stood black (never got to see the log on screen).  I turned the machine off by holding the power button.  Turned it back on and selected Windows, gave me the usual error about how Windows was improperly shut down but I selected 'Start Windows in Normal Mode' anyway.  It started up fine, got to the log on screen AND my resolution wasn't changed and my mouse was working!  

So then I logged into Windows normally and shut it down again normally.  Logged into Ubuntu, shut down normally, then started the machine back up and booted to Windows to ensure the changes stuck from before and they did :)  Not sure why/how it worked, but it did.  

Thank you for all your help tredegar!

---


---
title: "Printer And hplip-3.12.6.run"
date: 2012-07-13
forum: General Help
---

### Post by UltimateCat on 2012-07-13
I'm having trouble understanding what to do here.

I'm running Ubuntu 10.04 / Ultimate Ed 2.7
I purchased the brand new HP Envy d411c printer ; went to their website and downloaded the hplip-3.12.6.run and put it on my desktop.

I right clicked on it's properties and it's a Shell Script Application/x - Shellscript 537.3KB

I opened Synaptic and the first package I saw was:
```
 3.10.2-2 Ubuntu 2.2  Hp Linux Printing And Imaging System

```

Do I tell Synaptic to install the 3.10.2 ?
Or should I just open the terminal and try installing the 3.12.6.run ?

```
 chmod a+x hplip - 3.12.6.run

```

I'm confused-

---

### Post by ajgreeny on 2012-07-13
From what I can find, you will need to use the recent version of hplip that you downloaded, as it looks as if the 3.10.2-2 in Lucid does not work with that printer.  In fact I can not find that printer at the hplip site, but there is an envy d410 listed which may be good enough.

You will therefore need to use the terminal to install the .run file which you can do either by ```
cd Desktop
./hplip-3.12.6.run
``` or just double click on the run file on your desktop and chose Run in terminal, then follow the instructions that appear in terminal.

I think the run file is executable when it's downloaded, but I can't remember.  If it's not then make it so with ```
chmod +x Desktop/hplip-3.12.6.run
```

---

### Post by UltimateCat on 2012-07-13
ajgreeny:

Thank you for writing to me.

Here's the HP site for the printer.  It's a good printer I must say-
[http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?product=5150158&lc=en&cc=us&dlc=en&lang=en&cc=us](http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?product=5150158&lc=en&cc=us&dlc=en&lang=en&cc=us)

I'll follow your instructions and open the terminal and put in the argument
```
 cd Desktop
./hplip-3.12.6.run

```And see what happens.  I'll also double click on the run file and see if it starts.  If not I wrote down the instructions you gave me.

I'll post back with the results either way; thanks

---

### Post by UltimateCat on 2012-07-13
I opened the terminal and typed :
```
cd Desktop
hplip-3.12.6.run
```

The terminal told me:
```
  cat@ztcat:~$ cd Desktop
cat@ztcat:~/Desktop$ sh hplip-3.12.6.run
Creating directory hplip-3.12.6
Verifying archive integrity...Error in MD5 checksums: b24b64a07dd7e32f7ecf2c0c8f45de1a is different from 915e19af4522b70ad2c7846b0fc2396c
cat@ztcat:~/Desktop$ 
 
```
Not sure what this error is and how to fix it
Any advise?

---

### Post by UltimateCat on 2012-07-13
The file was corrupt so I re-downloaded.

The terminal is now telling me :

```
       INSTALLATION NOTES
------------------
Enable the universe/multiverse repositories. Also be sure you are using the Ubuntu "Main" Repositories. See: https://help.ubuntu.com/community/Repositories/Ubuntu for more information.  Disable the CD-ROM/DVD source if you do not have the Ubuntu installation media inserted in the drive.  During the install process you will be added to the lp group, please quit the installer before the setup stage, log out, log back in, and run hp-setup to complete the install.

Please read the installation notes. Press <enter> to continue or 'q' to quit:      
```

How do I know just before the installer setup stage starts?

It's instructing me to log out and log back in and run the hp-setup....I don't log in or out with my Ubuntu 10.04 I shut down or start up my computer tower-

Advise please; I'm not sure what to do at this point......

---

### Post by UltimateCat on 2012-07-14
I shut down and then restarted.  Opened the terminal and typed:
```
hp-setup

```

The HP wizard opened and asked me for my ip address and or network (ssid) name.  I typed both of these that the wizard asked for and clicked next and it's not working. The terminal says:
```
  QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /home/cat/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 
Searching... (bus=net, timeout=5, ttl=4, search=(None) desc=0, method=mdns)
error: Unable to send broadcast DNS packet: [Errno 1] Operation not permitted
|error: Unable to send broadcast DNS packet: [Errno 1] Operation not permitted
|error: Unable to send broadcast DNS packet: [Errno 1] Operation not permitted
error: No devices found on bus: net

```

I'm just so close but don't understand what the problem is-

I don't have a usb cable and the printer didn't come with one-

ANY ideas?:confused:

---

### Post by ajgreeny on 2012-07-14
I am not sure where you have got to from your description, but you need to open up **software-sources** to check that the universe and multiverse repos are enabled then at the screen where the hplip installer tells you to enable them you can just hit enter.

At some point you will need to type your password in order to continue, if you have not already done so at that point, and the hplip installer will just go through the compilation of the driver and install it for you.

Eventually it will ask you to restart the printer (press "r" I think, but can't remember) and then it should all be fine.

Running hp-setup before installing hplip will not work, as I think you have found, because there is no driver to setup at that point.

---

### Post by UltimateCat on 2012-07-14
I went through the Wireless Setup Wizard on my HP Envy printer.  I have a sheet that the printer printed out confirmation of the wireless network working and a grade of very good.
So that step is done and working.

I called HP and they think that my internet service provider may be restricting my printer from communicating with the wireless modem.

When I type 
```
hp-setup

```
In the terminal the Wizard opens and gives me these choices: ( this is where I'm at now)   -Universal Serial bus (usb)....printer did not come with one
                     -Network/Ethernet?Wireless Network (direct connection)
                      ( this is what I have tried)
                      -Wireless / 802.11 ( requires a temporary usb connection and is only available for select devices)  This I have not tried.

I wrote down you instruction so I can follow them but I have to find out what Universe and Multi-verse is.  My ISP may not be open until Monday.

I will try to set up the HP Wizard again and see what happens.
If I have to I will purchase a usb but the documentation that came with the printer strongly advises me not to-

Worse case senario; I'll have return the printer to the merchant for a refund.

At this point I don't know what else to try but I'm not ready to give up yet-
If you can think of anything else please let me know

---

### Post by UltimateCat on 2012-07-15
Problem Solved thank goodness-
When the terminal told me :
```
Can not get ibus-daemon's address

```
I knew something was not communicating properly but didn't know what.
I found a thread to help me go through the IBus Preferences and followed the members instructions.  Shut down and rebooted.

Upon restart the icon for my new HP Envy was on my GNOME desktop.
My wireless printer functioning properly and Ubuntu recognizes it.

I hope that other members don't encounter as much difficulty as I have.
I've spent the last 22 hours troubleshooting to get this new HP up and running.

Ajgreeny:
   Thank You for helping me I appreciate it:D

The HP Representative that I spoke to today explained that they are working on what they can to become Linux savvy for the future.

---


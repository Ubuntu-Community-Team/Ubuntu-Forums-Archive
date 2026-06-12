---
title: "Ubuntu 11.10 - System freezes on restart"
date: 2011-10-15
forum: General Help
---

### Post by osmak on 2011-10-15
Hi, 

I am new to linux and have just installed ubuntu 11.10 today. I had a problem connecting to the internet because I had to learn how to force my ethernet card to run at 10Mb full-duplex (although it is a 1Gb card). Anyways, after I solved the probelm by modifying the /etc/rc.local to include "ethtool -s eth0 autoneg off speed 10 duplex full" the system won't restart it just freezes on the ubuntu purple screen. To complete the restart I need to press the reset button. I tried removing the line from rc.local but nothing changed, the system freezes at restart!!. Any suggestion?

Thanks,

---

### Post by franmac on 2011-10-18
Same problem here, but not reset button so I have to remove the battery and power supply...

Acer Aspire One, dual boot with Windows 7

---

### Post by chipstix on 2011-10-18
I have the exact same problem and like franmac have no restart button so its a hard shut down for me too....im running a dual boot with XP so having a reliable restart would be pretty handy for switching systems...oh and i have tried the following command lines i found on the ubuntu help:
[INDENT]   The wrong driver is loaded which   prevents shutdown. To fix it you need   to do this:
      Open a terminal and type: sudo modprobe -rf rt2860sta
      Followed by: sudo modprobe rt2860sta
      Then you need to blacklist the wrong driver:
  echo blacklist rt2800pci | sudo tee -a /etc/modprobe.d/blacklist.conf
      Once you have rebooted (you will need   to do a hard power off for the last   time!) you will find 

you can reboot   properly.




Didnt work. it gave me a message saying something like - Fatal-  module not found (i didnt do the blacklist bit cos the first part wasnt working)


hmm, maybe franmac and osmak should try the above....


[/INDENT]

---

### Post by flangemonkey on 2011-10-18
does the computer stop loading before you can log in?

press escape to see the text of what the computer is doing and we should get an idea of what's going on.

Also worth trying is choosing recovery mode in your boot menu (you might have to press escape to see the options on boot) and showing us the last few lines of 

```

dmesg 

```

lemme know how you get on :)

---

### Post by flangemonkey on 2011-10-18
also 
[http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=11360765]("http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=11360765")
has the latest steps in the final post on how get past not booting properly :)

> 
by Nekksys 	
Re: 11.10 broken after update from 11.04

This bug is due to a change in the way the running programs and associated lock files are kept. The fix is simple.

******************************* IMPORTANT NOTE *******************************
You will be performing some of these tasks from the command line as the ROOT user!
Do NOT deviate from the commands given as you will TANK your system if done incorrectly
************************************************** **************************************

1.) Go to a command console after booting your machine by pressing CTRL+ALT+F4 - The console at CTRL+ALT+F1 may be busy or unresponsive so use F4 for now.

2.) You will have to log in as ROOT or a SUDO user and DELETE the file "pid" from the /var/run/dbus directory
If you logged in as a SUDO user, run the following command:

sudo -i

And then run:
rm /var/run/dbus/pid

3.) Reboot the system:

shutdown -r now

4.) Log in as usual

******************************* IMPORTANT NOTE *******************************
The following section will take place after you have logged in. Again, follow these instructions exactly
************************************************** **************************************

5.) Open your file manager AS ROOT - This _MUST_ be done as ROOT. No exceptions!!!!

6.) Copy everything inside the /var/run directory into /run - You will get some errors. It's OK. Don't worry. We mainly need the associated stuff and directories that live there. Choose "Skip" or "Autoskip" and move on to step 3.

7.) Copy everything inside the /var/lock directory to /run/lock - Same thing goes here as for step 2 above.

******************************* IMPORTANT NOTE *******************************
FROM HERE ON OUT, you'll want to write these directions down because you will NOT have GUI to help you. Do NOT deviate from the instructions given here or you WILL COMPLETELY TANK YOUR SYSTEM.
************************************************** **************************************

8.) Press CTRL+ALT+F1 and log in as either ROOT or a user with SUDO privileges

9.) If you logged in as a SUDO user, run the following command:

sudo -i

10.) Now that you're root, run the following commands based on your system:

For KDE systems
service kdm stop

For GNOME systems
service gdm stop

For XFCE systems
service xdm stop

If you get an error or no feedback at all, try one of the other system's commands.

11.) Change directories to /var using:

cd /var

12.) DELETE the run directory inside /var

rm -rf run

13.) DELETE the lock directory inside /var

rm -rf lock

14.) Create a symlink to /run using /var/run as the link name

ln -s /run /var/run

15.) Create a symlink to /run/lock using /var/lock as the link name

ln -s /run/lock /var/lock

16.) Reboot the system

shutdown -r now

******************************* IMPORTANT NOTE *******************************
If you have done everything exactly as noted here, you will come back to a properly running system.
************************************************** ************************************** 


---

### Post by chipstix on 2011-10-19
thanks flangemonkey, in answer to your first question - yeah mine freezes before you can log in. it goes to the Ubuntu logo and hangs there....i tried to esc and various force quit hot keys but it appears im locked out as soon as i hit restart (or shutdown, though im sure this was working before).
strangely it seems possible to shutdown from the log in screen but not once you enter the desktop... 
had to go to work so havnt tried your other solutions yet but thanks again.

---

### Post by chipstix on 2011-10-19
ran into problems with above straight way...when i ran the first remove file command it tells me it doesnt exist.....i broke it down and opened each directory in turn but it still denies the exist of /pid. when i ran a list command it showed /pid as present and infact i can find what i assume to be that file through GUI.
any clues to what im doing wrong?

---

### Post by osmak on 2011-10-21
Thanks for the replies guys,

I tried what flang suggested, but similar to chipstix the system is completely locked after I hit restart. I also tried some of the steps in the procedure, but did not continue because  my /var/lock folder is empty so I cannot really copy whats in there to replace the contents of the other lock folder

---

### Post by PikeHill on 2011-10-23
Thanks for the suggestions, but I still face the purple screen of silence.

Any other ideas?

Here are the details:
Last week I updated form Ubuntu 11.04 to 11.10 (64bit)
I had a few conflicts with nVidea & display manager; that user account would default to 'twinview' even after removing the aux screen, and would freeze when the generic display control was opened. After a few restarts and a few lucky nVidea display config changes, that problem cleared.

I received a warning that a few clusters were going bad. They appear to be marked and data transferred to a new location.

Then I woke up to a purple screen yesterday morning. At first, I thought the display problem had migrated to the basic login. That does not seem to be the case. Then I thought another cluster bit the dust - a disk check from USB mounted system does not show any new dead clusters.

So I am back to this thread. Startup freezes at the purple screen. I can get to terminal mode (alt+f4, ctl+alt+f1, and ctl+alt+f4 all work). I ran through the suggestions in this thread, with one small change.
 chipstix idea, modprobe.... Module rt2860sta not found
 flangemonkey repost of Nekksys... Rather than remove 'pid', I moved it to a user folder. Shutdown, restart, and 'pid' is back in /var/run/dbus. Restart as normal does not work. I then removed it from /var/run/dbus. Restart as normal does not work, and pid is back. I can not go beyond step 3.

I'm still looking at the purple screen.

Any other ideas?

---

### Post by ChronoMTB on 2011-10-24
Unfortunately enough, I have a problem that is similar to the one mentioned. The difference is that when I try to reboot Ubuntu my system freezes for somewhat like 10 seconds just when BIOS is supposed to show up and then shuts down automatically. I guess this has something to do with my BIOS. I'm using Acer 1810tz, dual boot with Windows 7. Updated Ubuntu from 11.04 to 11.10, 64 bit. Does anyone have any suggestions on how to deal with that?

---

### Post by chipstix on 2011-10-25
no break through as yet....i like you am still getting purple screened into submission......
tried the suggestions again and found my lock folders to be empty too....

---

### Post by chipstix on 2011-11-21
for those of you experiencing this, try command line

sudo reboot

also i can acheive a full shutdown through the command

sudo init 0

this seems to work. if this gives any clues as to why the regular restart methods are not working i would be glad of any input....

---


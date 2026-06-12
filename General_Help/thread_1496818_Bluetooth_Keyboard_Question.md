---
title: "Bluetooth Keyboard Question?"
date: 2010-05-29
forum: General Help
---

### Post by Teracis on 2010-05-29
Gday all, I'm hoping to find a solution here to the last piece of my puzzle. 

I accidentally posted this in the networking forum, no wonder nobody looked at it there, I must have had the wrong tab open when I created the post, oh well moved to here now!

I am running ubuntu 10.04 64bit in a dual boot with windows 7 and have a bluetooth keyboard and mouse.

I'm having trouble getting my keyboard to stay paired to my system between operating systems, I don't care if it works in bios as I've a usb keyboard hidden for selecting grub entries so it's all good.

The problem I am having is ubuntu sets up the keyboard with a passkey, when I boot into windows 7, windows wants me to pair the keyboard again to get it to work and uses a different passkey. Back to ubuntu and now I have to pair again because windows has changed the passkey

Running Ubuntu 10.04 and Windows 7 using a Razer Orochi mouse and a microsoft bluetooth keyboard 6000.

The mouse connects fine in both operating systems because it requires no passkey. This (and the internet) gave me the idea to connect the keyboard without a passkey.
Easy enough to do in windows, seemingly harder in Ubuntu because I lack the skills.

Windows:


> Right Click the Bluetooth icon, Add device. Make your keyboard discoverable.

When shows up, Right Click, Properties on the keyboard. On the services tab, check the HID service and click OK.

Cancel the pairing wizard.
This is taken directly from a post by Todd Schiele at this link [http://social.technet.microsoft.com/...7-884d2129e84f](http://social.technet.microsoft.com/...7-884d2129e84f)
It works for me. No problems at all.

Ubuntu:
First step was to go here [https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup) and start following the instructions. I did the first part


> Before you begin open up the terminal and type the following:

sudo apt-get install bluez && sudo apt-get install bluez-utils
Which I didn't need to do (did it and it's already there) but you might if you are reading this as a fix.

IMPORTANT: Later in the guide it says to use the hidd command. I could not get this to work until I followed the instructions from the last post here [https://answers.launchpad.net/ubuntu...question/24516](https://answers.launchpad.net/ubuntu...question/24516)


> MushuWeb said on 2008-12-27:

sudo aptitude install bluez-compat
I can then skip down to the SETUP DEVICES section and run the commands there.


> Find Device Addresses

Locate the device address, make the device discoverable (a "Connect" button for keyboards and mice or check the manual) and search for the device by the following:

sudo hidd --search
This connects my keyboard for the session, however the connection will timeout after about 30 minutes of inactivity and will not persist through a reboot (understandably) however this method does not break the connection with windows when I reboot into windows 7. The next section of the guide Connect Devices at Startup requires the editing of /etc/default/bluetooth which no longer exists.

I read that one can create this file with the lines you need and the program will use it, however I cannot get this to work, and when I add the required lines, it stops my mouse from working after a restart (until I delete the file and restart) and the keyboard doesn't work either. Here is the link to the info, the last post by Mevos says to just create the file (/etc/default/bluetooth) with the appropriate lines and the program will use it.
[http://ubuntuforums.org/showthread.php?t=1316959](http://ubuntuforums.org/showthread.php?t=1316959)

I hope I haven't confused anybody, and I'm hoping this will work in a system which still has a /etc/default/bluetooth file but I'm still looking for a solution in lucid.

I have also been looking for /etc/bluetooth/hcid.conf which is also missing in lucid, I think this file may also hold a solution as it allows the same manual connection without passkey and seems to integrate it into startup.

Thanks for any help
Teracis

---

### Post by Teracis on 2010-05-30
IF nobody has any other ideas, maybe someone can point me in the direction of which file has replaced /etc/default/bluetooth or /etc/bluetooth/hcid.conf

If neither of them, maybe someone can point me in the direction of where I would find out more info about these files, or the lucid lynx bluetooth stack in general. I don't seem to be having any luck with google, can't find any manpages for how to use files or anything.

Thanks in advance
Teracis

---

### Post by Teracis on 2010-06-05
Still having no luck with this, I'm down to just manually connecting when I want to use Ubuntu.

I have to set the keyboard to discoverable, open a terminal and run sudo hidd --connect

Which finds and connects the keyboard, Surely there is a way to get Ubuntu to remember this connection for next time?

---

### Post by RJ12 on 2010-06-05
What if you make those commands into a script, and run it at startup?

---

### Post by Teracis on 2010-06-05
If I knew how to make them into a script I probably would, only problem is I would still have to press the connect button on my keyboard and that defeats the purpose of automating the process :D

It would make it easier however It still wouldn't be right so I'll leave the script out of it for now. It would all be solved if they hadn't taken away /etc/default/bluetooth
or /etc/bluetooth/hcid.config

at least thats what the cloud tells me :D

---

### Post by Teracis on 2010-06-28
So I finally decided to learn how to script and scripted this to work. Even better I found one someone had already done and it should work from startup, just got to make the device discoverable.

First make sure you have run sudo apt-get install bluez-compat

Next follow the instructions here: [http://blog.projectnibble.org/2010/01/28/how-to-connect-a-bluetooth-keyboard-in-ubuntu-9-04-jaunty-and-9-10-karmic-workaround/](http://blog.projectnibble.org/2010/01/28/how-to-connect-a-bluetooth-keyboard-in-ubuntu-9-04-jaunty-and-9-10-karmic-workaround/)

This should make a script which will connect to your device using hidd --connect on startup and then keep reconnecting after idle dropouts. Again you will have to make your device discoverable to get it to reconnect.

---

### Post by HeinekenPissr on 2010-10-04
i am having the exact same problem.  I can't believe i haven't been able to find a solution online either.  I can get my apple keyboard to work in both WIN7 and ubuntu 10.04 and it auto connects after i reboot so long as i reboot into the same OS. When i choose the other OS i will have to re-pair the device.  

any help...?

---


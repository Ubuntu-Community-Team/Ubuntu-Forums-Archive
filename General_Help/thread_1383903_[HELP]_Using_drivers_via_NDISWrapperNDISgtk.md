---
title: "[HELP] Using drivers via NDISWrapper/NDISgtk"
date: 2010-01-17
forum: General Help
---

### Post by Xog on 2010-01-17
Hello there. I'm dualbooting XP and Ubuntu. I've probably switched back and forth over 50 times today to download certain files to hopefully get this thing working.

Problem: I use a Linksys Wireless-G Adapter to connect to my wireless router. The cord is too short to reach my PC. Different rooms. Ubuntu will not connect without the correct drivers. I have installed ndiswrapper and the ndisgtk. 

Adapter Model No.: WUSB54GC
ver.: 3.0.02 / 3410-00450

I have successfully installed the following programs without internet:
1) Wine v. 1.1.36
2) ndiswrapper
3) ndisgtk

I have access to the specific driver on the installation CD for the adapter.

Questions:
1)How do I use the NDISwrapper or ndisgtk to use the drivers from the CD?
2)Where do I move the drivers if I have to in order for ubuntu to use them?

Thanks, 
Xog

---

### Post by jamesisin on 2010-01-17
I usually prefer to connect the wired NIC long enough to get the wireless drivers functioning.  It's so much easier.  So hook your box up in the hall if you have to, but that's my suggestion.

---

### Post by Xog on 2010-01-17
too many wires X.X

---

### Post by Xog on 2010-01-17
besides that wouldn't really work anyways lol. i need to use those drivers no matter what and the only way to do that is to answer my questions

something interesting to note though:
my wireless adapter is somewhat functioning. the green light on it doesn't light up but ubuntu is able to see the 3 wireless networks in range.. when I click connect it still wont let me. So i definitely need the drivers to work!

---

### Post by jamesisin on 2010-01-17
Ah, usually I attach the wireless card and when I try to use it Ubu asks me if I want to get the drivers and it manages the rest.

---

### Post by wojox on 2010-01-17
Did you follow everything from here down: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#USB%20Wireless%20Adapter](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#USB%20Wireless%20Adapter)

I used this page around Christmas to hook up my sister's computer. Out of curiosity why did you download Wine?

---

### Post by Xog on 2010-01-17
> **wojox said:**
> Did you follow everything from here down: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#USB%20Wireless%20Adapter](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#USB%20Wireless%20Adapter)

I used this page around Christmas to hook up my sister's computer. Out of curiosity why did you download Wine?

I installed wine first because I wanted to install the software that came with my wireless adapter. I then learned that ubuntu has problems with some drivers so I installed the ndis software.

anyways, here's some more information to dump:

terminals:
ls /home/logan/WindowsDrivers
Result: RaCoInst.dat  RaCoInst.dll  rt2870.inf  rt2870.sys  wusb54gcv3.cat
**(this is where I put the drivers after getting them from the adapter's software CD)**




sudo lshw -C network > network.txt
Result: It runs its course and I go to my home directory and open network.txt. It's blank.




+++

I click on System > Administration > Windows Wireless Drivers
I click 'Install New Driver'
I select the **rt2870.inf** (that's the driver right?) from its directory **(/home/logan/WindowsDrivers)**
Clicked Install
I get an error message: 'Unable to see if hardware is present.'
Clicked OK



I see **rt2870** on the list of currently installed windows drivers in the
Wireless Network Drivers. Below it, it says 'Hardware present: Yes'
I click Configure Network
I get an error message: Could not find a network configuration tool.

---

### Post by jamesisin on 2010-01-17
Your command ( sudo lshw -C network > network.txt ) will only send standard output to that file.  You may want to include standard error as well:

[noparse]sudo lshw -C network >& network.txt[/noparse]

---

### Post by bkratz on 2010-01-17
Both of the messages are normal

I get an error message: 'Unable to see if hardware is present.'
Clicked OK

I see rt2870 on the list of currently installed windows drivers in the
Wireless Network Drivers. Below it, it says 'Hardware present: Yes'
I click Configure Network
I get an error message: Could not find a network configuration tool.


now go to system>>preferences>>network connections
and do your setup there or right click on the network icon, it does the same thing

__________________

---

### Post by Xog on 2010-01-17
> **jamesisin said:**
> Your command ( sudo lshw -C network > network.txt ) will only send standard output to that file.  You may want to include standard error as well:

[noparse]sudo lshw -C network >& network.txt[/noparse]

Still blank


Also, i can no longer see available networks. Wireless internet isnt an option anymore

---

### Post by Xog on 2010-01-17
Bump

---

### Post by bkratz on 2010-01-17
When you did the sudo lshw -C network did you see results on the screen? The command you originally did should have written the output to the file you specified since you were redirecting the standard output (the terminal) to the file. That is why I am curious if you actually see anything. If you do you can simply copy/paste the output here using the # (code tags) for ease of visualization. Copy/paste is available by highlighting and right clicking.

---

### Post by Xog on 2010-01-17
> **bkratz said:**
> When you did the sudo lshw -C network did you see results on the screen? The command you originally did should have written the output to the file you specified since you were redirecting the standard output (the terminal) to the file. That is why I am curious if you actually see anything. If you do you can simply copy/paste the output here using the # (code tags) for ease of visualization. Copy/paste is available by highlighting and right clicking.

When i execute the command, the terminal says 
CPUID
then it disappears and is replaced with
PCI (sysfs)

nothing shows up in the txt file

---

### Post by Xog on 2010-01-17
[[IMG]http://img96.imageshack.us/img96/6183/screenshotbk.th.png[/IMG]](http://img96.imageshack.us/i/screenshotbk.png/)

i also did the command with the & symbol after the >

the CPUID and PCI(sysfs) doesn't show up but the txt file is still blank (closing and opening multiple times to make sure it's refreshed)

---

### Post by bkratz on 2010-01-17
> **Xog said:**
> When i execute the command, the terminal says 
CPUID
then it disappears and is replaced with
PCI (sysfs)

nothing shows up in the txt file

That is what i see when i do it for about 1/2 second then the screen continues with all the network stuff.  I am afraid this is really probably way beyond my ability. Look at this thread about using the native drivers and consider re-installation or at least post a new thread in the wireless and networking section because frankly I don't know what to do next.

[http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336) 

here is the original instructions for the card.
[http://ubuntuforums.org/showthread.php?t=1155941&highlight=WUSB54GC](http://ubuntuforums.org/showthread.php?t=1155941&highlight=WUSB54GC)

---

### Post by bkratz on 2010-01-17
So when you were looking at the screen you were still redirecting the output to the text file? That would explain why you don't see it on the screen.
Just do the 

sudo lshw -C network

and copy/paste the output back here

---

### Post by bkratz on 2010-01-17
> **bkratz said:**
> So when you were looking at the screen you were still redirecting the output to the text file? That would explain why you don't see it on the screen.
Just do the 

sudo lshw -C network

and copy/paste the output back here



By the way I just copy/pasted the exact command you originally used from you earlier post in the terminal and got the redirected .txt file in my home folder (with data). So you were doing it correctly. I still don't know why yours is empty.

---

### Post by Xog on 2010-01-17
Same thing happens with sudo lshw -C network, nothing different.

Also im getting errors with the 26 step instructions u linked to ([http://ubuntuforums.org/showthread.php?t=960642](http://ubuntuforums.org/showthread.php?t=960642)), at sudo make

honestly im very upset right now ive done so much. Ive been trying to fix this since 12:30 pm and its almost 12am im exhausted

---

### Post by jamesisin on 2010-01-18
Have a small glass of port and think about tomorrow?

---

### Post by Xog on 2010-01-18
> **jamesisin said:**
> Have a small glass of port and think about tomorrow?

sounds like a plan.. but first.. i reinstalled ubuntu because in the 10+ various different ways i've tried solving this, I probably messed up a file somewhere.

Here's some screenshots from when I was booted in to ubuntu. saved them on my windows partition. you'll notice i have firefox open but I saved the webpage to my windows partition too so i could read it..

[http://img63.imageshack.us/img63/2562/onevg.png](http://img63.imageshack.us/img63/2562/onevg.png)
[http://img707.imageshack.us/img707/6840/twot.png](http://img707.imageshack.us/img707/6840/twot.png)

---

### Post by Xog on 2010-01-18
This is driving me absolutely batty!

I've decided to use this updated guide:
[http://ubunturt2870.pbworks.com/FrontPage](http://ubunturt2870.pbworks.com/FrontPage)

I get up to
7. If you are using Karmic koala you need to blacklist the new kernel driver as it doesn't work so good for the moment

sudo echo blacklist rt2800usb > /etc/modprobe.d/blacklist.conf

I get a Permission denied. I'm using sudo. I cannot edit the blacklist.conf file. I manually went to the folder and opened it to edit. But alas, the Save option is greyed out. Can someone help me? I think this is promising!

---

### Post by jamesisin on 2010-01-18
Boot into the live CD, drill down, and change the file.

---


---
title: "I know it's not the OS's fault!"
date: 2010-02-19
forum: General Help
---

### Post by joecichocki on 2010-02-19
About six weeks ago after getting my computers infected with viruses and being run around by Windows XP, I wiped out everything and installed Ubuntu 9.10 on my Dell desktop with Pentium 4 2.4GHz, 500 MHz ram, and on my Presario Laptop with 1.6GHz AMD processor and 2GHz ram. I love the OS and will never go back to Microsoft. Never. However, I am having a problem doing a couple of things: I cannot load any of my photo files onto my flash drive. Both computers keep telling me that files are read only. When I open up the window to change the properties of the files and folders to read-write, I click the button, and then when I hit the other button to globalize the changes throughout the folder, everything changes back to read only while I am watching. I am the system administrator and I sign in as such.

The other issue I am having is slowness with my Dell desktop (The Presario laptop is just wonderful). Saving photos off the net sometimes takes up to 30 seconds from the time I click the save as button until the download is complete. At other times, the monitor dims, like the electricity in the house is browning out - for 15 - 30 seconds - and then comes back up again. I have tried coping with this by just rebooting and sometimes that helps. Is there anything else I can do - or is this an issue with my 500 MHZ of memory not being enough? I've read that the type of ram this computer contains is expensive and heats up a lot, so I am not in the market for new ram. I know it's not DRAM or the other common one (??) but is relatively rare. 

Basically it is a pain in the butt, hitting a button and waiting. The cursor even moves all herky-jerky, and if I try to close a window, I wait up to 15 seconds until it takes effect. I know - it's not a lot of time, but if you are in the middle of doing something, the slowdown is just excruciating.

Can anyone throw a bone of advice my way? I would appreciate it.

---

### Post by 23dornot23d on 2010-02-19
Are you running Compiz .... by any chance ... ?

the darkening of the screen only seems to occur with compiz on .... on mine .....

could try to turn it off for faster results ..... 

as regards downloads ..... what size are the pictures you are downloading ..... 800 x 600 

or bigger sizes above this can be big ....... 1600 x 1200 ...... especially if ..... png   or bmp files

so may take a little time to download .....

ok hope this helps a little ......

---

### Post by Primefalcon on 2010-02-19
Go to your desktop and right click and select create launcher in the name type Nautilus-Admin (or whatever you want, its the name that will show)

in the command box type gksudo nautilus and then hit ok

In ubuntu to exercise admin powers you need to use either sudo or gksudo, and the launcher we just created will launch a nautilus file browser with admin privileges, be very careful when using this as you can modify any file on your computer, even ones you shouldn't be touching, another words only use this launcher when you have to...

Anyhow use that to browse to where your files are, and then change the permissions using this

---

### Post by audiomick on 2010-02-19
For the permissions, try starting the file manager from a terminal using
```
gksu nautilus
```
this will give you an instance of nautilus with root privileges, and should allow you to change the permissions as you want. Be careful with this; it also allows you to delete system files and break your system.

As far as the "brown outs" go, yes I think that is probably due to the relatively small RAM. I get it occasionally on mine when I give it something chunky to do, and I have 4GB of RAM. If you can increase your RAM, then do so. 512MB is pretty much the minimum for Ubuntu 9.10. Turning off the desktop effects, if they are on, may help.

---

### Post by GolemXIV on 2010-02-19
You might need a proprietary linux driver for the graphics card in your desktop. 
I'd run hardware drivers (it's in the menu somewhere) to see if it can find the 
proprietary drives and install them. Hopefully it will fix your problem if not more 
information about what graphics card you have in the desktop might be helpful.

---

### Post by Primefalcon on 2010-02-19
Actually you'd probably benefit from using a lighter windows manager, such as LXDE.

to installa systemw ith LXDE, simply use the alternate download disc to install a base (command only system) and then boot and enter the command 

```
sudo apt-get install lxde
```

this will install a very light windows manager which should see the end of your ram shortages

---

### Post by Primefalcon on 2010-02-19
also try going to system->preferences->appearance

and then clicking on the visual effects tab and changing the effects to none, then will lower ram usage

[COLOR="Red"]**I WOULD ADVISE TRYING THIS FIRST**[/COLOR]

---

### Post by audiomick on 2010-02-19
> **GolemXIV said:**
> You might need a proprietary linux driver for the graphics card in your desktop. 
I'd run hardware drivers (it's in the menu somewhere) to see if it can find the 
proprietary drives and install them. Hopefully it will fix your problem if not more 
information about what graphics card you have in the desktop might be helpful.
May be an issue.
the utility is at
system> administration> hardware drivers
However I have my nVidia driver enabled ( and I know for sure that it is working) and still get the occasional "brown out".

---

### Post by joecichocki on 2010-02-19
I tried this one and it still willnot let me change anything.

---

### Post by neoanderthal on 2010-02-19
Did you format the flash drive under Ubuntu? It sounds like the drive is being mounted read-only, or that the filesystem is read-only.

---


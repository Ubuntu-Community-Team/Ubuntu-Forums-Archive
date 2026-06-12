---
title: "Help me with internet"
date: 2011-05-12
forum: General Help
---

### Post by Wozza365 on 2011-05-12
Ok so recently ive tried to install the driver for my network piece and it doenst wanna <snip> work and it is really <snip>, ever since i installed 11.04 all ive had is problem this problem that 'to download the network driver you must connect to the internet' <- seriously <snip>

god help me i click on the program file for my network driver install and it just comes up with some box with a browse button thing 

just <snip> work, before i uninstall it!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

Edited for language by The Cog

---

### Post by hackb0y294 on 2011-05-12
I understand how you feel, but be patient and you'll get it working.

It sounds to me that you downloaded a Windows driver file, which won't install under Linux. See if you can find your driver here [http://www.linux-drivers.org/network.html](http://www.linux-drivers.org/network.html)

---

### Post by Wozza365 on 2011-05-12
no i downloaded the linux one from intellinuxwireless.org

---

### Post by akand074 on 2011-05-12
> **Wozza365 said:**
> to download the network driver you must connect to the internet' <- seriously wtf

Plug in a ethernet cable and install it from the additional drivers. Otherwise download it from another computer and bring it over via usb and install it. You'd have to do the same in Windows... how can you download something without an internet connection?

---

### Post by hackb0y294 on 2011-05-12
> *it just comes up with some box with a browse button thing*Can you attach a screenshot of it?

---

### Post by Wozza365 on 2011-05-12
i already downloaded it via my laptop (which im using it now, and transferred by USB stick

and im assuming print screen is the same button but how do you save it as a file?

---

### Post by akand074 on 2011-05-12
> **Wozza365 said:**
> i already downloaded it via my laptop (which im using it now, and transferred by USB stick

and im assuming print screen is the same button but how do you save it as a file?

The print screen button should open up a dialog where you can press save to save it as a file. You can also press Alt+PrtScn to take a snapshot just of the current window.

---

### Post by Wozza365 on 2011-05-12
ok you will need to give me a while cos im gonna but some arrows and <snip> to help

really appreciate it btw and ive calmed down a bit now, was jsut getting really pissed off sorry

---

### Post by astex on 2011-05-12
could you copy and paste the output of:

```
$ lspci
```

?

---

### Post by hackb0y294 on 2011-05-12
> **Wozza365 said:**
> ok you will need to give me a while cos im gonna but some arrows and sh*t to help

really appreciate it btw and ive calmed down a bit now, was jsut getting really pissed off sorry

No problem, that's what we're here for.

---

### Post by hackb0y294 on 2011-05-12
> **astex said:**
> could you copy and paste the output of:

```
$ lspci
```?

To use that code, you must open a Terminal window (Applications > Accessories > Terminal) and type

```
lspci
```

---

### Post by Wozza365 on 2011-05-12
here is the image with the driver file on my pendrive and what appears when i click open with

---

### Post by Wozza365 on 2011-05-12
will get you that code moved over asap

*do you want it in MS format (doc) or linux format

---

### Post by hackb0y294 on 2011-05-12
Have you read this: [http://intellinuxwireless.org/tar.php?p=iwlwifi&f=README.iwlwifi-3945-ucode&a=iwlwifi-3945-ucode-15.32.2.9.tgz](http://intellinuxwireless.org/tar.php?p=iwlwifi&f=README.iwlwifi-3945-ucode&a=iwlwifi-3945-ucode-15.32.2.9.tgz)

---

### Post by Wozza365 on 2011-05-12
here is a doc file of the results from terminal, dw im not a complete noob and came to terms with the terminal feature quickly after being told to type various things

PS on the read me file it says something about changing a kernel setting

**and yes ive read that, it came with it, but i need to change a kernel setting and ive searched on ubuntu itself and on the internet and nothing came up, ive also tried Yahoo answers but obviously most people just about know what AV to use let alone download and install linux

---

### Post by hackb0y294 on 2011-05-12
I also found this: [http://ipw3945.sourceforge.net/](http://ipw3945.sourceforge.net/) which seems to be more detailed.

---

### Post by hackb0y294 on 2011-05-12
> **Wozza365 said:**
> here is a doc file of the results from terminal, dw im not a complete noob and came to terms with the terminal feature quickly after being told to type various things

PS on the read me file it says something about changing a kernel setting

**and yes ive read that, it came with it, but i need to change a kernel setting and ive searched on ubuntu itself and on the internet and nothing came up, ive also tried Yahoo answers but obviously most people just about know what AV to use let alone download and install linux

From that output it would appear Ubuntu recognizes the adapter.

What problem exactly do you have?

---

### Post by Wozza365 on 2011-05-12
i found that site before although didnt really think much of it im currently downloading the files it says are required will put them on the memory stick in a sec

---

### Post by Wozza365 on 2011-05-12
the problem is that i cannot connect at all it says that the hardware switch is somehow turned off although my sister claims it worked fine the last time she used it on windows

---

### Post by Wozza365 on 2011-05-12
so just whilst all the tgz files are extracting, what sort of software can i find on the download centre anything good and what would you recommend.. if i ever get there

---

### Post by Wozza365 on 2011-05-12
im guessing the real thing i need to know is how you actually open a ucode file... =/

---

### Post by hackb0y294 on 2011-05-12
> **Wozza365 said:**
> so just whilst all the tgz files are extracting, what sort of software can i find on the download centre anything good and what would you recommend.. if i ever get there

GIMP is a very full-featured photo editor, which may already be installed. There are several IM and E-mail clients; just try a few and choose your favorite. Games abound as well, from the silly to the RPG and FPS types, try a few of those out as well if you're interested.

---

### Post by hackb0y294 on 2011-05-12
> **Wozza365 said:**
> the problem is that i cannot connect at all it says that the hardware switch is somehow turned off although my sister claims it worked fine the last time she used it on windows

Can you post a screenshot of that error as well?

---

### Post by Wozza365 on 2011-05-12
i will put up a screenshot once ive tried all this, its up on th etop bar when you select the network bit and the 4th option is locked and says 'wireless is disabled by hardware switch'

im having fun trying to switch on the light bulb on the mouse options with lowest double click timeout, i now see why you guys got this instead of Windows, MS would never think of this xD

---

### Post by Wozza365 on 2011-05-12
so how exactly can i get ucode files to work

---

### Post by hackb0y294 on 2011-05-12
> **Wozza365 said:**
> so how exactly can i get ucode files to work

I've never tried it myself, but on that second link I provided, there was a very detailed tutorial.

By the way, a "ucode" file is just regular unicode.

---

### Post by akand074 on 2011-05-12
> **Wozza365 said:**
> so how exactly can i get ucode files to work

extract the entire folder and read the README it should tell you how to install it. Usually it should be something like this:

```
cd /<extracted folder>
```using cd then the folder location puts you in that folder. Then:

```
make
```then 

```
make install
```In the terminal of course. If that doesn't work, check the readme it should tell you how to do it. Also most laptops have a button/switch to turn on/off wifi. Make sure that's on (not showing red).

BTW: You might have to move the file after doing that to the correct place so it loads with the kernel. This should all be in the readme file.

EDIT: Found a nice [link]("http://kuscsik.blogspot.com/2007/06/how-to-install-intel-4965-wireless.html") that might be useful.

---

### Post by Wozza365 on 2011-05-12
how do you become 'root'

---

### Post by akand074 on 2011-05-12
> **Wozza365 said:**
> how do you become 'root'

just use "sudo" before any command to run the command as root

---

### Post by Wozza365 on 2011-05-12
where you posted cd /extracted folder, please explain i either get syntax error or no such file directory, despite extracting it, am i supposed to be linking it to the folder the file it is in or the file

GRRRH is it me or does nothing work when i try to do it, whenever i install anything i always get a problem of some sort

---

### Post by akand074 on 2011-05-12
> **Wozza365 said:**
> where you posted cd /extracted folder, please explain i either get syntax error or no such file directory, despite extracting it, am i supposed to be linking it to the folder the file it is in or the file

GRRRH is it me or does nothing work when i try to do it, whenever i install anything i always get a problem of some sort

what I meant is change "/extracted folder" to the destination where you extracted it. For example 

```
cd /home/wozza365/iwlwifi-3945-ucode-15.32.2.9
```

if your ubuntu username is wozza365 and you extracted it in your home folder. Did you read the readme file? Did it give you any useful information?

---

### Post by Wozza365 on 2011-05-12
sorry i didnt reply earlier i thought you had blanked me until i realised it started a new page

---

### Post by Wozza365 on 2011-05-12
i finally managed to get to the directory properly YIPPEE but then when i type make it comes up with this
make: *** no targets specified and no makefile found. stop

tried with sudo and did the same just asked for a password as well

---

### Post by Wozza365 on 2011-05-12
in this case the laptop does not have a switch that i can find and tbh, i have 6 laptops in my room (most currently broken and i believe only 1 maybe 2 have internet switches on them

---

### Post by Wozza365 on 2011-05-12
im about to go any minute now so if you are gonna reply be pretty quick before i turn off the computer for the night

---

### Post by akand074 on 2011-05-12
Sorry I wasn't at the computer. Okay I think you went the difficult way. What is your wireless card? Which driver were you installing. There is probably a .deb file for it. When you're back post relevent info about your wireless card and post the link where you got your drivers and we'll go from there.

---

### Post by Wozza365 on 2011-05-13
umm its an Intel Corporation PRO/Wireless 3945 ABG

and i downloaded the tgz. file from intellinuxwireless.org which is the official site for the drivers, it had no sign of a deb. file just that

---

### Post by Wozza365 on 2011-05-13
do you have a link to kernel 2.6.24 or above? they all have my driver merged into them

---

### Post by akand074 on 2011-05-13
> **Wozza365 said:**
> do you have a link to kernel 2.6.24 or above? they all have my driver merged into them

It's 3am here I have to get to bed but check out these links:

[http://www.aircrack-ng.org/doku.php?id=iwl3945&DokuWiki=b9d627daa019b07d281a4d981341a3f0](http://www.aircrack-ng.org/doku.php?id=iwl3945&DokuWiki=b9d627daa019b07d281a4d981341a3f0)
[http://forum.aircrack-ng.org/index.php?topic=2898.0](http://forum.aircrack-ng.org/index.php?topic=2898.0)

I think this looks promising for your driver:

[http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2011-05-11.tar.bz2](http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2011-05-11.tar.bz2)

Download that and you should be able to cd to that folder and do:

```
sudo apt-get install linux-headers
sudo apt-get install build-essential
sudo make
sudo make install
sudo make load
sudo modprobe -r ipw3945
sudo modprobe ipw3945
```

Or something along those lines I notice people were having issues... I have to get to bed. Good luck! I think it would be much easier to just plug into a wired internet connection and let Ubuntu automatically install/setup the drivers for you.

---

### Post by Wozza365 on 2011-05-13
hey so i plugged it in to the router and all is good like this but obviously cant leave it like this forever and need to know how to download the driver

ive just started to download some games and apps and one has frozen at halfway and says applying changes... does it always take this long or have i bugged it i dont wanna restart i got like 40 others in the queue


infact it seems like i am unable for anything to apply changes any reason for this???

---

### Post by akand074 on 2011-05-13
> **Wozza365 said:**
> hey so i plugged it in to the router and all is good like this but obviously cant leave it like this forever and need to know how to download the driver

ive just started to download some games and apps and one has frozen at halfway and says applying changes... does it always take this long or have i bugged it i dont wanna restart i got like 40 others in the queue


infact it seems like i am unable for anything to apply changes any reason for this???

To install your wireless driver you should just have to search "Additional Drivers" from the dash. Or click the power button and choose "Additional Drivers" under the hardware section. It should open up a display showing available drivers. Hopefully it should show you your wireless card driver. Just select to install it and it'll take care of the rest.

About installing apps, in software centre go to Edit > Software sources, Under "Download from" choose "other" and click select best server. It'll then check every server for the strongest one for you. Then choose that server, things should start running faster. It might also be a bug with installing too many things at a time. If the problem persists after selecting best server perhaps try installing less at a time? Though I doubt that should be an issue.

---

### Post by Wozza365 on 2011-05-13
hi so im gonna try that tomorrow morning (its past 9pm here in UK) and hopefully it works, the games ended up downloading but not really working, i didnt realise that laptop had such a sh*te graphics card, hopefully i can properly install it when i get a PC, despite it not being til xmas, i cant wait

ill also be getting windows so hopefully the side by side install works properly unlike what this one seems to be (i think ive lost my sisters files :/)

---

### Post by akand074 on 2011-05-13
> **Wozza365 said:**
> hi so im gonna try that tomorrow morning (its past 9pm here in UK) and hopefully it works, the games ended up downloading but not really working, i didnt realise that laptop had such a sh*te graphics card, hopefully i can properly install it when i get a PC, despite it not being til xmas, i cant wait

ill also be getting windows so hopefully the side by side install works properly unlike what this one seems to be (i think ive lost my sisters files :/)

Alright. Yeah you should always make a backup regardless. Easiest way after that is just to let the Ubuntu installer set up Ubuntu side by side with Windows. Otherwise you can search up how to manually partition if required (it's really easy).

---

### Post by Wozza365 on 2011-05-13
the problem i had with installing it side by side is that the first time i tried it didnt work due to dodgy disk and left it half installed, i then had to do it again and chose rewrite over linux or something like that, but i looked at the hard drive and only 20gb had been used although i also didnt think that it was possible for linux to take up 20gb space, and there is no boot option to choose windows or linux, just loads linux automatically

---

### Post by Wozza365 on 2011-05-13
is there anyway you can message privately on this forum so i can send you msn/skype so we can talk easier

---

### Post by akand074 on 2011-05-14
> **Wozza365 said:**
> is there anyway you can message privately on this forum so i can send you msn/skype so we can talk easier

You can PM me but I don't know when I'll be free. Your best best is to ask your questions through the forum or join an Ubuntu [irc channel]("http://www.ubuntu.com/support/community/chat") to get direct chat support.

---

### Post by Wozza365 on 2011-05-14
ok then, i think im gonna give up and just stick with the games/apps i have (if they decide to work at a decent speed) and give up on the internet, i also need to find out how to recover my sisters files if they have been deleted or how to get back to Windows Vista :0 i heard that a menu should appear on startup but nothing appears

---


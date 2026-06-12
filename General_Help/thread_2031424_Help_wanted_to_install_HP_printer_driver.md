---
title: "Help wanted to install HP printer driver"
date: 2012-07-22
forum: General Help
---

### Post by UltimateCat on 2012-07-22
:)Hi

I went to [www.psychocats.net/ubuntu](www.psychocats.net/ubuntu) for help.

Normally I would use the terminal but in this case; installing as root in not advised by HP.

Are there instructions I can follow to install a package (.run) using the Ubuntu Software Center?

---

### Post by 3Miro on 2012-07-22
The Software Center handles only packages, that is .deb files that have been downloaded either manually or automatically.

What is it that you want to install? A .run file should be a last resort for installing anything, since it cannot be handled via the Software Center and would require manual upkeep.

---

### Post by oscarivera9 on 2012-07-22
What are you trying to install?
Usually installing from a terminal (as root) is the best option.
Also, by HP do you mean Hewlett Packard?


To better help you, we need more information
Help us help you

---

### Post by UltimateCat on 2012-07-22
I am trying to install the hplip-3.12.6.run from this website as it ( seems ) is my only option to assist my printer.

[http://hplipopensource.com](http://hplipopensource.com)
It's the HP Envy d411c and the website is:
[http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?product=5150158&lc=en&cc=us&dlc=en&lang=en&cc=us](http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?product=5150158&lc=en&cc=us&dlc=en&lang=en&cc=us)

Long story short; I installed it using the terminal last week and the printer worked.  I had difficult questions that the terminal prompted me for along the way (ibus daemon's address) but it installed.  However when I moved the installer/folder off of my Desktop the printer stopped working in Ubuntu all together.

If it (.run) requires continued up keep then I will have to learn how to do that as well.

I could be wrong but since the printer stopped working altogether I thought it wise to un-install.  The un-install is complete-
I used ```
sudo rm -rf /user/share/hplip

```If there is another way that is best how can I install this for my printer?
...Please advise

---

### Post by 3Miro on 2012-07-22
1. Uninstall the driver.
2. From the Unity menu find Printing.
3. Select Add Printer and follow the Next->Next->Finish steps. This will vary depending on whether you have the printer as a USB or Wireless.

I have a wireless HP printer, this is what I did and it works perfectly. The HP driver is inside the Ubuntu Software Center and it should be installed automatically when you need it.

If the above fails, then you should install the HP driver manually, but from the Software Center again. The .run file is the last resort, should  be used only when all else fails.

---

### Post by UltimateCat on 2012-07-22
I uninstalled so that's done.
I don't have Unity.  I'm running 10.04 Lucid Lynx with Ultimate Ed but I do have Sys>Admin>Printing

My HP Envy is wireless and I have set all of that up.

As far as the driver goes; I ( think ) it's inside of that .run folder and do not know how to get it out to be able to manually install.  But I'm learning. Also; there is a hp driver in my Synaptic but it is 3.10.?

The new one is 3.12.6 
I'll follow as you have advised to the best of my abilities and will only resort to the terminal if all else fails.

---

### Post by codingman on 2012-07-22
> **UltimateCat said:**
> :)Hi
Normally I would use the terminal but in this case; installing as root in not advised by HP.

HP has nothing to with Linux, they cannot say to not install as root as Hewlett-Packard only makes hardware, install as root, it will not impact anything.

---

### Post by 3Miro on 2012-07-22
Ubuntu 11.10 and 12.04 just found the driver as soon as I pointed to the printer on the network. You can install the one from Synaptic manually and then use the System-> Admin->Printing to set your printer.

Does your printer require driver 3.12, if the printer can run with 3.10, then just use 3.10.

If you do require driver 3.12, you can search for an unofficial ppa that is still way easier then the .run file:

[http://ubuntu-tweak.com/source/hplip-isv-ppa/](http://ubuntu-tweak.com/source/hplip-isv-ppa/)

The unofficial ppa will add the newest driver to your Software Center.

---

### Post by 3Miro on 2012-07-22
> **codingman said:**
> HP has nothing to with Linux, they cannot say to not install as root as Hewlett-Packard only makes hardware, install as root, it will not impact anything.

I don't understand what you mean! HP makes the hplip driver, which is software and integrates into the Ubuntu system. I don't think hplip goes into the kernel as a module, but it certainly interacts with cups.

---

### Post by UltimateCat on 2012-07-22
> **codingman said:**
> HP has nothing to with Linux, they cannot say to not install as root as Hewlett-Packard only makes hardware, install as root, it will not impact anything.

Codingman:
  I needed confirmation to go ahead and install as root-
 ....Thank You
I was really starting to get to my wits end with this install

---

### Post by UltimateCat on 2012-07-22
> **3Miro said:**
> Ubuntu 11.10 and 12.04 just found the driver as soon as I pointed to the printer on the network. You can install the one from Synaptic manually and then use the System-> Admin->Printing to set your printer.

Does your printer require driver 3.12, if the printer can run with 3.10, then just use 3.10.

If you do require driver 3.12, you can search for an unofficial ppa that is still way easier then the .run file:

[http://ubuntu-tweak.com/source/hplip-isv-ppa/](http://ubuntu-tweak.com/source/hplip-isv-ppa/)

The unofficial ppa will add the newest driver to your Software Center.
I have not installed yet but when I went to:
System>Admin> Printing.....I found that my Envy was already established and connected to local host.
The HP Envy is so new ( told by the merchant) that it would need the newest driver.
I was not aware that I could find a ppa to assist this install.  However I have zero experience with working with repositories much less ppa's.
I've learned today and appreciate all that you've taught me....Thank You very much:popcorn:

---

### Post by UltimateCat on 2012-07-22
I'm off to learn more about ppa's what they are; how to use and or manipulate them....etc. 
I went to this site:
[http://ubuntu-tweak.com/source/hplip-isv-ppa/](http://ubuntu-tweak.com/source/hplip-isv-ppa/)
Didn't even know it existed.  Looks like I can profit from it; Thanks again

---

### Post by 3Miro on 2012-07-22
Ubuntu software is split into packages that come as .deb files.

ppa is an on-line repository with .deb files. When you install Ubuntu, the Software Center and Synaptic are automatically connected to the official Canonical repository.

You can also connect to custom unofficial ppa. Many people use such ppa to use newer software on older versions of Ubuntu. To add a new ppa, you can either use Synaptic Package Manager (manage software sources) or use the software courses program (sys->admin I think). Alternatively, you can just run the following command:
```
sudo add-apt-repository ppa:hplip-isv/ppa
```

Software that comes in .run or .tar files, can still be installed and used, but it will not register with the rest of the system and usually will have to be manually updated. The .run or .tar files are usually not tuned to specific Linux distributions and additional settings may be required. Use those as a last resort.

---

### Post by UltimateCat on 2012-07-22
> **3Miro said:**
> Ubuntu software is split into packages that come as .deb files.

ppa is an on-line repository with .deb files. When you install Ubuntu, the Software Center and Synaptic are automatically connected to the official Canonical repository.

You can also connect to custom unofficial ppa. Many people use such ppa to use newer software on older versions of Ubuntu. To add a new ppa, you can either use Synaptic Package Manager (manage software sources) or use the software courses program (sys->admin I think). Alternatively, you can just run the following command:
```
sudo add-apt-repository ppa:hplip-isv/ppa
```Software that comes in .run or .tar files, can still be installed and used, but it will not register with the rest of the system and usually will have to be manually updated. The .run or .tar files are usually not tuned to specific Linux distributions and additional settings may be required. Use those as a last resort.

So if I open the terminal and execute the command you advised me-
```
sudo add-apt-repository ppa:hplip-isv/ppa

```
It will automatically be in my Synaptic Package Mgr?
And from there all I have to do is mark the package for installation?

I appreciate your patience....this is new to me.
I'm not good with Synaptic- I'm much better with command line/use of the terminal.  Learning from you I see that manually having to maintain could get interesting to say the least.

---

### Post by UltimateCat on 2012-07-22
Executed the command as you advised-

```
cat@ztcat:~$ sudo add-apt-repository ppa:hplip-isv/ppa
[sudo] password for cat: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 6786BBBBAA1BD96ABA5CD549D5DD920D57840E95
gpg: requesting key 57840E95 from hkp server keyserver.ubuntu.com
gpg: key 57840E95: public key "Launchpad PPA for HPLIP" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)

```
I then opened up Synaptic and saw hplip-3.10.2 but didn't see the new 3.12.6 but maybe the new printer will still work with 3.10.2?
Not sure here what the next step I should perform here-
Please advise-

---

### Post by UltimateCat on 2012-07-23
I used Synaptic Package Manager to upgrade the driver for the hplip.
I went into Printing and checked on everything.
I'm getting a error message:

```
usr/lib/cups/backend/hpfailed

```

When I used Synaptic I noticed that it also installed other packages to accommodate the hplip. The program even told me the chosen action also affects other packages; changes are required in order to proceed. So; I told Synaptic to mark addition required pkgs and install as well.

After Synaptic was done I shut down and rebooted.....my printer still won't print-
I don't know what the deal is but I'm at my wits end as this troubleshooting has gone on now for a week.  I appreciate the help that I've been giving but very disappointed with a $259.00 printer that won't function-:(

---

### Post by nothingspecial on 2012-07-23
Thread title changed to reflect the problem.

---

### Post by oscarivera9 on 2012-07-23
About half a year ago I was having trouble scanning documents and so I looked into installing hplip to get my printer/scanner to scan.  So basically I had to switch from using CUPS to using hplip.   I'm trying to remember exactly how I finally got it to work, but I can't seem to remember what the trick was.  I do remember that part of the  problem had something to do with having the wrong setting with the server that hplip had to connect to.
However, while I was retracing my steps in order to help you, I found this web page that might help you:

[https://help.ubuntu.com/community/HpAllInOne](https://help.ubuntu.com/community/HpAllInOne)
Make sure to read everything, especially the section all the way down that says 
**Setting up printers to use HPLIP**



Also, if it helps any, I do remember that eventually, when I upgraded to Ubuntu 12.04, CUPS was installed automatically and I didn't have to use hplip any more.


If I can think of anything else I'll let you know.

---

### Post by 3Miro on 2012-07-23
Do you see the printer? If you install the hplip driver and use the Printer tool to add a new network printer, do you see the printer.

If not, go to the web-browser and type in the URL bar:
```
127.0.0.1:631
```

You can add a printer from there.

---

### Post by UltimateCat on 2012-07-24
> **3Miro said:**
> Do you see the printer? If you install the hplip driver and use the Printer tool to add a new network printer, do you see the printer.

If not, go to the web-browser and type in the URL bar:
```
127.0.0.1:631
```You can add a printer from there.
Yes, I see the printer but it not printing.

The icon for the printer shows and tells me it's printing....but doesn't-

I'm getting these 2 error messages; one from the HP icon and the other from the Ubuntu icon-
```
Device Communication Error 5012

```
And the Ubuntu icon:
```
usr/lib/cups/backend/hpfailed

```
I read about 20 article's on Google about this Error 5012; haven't found a solution yet.  So; I followed the path of the usr/lib/cups.....etc. and looked into this hp file. 
It's a 36.5 KB executable and the permissions are:
-Owner root
-Group root
The file says at the bottom of the window" You are not the owner so you can not change these permissions"

I ran sudo add-apt-repository ppa:hplip-isv/ppa like you told me to. And upgraded the driver using Synaptic as well.
I don't understand how this printer is recognized by Ubuntu but fails to print-
Is it just me 3Miro; or is this bazaar?

What do you recommend?

---

### Post by UltimateCat on 2012-07-24
> **nothingspecial said:**
> Thread title changed to reflect the problem.

Thank You;)

---

### Post by UltimateCat on 2012-07-24
When I went to Sys>Admin>Printing the print manager confirms
```
Connected to localhost

```
I'm not connected to a server.  My ISP provided me with a modem and my Computer communicates with the modem via a Linksys adapter and my internet connection has been very good.

I used the troubleshooting wizard that opened up while I was digging around in the Print Manager and it told me something to the extent that the problem was not able to be solved.  
Not sure what to do here.  But I only have 30 days to return this printer to the merchant ( no stress or pressure on you) and it's already been 18 days.

What on earth could I be overlooking?

---

### Post by UltimateCat on 2012-07-24
> **oscarivera9 said:**
> About half a year ago I was having trouble scanning documents and so I looked into installing hplip to get my printer/scanner to scan.  So basically I had to switch from using CUPS to using hplip.   I'm trying to remember exactly how I finally got it to work, but I can't seem to remember what the trick was.  I do remember that part of the  problem had something to do with having the wrong setting with the server that hplip had to connect to.
However, while I was retracing my steps in order to help you, I found this web page that might help you:

[https://help.ubuntu.com/community/HpAllInOne](https://help.ubuntu.com/community/HpAllInOne)
Make sure to read everything, especially the section all the way down that says 
**Setting up printers to use HPLIP**



Also, if it helps any, I do remember that eventually, when I upgraded to Ubuntu 12.04, CUPS was installed automatically and I didn't have to use hplip any more.


If I can think of anything else I'll let you know.

Oscarivera9:
You said that you had to switch from using cups to using hplip-
How exactly did you switch?
Curious as I'm reaching my wits end.........

---

### Post by oscarivera9 on 2012-07-24
> Oscarivera9:
You said that you had to switch from using cups to using hplip-
How exactly did you switch?
Curious as I'm reaching my wits end.........                                                                                               __________________Unfortunately, the way I did it was by following the instructions on this webpage that you already listed:
[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

And in fact, come to think about it, I don't think I switched from cups to hplip exactly, but rather manually updated the hplip software.  Like I said, I do remember having to adjust something so that my PC's hplip could connect to the correct server, so you may want to look into that. 
 Have you tried the following?:
1. unplugging your printer, shutting it off, leaving it unplugged from the PC for a minute or two, then re-connecting it and turning it back on

Sometimes, something as simple as that will do the trick.  If that doesn't work, then after plugging it back in go ahead and 

2. Delete any entries for this printer in System->Administration->Printers. 
3. Run HP Setup from the console.      

sudo hp-setup  

This will walk you through the setup for USB, network or parallel connections.

---

### Post by jimmac49 on 2012-07-24
Google HPLIP, and follow the instructions there, this is what I did for my HP Photosmart 6510 all in one, it works in 12.04 which I am using now, it also worked in 10.04 no problems.

Give it a try, you have nothing to lose.

Luck

---

### Post by UltimateCat on 2012-07-24
> **jimmac49 said:**
> Google HPLIP, and follow the instructions there, this is what I did for my HP Photosmart 6510 all in one, it works in 12.04 which I am using now, it also worked in 10.04 no problems.

Give it a try, you have nothing to lose.

Luck

I did follow the instructions and installed hplip-3.12.6.run and the install went well.  I have the HP icon on my desktop next to my clipboard manager and clock.
I don't get why this printer is not printing-

---

### Post by UltimateCat on 2012-07-24
> **oscarivera9 said:**
> Unfortunately, the way I did it was by following the instructions on this webpage that you already listed:
[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

And in fact, come to think about it, I don't think I switched from cups to hplip exactly, but rather manually updated the hplip software.  Like I said, I do remember having to adjust something so that my PC's hplip could connect to the correct server, so you may want to look into that. 
 Have you tried the following?:
1. unplugging your printer, shutting it off, leaving it unplugged from the PC for a minute or two, then re-connecting it and turning it back on

Sometimes, something as simple as that will do the trick.  If that doesn't work, then after plugging it back in go ahead and 

2. Delete any entries for this printer in System->Administration->Printers. 
3. Run HP Setup from the console.      

sudo hp-setup  

This will walk you through the setup for USB, network or parallel connections.

I tried the unplug of all and what you mentioned-  Still nothing prints.

I'll try Sys>Admin>Printing like you advised me and see if that makes any difference.

Hope something works soon.  It's really a nice printer; I'd hate to return it
But I'll keep trying...see what happens
Thank You;)

---

### Post by oscarivera9 on 2012-07-25
If nothing else works and you'd like to know whether to return the printer or not, try using a Live CD from Ubuntu and other distros to find out if that printer works at all with any Linux.  If it works, even if it's with another distro, then at least you know that you can get it to work with the right settings.

---

### Post by Alcidious on 2012-07-25
provided your printers driver is supported by hplip, your installer should do almost everything on its own when you type sh hplip-3.12.6.run, or whatever.  I just installed my first printer, an BP office, a few weeks ago. u should also be able to do it with the ubuntu add printer utility, if the driver and printer are supported. when I attempted it my printer was new, but the new hplip was going to support it, so I waited and installed it through the terminal and the .run file. seems like u got it worked out though! I'm finding the best policy is not to freak out when I have issues, its usually something really simple!

---

### Post by UltimateCat on 2012-07-25
> **oscarivera9 said:**
> If nothing else works and you'd like to know whether to return the printer or not, try using a Live CD from Ubuntu and other distros to find out if that printer works at all with any Linux.  If it works, even if it's with another distro, then at least you know that you can get it to work with the right settings.

I have given thought to installing another distro.  And; I'm am seriously considering what you have said as I'm at my wits end with this printer.

For writing to me; advising me and giving me instructions and help :


Thank You:)

---

### Post by UltimateCat on 2012-07-25
> **Alcidious said:**
> provided your printers driver is supported by hplip, your installer should do almost everything on its own when you type sh hplip-3.12.6.run, or whatever.  I just installed my first printer, an BP office, a few weeks ago. u should also be able to do it with the ubuntu add printer utility, if the driver and printer are supported. when I attempted it my printer was new, but the new hplip was going to support it, so I waited and installed it through the terminal and the .run file. seems like u got it worked out though! I'm finding the best policy is not to freak out when I have issues, its usually something really simple!

Indeed the driver from the installer that I used the terminal to install the hplip-3.12.6.run was included.

Even after the successful install......the printer still does not print and I have come to the end of my rope with it-

I agree freakin out does not help however; I have been  consistent and  persistent for 3 weeks now (troubleshooting) following the advise and instructions that members here have given me. 

Ich bin fertig. In German; means I am done-  

I am considering another distro

---

### Post by oscarivera9 on 2012-07-26
> **UltimateCat said:**
> I have given thought to installing another distro.  And; I'm am seriously considering what you have said as I'm at my wits end with this printer.

For writing to me; advising me and giving me instructions and help :


Thank You:)

You're welcome.  There are many reasons I love Ubuntu and the user community is one of them, so when I can give back a little of what has been freely given to me, I try my best to help.  Go ahead and do like I said, try using a Live CD to see if that works.  It's best to try stuff out before you commit to a full install only to find out that the printer is still not working.  Try using an Ubuntu Live CD just for kicks, you never know.  If that doesn't work, then try something else like Xubuntu which is based on the Ubuntu family but it's different enough that it may work.  If that doesn't work then go ahead and try something completely different.  It seems to me like this printer is relatively new and sometimes with Linux, you just have to wait for it to work properly.  

I know you've been patient with this issue, but being that it's almost time to decide to return it or not, you may have to make that choice if it doesn't work with another distro.  :(

Best of Luck

---

### Post by jimmac49 on 2012-07-26
Just googled hplip, and went through the motions of downloading for HP Envy, it is not listed in the printer type section, apart from under other, where there are two printer models:- HP Envy 100d410-series and HP Envy 100E All-In-One.
Have you tried both?.

What command line instructions did you use, the ones that came with download?.

---

### Post by Alcidious on 2012-07-28
Hey man,

I looked at the HPLIP site and didn't see your Envy 114 listed as supported.  I had the same issue when i got my Officejet 4620 in May.  Supposedly you can use similar, other, drivers, but I was wary since im still a newbie.  Anyway, I sent a message to the guys at HPLIP to ask them if/when it would be supported; luckily, they responded saying it would be included in the next HPLIP- the 3.12.6.  Perhaps your printer is too new, like mine was.

If you haven't yet, send them a message before you give up.  Or look at their list of recommended/supported printers and just trade it out.  I know that sucks, but maybe this problem is just that?

---

### Post by nino75 on 2012-08-10
> **oscarivera9 said:**
> 

2. Delete any entries for this printer in System->Administration->Printers. 
3. Run HP Setup from the console.      

sudo hp-setup  

This will walk you through the setup for USB, network or parallel connections.

Thak you very much oscarivera9 i fixed my **hp 1132 mfp** *5012 error* with the above trick ... you are great and this forum is great !!!
Good summer :)
[I]
Nino75
[/I]

---

### Post by oscarivera9 on 2012-08-13
> **nino75 said:**
> Thak you very much oscarivera9 i fixed my **hp 1132 mfp** *5012 error* with the above trick ... you are great and this forum is great !!!
Good summer :)
[I]
Nino75
[/I]

You're welcome.  Just trying to give back a little of what was freely given to me.

---

### Post by Karl_L on 2012-08-13
> **UltimateCat said:**
> :)Hi

I went to [www.psychocats.net/ubuntu](www.psychocats.net/ubuntu) for help.

Normally I would use the terminal but in this case; installing as root in not advised by HP.

Are there instructions I can follow to install a package (.run) using the Ubuntu Software Center?
I used sudo apt-get install hplip to switch to HP Linux Internet Printing  rather than using default CUPS and have had no problems since with printer.

---

### Post by Karl_L on 2012-08-13
> **UltimateCat said:**
> Indeed the driver from the installer that I used the terminal to install the hplip-3.12.6.run was included.

Even after the successful install......the printer still does not print and I have come to the end of my rope with it-

I agree freakin out does not help however; I have been  consistent and  persistent for 3 weeks now (troubleshooting) following the advise and instructions that members here have given me. 

Ich bin fertig. In German; means I am done-  

I am considering another distro
Mann, Es ist noch kein Meister vom Himmel gefallen.
Don't give up.

---


---
title: "difficulty with wireless card"
date: 2006-03-19
forum: General Help
---

### Post by willemmerson on 2006-03-19
Hello, I have a BT Voyager 1040 wireless card which I am trying to get to work with Ubuntu via ndiswrapper. I know how to use ndiswrapper and have all the windows drivers, the problem is that I can't seem to install it in Ubuntu because the package manager won't open. Almost all the admin programs won't open in fact - am I doing something stupid, like not getting permissions or something?
Every time I try to configure the wireless card, programs just seem to hang.
I could maybe try to install ndiswrapper from the command line but I would quite like to know why nothing is working properly from the desktop.

---

### Post by Zelut on 2006-03-19
You can try the '10 steps to wireless' in my signature & see if that gets you on a closer track.  Those commands are from the command line but, I think, the instructions are pretty straight-forward..  

Give it a try & let me know.  We'll get you working..

---

### Post by willemmerson on 2006-03-19
Hello, I can't believe how fast people reply on this forum! I left a message on the mandriva forum and had to wait overnight! 
I'll try what you say. As I said, I have the .inf and .sys files and know what chipset it is, a broadcom BCM 4306. There is actually a project to make a native linux driver for this chipset but I havn't a hope in hell of compiling it. I can compile visual basic in Windoze and thats my limit.
I'll also try and write down what things aren't working, because it does seem a bit wierd.

---

### Post by Zelut on 2006-03-19
If that is your chipset I can almost guarantee that we can get you working.  I have that chipset on my machine & its been running wireless for months.  (I've also configured 3 other Broadcom cards, also with minimal trouble.)

I have been testing the native driver for use with Dapper, but that hasn't worked as well for me as has the ndiswrapper method.

---

### Post by willemmerson on 2006-03-19
...I forgot to say - I put the windows drivers on an ntfs partition next to the Ubuntu partition, how can I get to these? I had a mess around in the file manager but couldn't see anything but the Ubuntu directory. Does Ubuntu read NTFS?

---

### Post by willemmerson on 2006-03-20
I tried sudo apt-get install ndiswrapper-utils and it says:
'sudo: unable to lookup diningroom via gethostname()'
Also, after I log in it says
'could not look up internet address for diningroom. This will prevent gnome from operating correctly...' and some more stuff.

Any ideas?

---

### Post by Zelut on 2006-03-20
Ok it sounds like we've got an entire different issue as well.

What is 'diningroom'?  Is that the hostname of your PC?
Can you tell me what is listed in the General tab of your Network Settings? (Sys > Admin > Networking)

---

### Post by willemmerson on 2006-03-20
diningroom is the name of the computer which it asked me for during install, is that the hostname?
I can't tell you what is listed in the general tab of my network settings because it doesn't work - it starts in the taskbar then just disapears. This is the same with ALL the things in sys\admin except device manager.
Also, I tried apps\system\networktools afterwards and the whole computer hung and I had to actually press the reset button.
Its not looking good.

---

### Post by Zelut on 2006-03-20
To return to a question I didn't see before.  Yes Ubuntu can read NTFS (but currently can't write-to NTFS).  If you have your drivers there we can help you get that loaded or you can use the two lines below to download the driver I use.

wget [http://christer.homeip.net/bcmwl5.inf](http://christer.homeip.net/bcmwl5.inf)
wget [http://christer.homeip.net/bcmwl5.sys](http://christer.homeip.net/bcmwl5.sys)

Do you have a wired connection you can use while we get this wireless setup?  You'll need some access outside if possible (and if not we can still use a work-around, but its a little more work).

---

### Post by willemmerson on 2006-03-21
Hello again, I have managed to sort out the whole 'unable to lookup diningroom via gethostname()' stuff. I installed some driver so I could edit linux files from windows and I edited the etc/hosts file to include 'diningroom'; I couldn't seem to edit it through Ubuntu, even in recovery mode.
Anyway, I installed ndiswrapper but when I tried to install the bcmwl5 file there was an error.
I now have 3 different versions of bcmwl5 though. The first one I got out of my windows installation and it is only the .sys file. 
The second one I got from ndiswrapper.com which was actually a link to a Dell or Acer support site. It includes bcmwl5.sys, bcmwl5a.sys and bcmwl5.inf.
The third one is from your link above.
I havn't tried yours yet, I'll try it now...its such a pain in the arse switching between windows and linux.
By the way I COULD have a wired connection but it would be a right hassle - I'd rather try and do it unwired unless its really difficult.
Thanks for all your help!

---

### Post by willemmerson on 2006-03-22
Hello, I have now managed to install the drivers into ndiswrapper and it says 'hardware present, driver present' but nothing is working, and there are no lights on the wireless card. I have set up WEP and network name but not sure about DHCP.

---

### Post by Zelut on 2006-03-22
You'll also need to make sure you **sudo modprobe ndiswrapper** (to insert the module into the kernel).  Have you configured the card & broadcast in your network settings area?  ..also, on first installation I often have to reboot.

---

### Post by willemmerson on 2006-03-22
I've done everything you said in your '10 steps', including rebooting and it still doesn't work. I took screenshots of the bt voyager 1040 property pages in the device manager in Ubuntu if you need to know anything.

---

### Post by willemmerson on 2006-03-24
Hello! I'm writing this from Mandriva, finally got my wireless card working! I tried it in Ubuntu, Knoppix, Mepis but this is the only distro it worked in, it must have a more recent version of ndiswrapper or something. Also realised that my CDrom drive was broken which was causing a lot of problems, and only today realised I could get into root user with name 'root' and password 'root'...it seems so obvious now. Guess I should have read the f*cking manual. I think my linux nightmare is finally over...or just beginning.
Thanks for all your help anyway...

---


---
title: "Trouble with UBuntu"
date: 2006-04-04
forum: General Help
---

### Post by GameSky on 2006-04-04
I'm new to linux world... and decided to try it coz it's open source...and got some function I wanted which is unavailable for Windows...

Currently I've Ubuntu Linux 5.10 Install and Live CD which I obtained from their website

Before installing Ubuntu Linux..I decided to try it out first, by using the bootable Live CD...

Everything is running normal..until when the system tries to boot up into the GUI....and this error comes out:

"Failed to start the X server(your graphical interface). It is likely that is not set up correctly. Would you like to view the X server output to diagnose the problem?"

I can't view the report because the word "ubuntu@unbuntu:~$" is floating around..and when I press 'Enter' key...the word "ubuntu@unbuntu:~$" keeps coming out..

Any linux expert here? Can you help me?

my comp specs:
Intel P2.4Ghz 1MB
Asus P4v8x-x mb
768 MB DDR400 (512MB+256MB Apacer)
40GB (2 partition with all formatted to NTFS)
ATi Radeon 9200 SE

Thanks in advance!

---

### Post by WelterPelter on 2006-04-04
The ubuntu@ubuntu is your command line prompt. That is a terminal from which you can enter commands into the computer without the GUI. 

In order to get things working right, you are going to have to configure the X server from that command line. There are several threads in this forum that will show you how to do it. 

Hang in there. It gets better. ;)

---

### Post by RRS on 2006-04-04
Sounds like X is having trouble with your video card.

For an installation you'd likely have to install a "linux" friendly driver and then manually configure the xorg files to match.

Proccess is actually easier then it sounds so don't worry, but I'd suggest more experienced help then I can provide. The "Hardware" section  or possibly "Beginner Talk" may be a better place to post if you can't find by searching.

Also be sure you specify your running the live CD as the procedure is likely different.

The folks here are really good @ helping us "Newbies" so I'm sure you'll get things sorted out quickly.

---

### Post by johnc4510 on 2006-04-04
Try this at boot login then:
sudo apt-get install xorg-driver-fglr
sudo xorg-driver-fglrx-config enable
Worked for me using nvidia drivers.
By the way, I looked up and used the correct drivers for your Radeon card.

---

### Post by johnc4510 on 2006-04-05
[QUOTE=johnc4510]Try this at boot login then:sudo apt-get install xorg-friver-fglrx
                                    sudo xorg-driver-fglrx-config enable
Worked for me using nvidia drivers.[/QUOTE]
By the way, I used the drivers for your radeon card.

---

### Post by GameSky on 2006-04-05
Thanks for the reply guys...I'm still new to linux though...will definitely go try it out :D

---


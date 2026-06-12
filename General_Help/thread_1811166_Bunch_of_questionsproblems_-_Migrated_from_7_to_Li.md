---
title: "Bunch of questions/problems - Migrated from 7 to Linux about a month ago."
date: 2011-07-24
forum: General Help
---

### Post by Jimboland on 2011-07-24
Hello guys, 

I'm having some problems with my Linux (Kubuntu) installation.
I deleted Windows more then a month ago and replaced it with Linux (finnaly) :)

After trying a few different distro's i ended up with Kubuntu. I like it, its nice to use and easy at most of times to configure, but its not very "stable" Not like i would expect from Linux installation..

-To start, its not as smooth nor fast as my previously installed windows 7. 
I hope this can be fixed with some driver updates?

-Chromium won't start from time to time, the only way round this is a system reboot (after a fresh reboot!) 
Before i was using Firefox and i had simular problems. Even Rekonq had problems, infact at one time i couldn't start none of my tree browsers. But after i updated some packages they where working again. But this is not normal, is it?

-Just today, my dolphin file manager kept crashing, also after a fresh reboot. So, again.. Reboot system..

- When i install a new file manager like "Gentoo", "Tuxcommander"
I can't open my media from inside the file manager, meaning:
If i double click on an mp3 file using Gentoo or Tux it doesn't start playing for some reason. Nothing happens.. Why?
**Solved**

-When i'm using Gtalk, and i want to use the webcam using the browser plugin that Google provides, it crashing every two minutes. So that means it not usable, and that means take my notebook with Windows 7 just to use the webcam..

-My NAS (dns-320) is not reachable from Kubuntu, it keep asking me for the correct login and pass. While i'm really sure the details are correct. 
Is there a simple "net use" like command i can use to connect my NAS from the terminal?

-Is there anyway to disable animation screen when (k)ubuntu is shutting down? 
I would prefer to see whats happing in the shell/terminal/konsole, rather than see "Kubuntu is shutting down" ... ... ... ...

So many questions, i hope somebody can en is willing to help me. All help would be really appricated.

Thanks in advance

---

### Post by oldos2er on 2011-07-24
Sometimes if you start a program in a konsole, it will show information as to why it might be failing or crashing.

For the mp3 issue, have you installed the proper codecs? [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

What are your system specs?

---

### Post by Jimboland on 2011-07-24
I have all codec's installed because when I open them with the standard Dolphin file manager, they play perfect. Its just when i try to open them with a different file manager.

And, i frequently open programs in the Terminal, but with my web browsers is the problem that they won't start at all (sometimes)

My system specs are:

Abit kn9 ultra mobo
[http://www.abit.com.tw/page/en/motherboard/motherboard_detail.php?pMODEL_NAME=KN9+Ultra&fMTYPE=Socket%20AM2](http://www.abit.com.tw/page/en/motherboard/motherboard_detail.php?pMODEL_NAME=KN9+Ultra&fMTYPE=Socket%20AM2)

AMD 5600+ Proc
Western digital caviar black 640GB
ATI X1800GTO Video card

Not the lastest hardware, but it was perfectly capable to run 7.
So i assume it shouldn't be a problem for Linux, right?

---

### Post by Jerry N on 2011-07-24
Have you considered re-installing Kubuntu from scratch?  This _might_ solve some of your stability problems but in my experience Kubuntu is not noticeably faster than Win 7.  

Jerry

---

### Post by Jimboland on 2011-07-24
No i didn't, because installing it was a pain as well.
I had to install it from a USB key and still it was giving me a hard time. Isn't there any way to repair all the packages?

---

### Post by bakegoodz on 2011-07-24
The instability your experiencing is not typical with Linux. Not enough information is given to know the problem for certain. I have a couple of educated guesses though. 
 First is example from experience, where I saw Windows crash rarely and Linux crash all the time on the same computer. I can't explain it, but sometimes failing hardware doesn't effect Windows as much as Linux. In this case it was bad RAM causing the problems. Replacing the RAM made Windows and Linux (More obviously) run reliable again.
  Second Do you have a Nvidia video card? The opensource Nouveau driver is not very stable for recent Nvidia chips and installing the Nvidia driver will fix it, if that is the issue. There are several guides to installing this, the easiest is using the built-in tool "Hardware Drivers" in Administration or the Control Panel, look around. I heard the same issue for ATI too, if the card is a very new model.

---

### Post by Jimboland on 2011-07-24
No, i have an x1800GTO video card. Which is not new. Its pretty old. 
I will try to update the drivers, i just have figure out which drivers are best.

And if you tell me which info i have to provide to give you a clue of whats going on, tell me. I will happely post it.
I  just don't know what more i can say right now.

Like you said, i don't have much experience _yet_ with Linux. So i don't know what else to say or do. thats why i came here.

---

### Post by bakegoodz on 2011-07-25
Are you getting any error messages? Put this in the command line: tail -n 80 /var/log/syslog Any error messages there? If you are having instability in about every program I would suspect a hardware problem. Running Memtest will test your RAM
 [http://www.memtest.org/download/4.20/memtest86+-4.20.iso.zip](http://www.memtest.org/download/4.20/memtest86+-4.20.iso.zip) (unzip and burn iso file)

---

### Post by Jimboland on 2011-07-25
I don't see any errors there.


[I][B]*@Black:~/Downloads$ tail -n 80 /var/log/syslog
Jul 25 19:12:01 Black NetworkManager[1435]: <info> (eth1): device state change: 1 -> 2 (reason 2)
Jul 25 19:12:01 Black NetworkManager[1435]: <info> (eth1): preparing device.
Jul 25 19:12:01 Black NetworkManager[1435]: <info> (eth1): deactivating device (reason: 2).
Jul 25 19:12:01 Black avahi-daemon[966]: Withdrawing address record for 192.168.0.103 on eth1.
Jul 25 19:12:01 Black avahi-daemon[966]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.0.103.
Jul 25 19:12:01 Black avahi-daemon[966]: Interface eth1.IPv4 no longer relevant for mDNS.
Jul 25 19:12:01 Black NetworkManager[1435]: <info> Added default wired connection 'Auto eth1' for /sys/devices/pci0000:00/0000:00:09.0/net/eth1
Jul 25 19:12:01 Black NetworkManager[1435]: <info> (eth1): device state change: 2 -> 3 (reason 0)
Jul 25 19:12:01 Black NetworkManager[1435]: <info> Activation (eth1) starting connection 'Auto eth1'
Jul 25 19:12:01 Black NetworkManager[1435]: <info> (eth1): device state change: 3 -> 4 (reason 0)
Jul 25 19:12:01 Black NetworkManager[1435]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Jul 25 19:12:01 Black NetworkManager[1435]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Jul 25 19:12:01 Black NetworkManager[1435]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Jul 25 19:12:01 Black NetworkManager[1435]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Jul 25 19:12:01 Black NetworkManager[1435]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Jul 25 19:12:01 Black NetworkManager[1435]: <info> (eth1): device state change: 4 -> 5 (reason 0)
Jul 25 19:12:01 Black NetworkManager[1435]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) successful.
Jul 25 19:12:01 Black NetworkManager[1435]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
Jul 25 19:12:01 Black NetworkManager[1435]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Jul 25 19:12:01 Black NetworkManager[1435]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
Jul 25 19:12:01 Black NetworkManager[1435]: <info> (eth1): device state change: 5 -> 7 (reason 0)
Jul 25 19:12:01 Black NetworkManager[1435]: <info> Activation (eth1) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jul 25 19:12:01 Black NetworkManager[1435]: <info> dhclient started with pid 1439
Jul 25 19:12:01 Black NetworkManager[1435]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.                                                                                      
Jul 25 19:12:01 Black dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1                   
Jul 25 19:12:01 Black dhclient: Copyright 2004-2010 Internet Systems Consortium.                   
Jul 25 19:12:01 Black dhclient: All rights reserved.                                               
Jul 25 19:12:01 Black dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)          
Jul 25 19:12:01 Black dhclient:                                                                    
Jul 25 19:12:01 Black NetworkManager[1435]: <info> (eth1): DHCPv4 state changed nbi -> preinit     
Jul 25 19:12:01 Black dhclient: Listening on LPF/eth1/00:50:8d:97:37:e4                            
Jul 25 19:12:01 Black dhclient: Sending on   LPF/eth1/00:50:8d:97:37:e4                            
Jul 25 19:12:01 Black dhclient: Sending on   Socket/fallback                                       
Jul 25 19:12:01 Black dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3         
Jul 25 19:12:01 Black dhclient: DHCPOFFER of 192.168.0.103 from 192.168.0.1                        
Jul 25 19:12:01 Black dhclient: DHCPREQUEST of 192.168.0.103 on eth1 to 255.255.255.255 port 67
Jul 25 19:12:01 Black dhclient: DHCPACK of 192.168.0.103 from 192.168.0.1
Jul 25 19:12:01 Black dhclient: bound to 192.168.0.103 -- renewal in 146017759 seconds.
Jul 25 19:12:01 Black NetworkManager[1435]: <info> (eth1): DHCPv4 state changed preinit -> bound
Jul 25 19:12:01 Black NetworkManager[1435]: <info> Activation (eth1) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jul 25 19:12:01 Black NetworkManager[1435]: <info> Activation (eth1) Stage 4 of 5 (IP4 Configure Get) started...
Jul 25 19:12:01 Black NetworkManager[1435]: <info>   address 192.168.0.103
Jul 25 19:12:01 Black NetworkManager[1435]: <info>   prefix 24 (255.255.255.0)
Jul 25 19:12:01 Black NetworkManager[1435]: <info>   gateway 192.168.0.1
Jul 25 19:12:01 Black NetworkManager[1435]: <info>   nameserver '192.168.0.1'
Jul 25 19:12:01 Black NetworkManager[1435]: <info>   domain name 'Jims'
Jul 25 19:12:01 Black NetworkManager[1435]: <info>   wins '192.168.0.1'
Jul 25 19:12:01 Black NetworkManager[1435]: <info> Scheduling stage 5
Jul 25 19:12:01 Black NetworkManager[1435]: <info> Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled...
Jul 25 19:12:01 Black NetworkManager[1435]: <info> Done scheduling stage 5
Jul 25 19:12:01 Black NetworkManager[1435]: <info> Activation (eth1) Stage 4 of 5 (IP4 Configure Get) complete.
Jul 25 19:12:01 Black NetworkManager[1435]: <info> Activation (eth1) Stage 5 of 5 (IP Configure Commit) started...
Jul 25 19:12:01 Black avahi-daemon[966]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.0.103.
Jul 25 19:12:01 Black avahi-daemon[966]: New relevant interface eth1.IPv4 for mDNS.
Jul 25 19:12:01 Black avahi-daemon[966]: Registering new address record for 192.168.0.103 on eth1.IPv4.
Jul 25 19:12:02 Black NetworkManager[1435]: <info> (eth1): device state change: 7 -> 8 (reason 0)
Jul 25 19:12:02 Black NetworkManager[1435]: <info> Policy set 'Auto eth1' (eth1) as default for IPv4 routing and DNS.
Jul 25 19:12:02 Black NetworkManager[1435]: <info> Activation (eth1) successful, device activated.
Jul 25 19:12:02 Black NetworkManager[1435]: <info> Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete.
Jul 25 19:12:03 Black rtkit-daemon[1502]: Successfully called chroot.
Jul 25 19:12:03 Black rtkit-daemon[1502]: Successfully dropped privileges.
Jul 25 19:12:03 Black rtkit-daemon[1502]: Successfully limited resources.
Jul 25 19:12:03 Black rtkit-daemon[1502]: Running.
Jul 25 19:12:03 Black rtkit-daemon[1502]: Canary thread running.
Jul 25 19:12:03 Black rtkit-daemon[1502]: Successfully made thread 1500 of process 1500 (n/a) owned by '1000' high priority at nice level -11.
Jul 25 19:12:03 Black rtkit-daemon[1502]: Supervising 1 threads of 1 processes of 1 users.
Jul 25 19:12:03 Black rtkit-daemon[1502]: Watchdog thread running.
Jul 25 19:12:04 Black rtkit-daemon[1502]: Successfully made thread 1505 of process 1500 (n/a) owned by '1000' RT at priority 5.
Jul 25 19:12:04 Black rtkit-daemon[1502]: Supervising 2 threads of 1 processes of 1 users.
Jul 25 19:12:04 Black rtkit-daemon[1502]: Successfully made thread 1513 of process 1500 (n/a) owned by '1000' RT at priority 5.
Jul 25 19:12:04 Black rtkit-daemon[1502]: Supervising 3 threads of 1 processes of 1 users.
Jul 25 19:12:04 Black rtkit-daemon[1502]: Successfully made thread 1514 of process 1500 (n/a) owned by '1000' RT at priority 5.
Jul 25 19:12:04 Black rtkit-daemon[1502]: Supervising 4 threads of 1 processes of 1 users.
Jul 25 19:12:10 Black ntpdate[1493]: adjust time server 91.189.94.4 offset 0.130489 sec
Jul 25 19:21:37 Black kernel: [  597.828951] exe (2269): /proc/2269/oom_adj is deprecated, please use /proc/2269/oom_score_adj instead.
Jul 25 19:28:29 Black ntfs-3g[2646]: Version 2010.8.8 external FUSE 28
Jul 25 19:28:29 Black ntfs-3g[2646]: Mounted /dev/sdb3 (Read-Write, label "Everything", NTFS 3.1)
Jul 25 19:28:29 Black ntfs-3g[2646]: Cmdline options: rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,dmask=0077,fmask=0177
Jul 25 19:28:29 Black ntfs-3g[2646]: Mount options: rw,nosuid,nodev,uhelper=udisks,allow_other,nonempty,relatime,fsname=/dev/sdb3,blkdev,blksize=4096,default_permissions
Jul 25 19:28:29 Black ntfs-3g[2646]: Global ownership and permissions enforced, configuration type 1
*@Black:~/Downloads$ 
[/B][/I]

I will try the memory test and update my post.

---

### Post by Mark Phelps on 2011-07-25
> **Jimboland said:**
> No, i have an x1800GTO video card. Which is not new. Its pretty old. 
I will try to update the drivers, i just have figure out which drivers are best.

You're right in the card being "pretty old", so old, in fact, that ATI dropped proprietary Linux driver support for that card years ago.

The open-source ATI drivers are installed by default for that card -- and are the only drivers that will work now.  Don't need to waste your time hunting down other drivers because there aren't any.

---

### Post by Jimboland on 2011-07-26
Well thats a nice reply..
Thanks for reminding me how "old" my hardware is. 
A video card launched in de middle of 2006 has no Linux support "anymore" but windows 2000 pro is still supported.... :P
So what you think? Its AMD being lazy and cheap or the hardware thats sooo old?

Serious; I read somewhere that i had to remove the "fglrx" and download the "radeon" driver. But appertly not. I'll take your word for it.

I also did a memory test(the one build by kubuntu) and there are many errors.  So if this test is reliable?? I have to change my memory.
Can somebody verify this?

---

### Post by Topsiho on 2011-07-26
If the memory test shows ((m)any) errors, then your question is answered, so you can do two things: try which memory stick is faulty (take one out, run the test again, a number of passes, if necessary), and if the memory still is faulty, take the next one out (and the previous one in :D), until your memory appears to be OK.

You need to have 512 mb of memory, so if necessary you'll have to buy some. As your computer is old, I guess you'll have to see the manual of your motherboard, to see what ram you need. And try and find it ...

Topsiho

---

### Post by Jimboland on 2011-07-26
Wel i had 17000+ errors this morning when i woke up, and the test was just 84% finished.
So i guess my memory ready for the bin.
The funny thing is, the memory was the most recent hardware in my computer:)
I bought it as "new" from ebay, 2x 2GBkingston DDR2 800mhz 240PIN.
In the worst case I still have my old memory which was 2x1GB.


I will run the tests again tonight, as soon as i see 1 error i will stop the test en try a new stick.

---

### Post by bakegoodz on 2011-07-26
I have had RAM go bad before. It shows as a few bad blocks in Memtest. When I have had massive amount of errors it was a motherboard problem. Look at your motherboard, look at the capacitors, the little cylindrical parts sticking up. They should all have flat tops. If any of them are domed up, or have brown junk on them. It's time to get a new motherboard, or if your skilled with a soldering iron and know what your doing you can replace the caps. Also I have found on several motherboards loose the ability to do dual channel after a few years of use. Putting 2 sticks together in non-dual channel model, or using 1 stick fixes this. Test 1 stick of RAM at a time and see if it passes.

---

### Post by walt.smith1960 on 2011-07-26
> **Jimboland said:**
> Wel i had 17000+ errors this morning when i woke up, and the test was just 84% finished.
So i guess my memory ready for the bin.
The funny thing is, the memory was the most recent hardware in my computer:)
**I bought it as "new" from ebay, 2x 2GBkingston DDR2 800mhz 240PIN.**
In the worst case I still have my old memory which was 2x1GB.


I will run the tests again tonight, as soon as i see 1 error i will stop the test en try a new stick.

That is a risk with buying electronics off Ebay.  You have no way of knowing whether the DRAM was really new, or if it was returned to a retailer in original packaging after having been subjected to static discharges or other damage.  There's no way to tell by looking at it.  I bought some DRAM off Ebay for a geriatric laptop but

[LIST=1]
[*]It was less than $10 including shipping
[*]I ran Memtest on it as soon as I installed it.  I'd recommend the same to anyone buying DRAM from any source.  Make sure you can return it if faulty and test it long enough for any problems to show themselves.
[/LIST]
You could test one stick at a time, and also test your old DRAM.  If they ALL show lots of errors, it probably is a MoBo problem like bakegoodz says.

---

### Post by Topsiho on 2011-07-26
17000+ errors is a lot. Means you have either very bad memory, or indeed the mother board is probably gone.

When testing memory the problem is that if you find an error, even if it is only one, you KNOW your memory is faulty. Only thing is which stick is not OK.
But if you find no errors, then you might think the memory is OK, but it might be not. Some errors only show up sometimes, and sometimes they don't. That's why you should run several passes, in that case. In fact you should run the test eternally, just to be really sure, but most people don't :D in these impatient times.

Topsiho

---

### Post by Jimboland on 2011-07-26
I will start tonight with checking the motherboard for bad capacitors. There's a good chance there gone because there just regular onces, not solid.
And i heared several story's of melted capacitors that caused system errors. But before i saw these errors this morning, i was not considering hardware problems.

If everything is ok i will try one stick at the time. I just wonder is a BIOS update could be of any use, because i saw some user reviews saying:

*"I had regular Linux crashes until I  updated the BIOS. The BIOS from January contains some specific Linux  fixes. Now everything is working great."*

*"S*cks  on Linux. HD Audio is buggy, onboard network, MCP55 chipset still needs  some time before it works well. You have to use 'noapic' boot  parameter.*


And when u look on the BIOS update page:

[B]BIOS ID:18
     

    Update CPU micro code.
    Enhanced compatibility with Linux.
    BIOS compiled date: 1/16/2007[/B]

Could it be the BIOS?

---

### Post by walt.smith1960 on 2011-07-27
The rule of thumb is don't update BIOS unless there's a problem.  You certainly have a problem so I probably would update it if it were mine.  Pick a time when your power seems stable if that's an issue for you.  Any power interruption during a BIOS update and you may have just created an inconvenient expensive brick.  If there's an option to back up your current BIOS first, you might want to do that.

---

### Post by Jimboland on 2011-07-28
I did a few memory tests, one module at the time in the same slot, and one of the two was giving thousands of errors. So i removed it, did a BIOS update and now everything is working perfect :)

I will do a complete re-installation tomorrow to start with a clean sheet,and then i can start fine tuning things the way i like it.

Thanks for your help guys!

---

### Post by Topsiho on 2011-07-29
Great!

So it's not the mother board, nor the BIOS, which saves you a lot of trouble, and gives you a more dependable computer.

Hope the amount of memory left is still sufficient. Should be 512+ MB, for running Ubuntu graphically. I think you mentioned it somewhere, but I am too lazy to try and find where :)

You mentioned slots. Dirty slots can also cause problems. Nice to know next time, or for the readers of this thread :)

Topsiho

---


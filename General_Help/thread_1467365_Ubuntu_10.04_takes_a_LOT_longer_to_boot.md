---
title: "Ubuntu 10.04 takes a LOT longer to boot"
date: 2010-04-30
forum: General Help
---

### Post by Skyline969 on 2010-04-30
Ok, well Ubuntu 9.10 took around 10 seconds to boot whereas Ubuntu 10.04 takes around 30. It sticks a lot at the "booting from hd0, blah blah blah" screen (black with just white text), then goes to another screen where it seems to be checking the condition of my system (battery, etc). Then, it finally goes to the purple Ubuntu screen and I am immediately presented with the login screen.

I'm running on a Dell Inspiron 1525 with an Intel Dual-Core processor (32 bit) with 2 GB of RAM. Any insight would be greatly appreciated.

---

### Post by Shadow12313 on 2010-04-30
I am not quite sure what the problem is but I heard removing HAL increases boot speed.

---

### Post by Kirky_D on 2010-04-30
I've been dissapointed with the speed to be honest as well, especially after all the gype of hal removal. Takes me 50 secs to get to gnome (Core 2 du0). The longest bit is actually between login and getting to the desktop.

---

### Post by Orographic on 2010-04-30
Yes, the longest delay for me too is from log in to the desktop which takes about 25 seconds and this has been the case for me since Alpha versions and was reported as a bug.

My system is a a Gigabyte 945GZMS2 with intel onboard graphics that runs Karmic perfectly, as it did with Jaunty and Intrepid.

What are others using?

---

### Post by nanog on 2010-04-30
see my comments here: 
[http://ubuntuforums.org/showthread.php?t=1358591](http://ubuntuforums.org/showthread.php?t=1358591)

---

### Post by singercs on 2010-04-30
I find that this is the same for me also, however I find that it shuts down very fast, hopefully the issue can be fixed so it can at least boot as fast as windows.

---

### Post by slamhound on 2010-04-30
For me, I had a long delay between login and usable desktop (30 seconds or so).  Disabling the floppy drive (a solution I saw in someone else's post) solved this problem; now it's almost instant.

Disabling in the bios, that is.

---

### Post by rjcroy on 2010-04-30
For me it has been faster than ever. I think it would be best to find something specific which is slowing it down, because I don't think 10.04 is universally slow to boot.

---

### Post by Lightstar on 2010-04-30
I'm on the same boat.
It boots really quick, but the wait time between the Login and the Desktop is way too slow, a whooping 30 seconds.

I hear the sound, and see my AWN dock and mouse pointer 3 seconds after login, but the rest of the desktop takes 30 secs to appear.

I will try disabling the floppy like I read in a post above.

---

### Post by Skyline969 on 2010-04-30
This I find weird now. Login is instant for me, but boot is what takes a long time.

---

### Post by Shadow12313 on 2010-04-30
I still have the hal package but, the speed seems very fast on my computer also core 2 duo.

---

### Post by Rob Strejc on 2010-04-30
> **slamhound said:**
> For me, I had a long delay between login and usable desktop (30 seconds or so).  Disabling the floppy drive (a solution I saw in someone else's post) solved this problem; now it's almost instant.

Disabling in the bios, that is.


I just wanted to confirm, disabling floppy in BIOS does actually reduce boot time substantially.  Though 10.04 seems a bit sluggish opening windows, and such.

---

### Post by mkrmec on 2010-04-30
> **slamhound said:**
> For me, I had a long delay between login and usable desktop (30 seconds or so).  Disabling the floppy drive (a solution I saw in someone else's post) solved this problem; now it's almost instant.

Disabling in the bios, that is.

Thnx that solved my long boot :D

---

### Post by Orographic on 2010-04-30
And the funny thing is that I just installed the Kbuntu version and it installs fast from log in on this same machine. I just don't like the package manager and the basic setup in Kbuntu. Its hard to use compared to Gnome.

Kbuntu installed perfectly on this machine and the live CD worked well but the Ubuntu one doesn't and its not a bad download or anything as I checked it thoroughly.

---

### Post by Orographic on 2010-04-30
Maybe I have and older lucid iso?

[http://www.phoronix.com/scan.php?page=news_item&px=ODE5Ng](http://www.phoronix.com/scan.php?page=news_item&px=ODE5Ng)

---

### Post by Orographic on 2010-05-01
Wow, disabling the floppy in BIOS has now taken my boot time from the log in screen to desktop to about three seconds instead of thirty! 

What a great tip!

Where is the thread that suggested that idea originally?

I still don't get any boot splash but man, the system boots very quickly now.

---

### Post by slamhound on 2010-05-01
I can't remember where I initially saw the tip; somewhere in the lucid development forum.  There wasn't much of an explanation, just the tip.  But it has worked on two of my computers (the others didn't have the problem).

---

### Post by Orographic on 2010-05-01
Its actually a bug report:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/567899](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/567899)

---

### Post by Zer0d on 2010-05-01
I can also confirm that disabling FDD in BIOS solved the slow login.

---

### Post by andyanderso on 2010-05-01
I have this same problem...System takes almost a full minute to boot. It gets hung on the "Boot from hd blah blah screen."  I tried the BIOS change but it did not work. It still takes about 50-55 seconds to boot.

Anyone else have any ideas?

---

### Post by Linuxforall on 2010-05-01
At least 8 seconds quicker than Karmic on my dual XEON PC here.

---

### Post by meldroc on 2010-05-01
Have the same issue - long boot times, in the minute range, on my laptop (Asus A8Js).  Can't disable the floppy in the BIOS because this laptop doesn't have a floppy, there's nothing in the BIOS setup to disable.

---

### Post by Orographic on 2010-05-01
That interesting meldroc,

My desktop doesn't have a floppy drive either, just a card reader in the floppy bay, which still works even though I disabled the floppy drive, I think.

Hope it works out for you.

---

### Post by andyanderso on 2010-05-01
meldroc - my system does not have a floppy controller either - but I read a solution to this problem during lynx development was to change the SATA settings in the BIOS. This did not work for me but maybe it will for you.

has anyone tried changing settings in grub?

---

### Post by meldroc on 2010-05-02
andyanderso: What SATA settings in the BIOS would you change?  I pretty much leave the BIOS alone - it does correctly autodetect my hard drive and DVD drive, sets them to the highest settings they're capable of, and for the most part, hasn't caused problems.

---

### Post by Lostsouls on 2010-05-03
Jup, disabeld floppy in the bios, now less then 5 sec from login to desktop, thanks for the tip

---

### Post by Mrs Twaddle on 2010-05-03
Mine is awfully slow too, disabled floppy, didn't seem to make any difference. I suspect mine is somehow associated to my fstab problem.

---

### Post by andyanderso on 2010-05-03
> **meldroc said:**
> andyanderso: What SATA settings in the BIOS would you change?  I pretty much leave the BIOS alone - it does correctly autodetect my hard drive and DVD drive, sets them to the highest settings they're capable of, and for the most part, hasn't caused problems.

In one of my BIOS pages in the SATA entry had two options: ATA and AHCI - neither of them helped solve this problem. 

I ended up trying a clean install. Now my boot times are around 30 secs...

---

### Post by dehrko on 2010-05-03
HOW TO FIX start up error in UBUNTU 10.4
pls need help
i upgrad from ubuntu 9.10 to 10.4 and found errror in boot fil 
i can't lon on system even i tryed recovery option as werll

---

### Post by Ravey on 2010-05-04
Disabling the FDD worked for me, thanks! :D

---

### Post by hyperlight7 on 2010-05-08
My Toshiba NB205 (netbook) had an option to disable AHCI. Besides trimming the boot time by 30 seconds, it also stopped giving up on the root device. Wish I knew why AHCI would be a problem...

---

### Post by m4tic on 2010-05-08
the splash is horrible, its resolution is the most horrible thing and its not in the centre, its just a small purple box with part of it missing on the bottom right and a dark void on the left area. I think boot screen similar to mandriva and open suse would be great. Also after it logged in, the panel takes another 20sec to appear, why i don't know. This race for fast boot sucks and isn't working at all.

---

### Post by rafaelpagliuca on 2010-05-08
Disabling Floppy Disk on BIOS worked for me as well. Now it doesn't take lots of seconds to login anymore.

---

### Post by EnricCirne on 2010-05-08
> **hyperlight7 said:**
> My Toshiba NB205 (netbook) had an option to disable AHCI. Besides trimming the boot time by 30 seconds, it also stopped giving up on the root device. Wish I knew why AHCI would be a problem...

If no one else has provided this.  I found the "HardwareSupport/Machines/Netbooks/ToshibaNB205" page, [https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks/ToshibaNB205](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks/ToshibaNB205) , solved my Toshiba netbook boot problem.  Particularly the part at the end, "Kernel Boot Fix".  On 10.04, just search for:

```
cat << EOF
        linux   ${rel_dirname}/${basename} root=${linux_root_device_thisversion} ro $2
```

since it's in a different location than described on the page.

This might also solve boot problem on other machines -- just speculating, haven't tested.

  -- Enric

---

### Post by scriptjamin on 2010-05-10
For me, Ubuntu 10.04 64 takes about 8 seconds to boot after post.

---

### Post by toddbmobile on 2010-05-11
Boots up quick, but when I click my name at login screen to enter my password it takes 15 to 20 seconds for the password box to appear below my name. Anyone have ideas on this? It delays me getting to the desktop.


MINE was a clean install, and my computer did not come with a floppy drive.

---

### Post by alphacrucis2 on 2010-05-11
I would be curious to know if the people suffering slow boot (apart from the FDD issue) did an upgrade rather than a clean install? On a Lenovo T400, boot to login prompt about 14 seconds. Login to usable desktop about three seconds. Considerably improved over Karmic. I did a fresh install to go from Karmic 32 to Lucid 64. I wonder if ureadahead doesn't work properly if you do an upgrade rather than a clean install.

---

### Post by meldroc on 2010-05-12
I did indeed do an upgrade rather than a clean install, alphacrucis2.  Maybe you're onto something.

---

### Post by slamhound on 2010-05-12
I have two systems with almost identical hardware.  One I upgraded, the other I did a fresh install on an ssd (though I kept my /home partition which had been on a separate disk).  Both had the slow login problem that was resolved by disabling the floppy in the bios.  However, once that was done, they are both fast to boot.  The ssd system feels a bit faster (I haven't used bootchart), but both are very fast to boot.

---

### Post by zidarsk8 on 2010-05-12
> **andyanderso said:**
> I have this same problem...System takes almost a full minute to boot. It gets hung on the "Boot from hd blah blah screen."  I tried the BIOS change but it did not work. It still takes about 50-55 seconds to boot.

Anyone else have any ideas?
yup .. i have the same issue .. and i've tried disabling almost everything in bios, but i have no floppy on my laptop so there is not disable floppy option there.

can someone please help.

---

### Post by chek2fire on 2010-05-12
I have the same problem with too long boot time in my dell inspiron 1011 netbook. I have install the netbook remix edition. I cant disable floppy because this netbook has no floppy. The boot time is about 30 seconds!! Is weird for a netbook and from canonical patern to do so much boot time.

---

### Post by warfacegod on 2010-05-12
I would start by going to System> Prefs.> Startup Apps. and disabling everything doesn't need to start on boot. I'll take a wild guess and say that Ubuntu One could be one of the main culprits. Last time I checked it out, its start time was atrocious.

---

### Post by migs73 on 2010-05-12
From me pressing the start button on my Dell Inspiron 1501 to my desktop (with login disabled) takes 68s.
The BIOS options are limited with this machine and there is no floppy to disable anyway (not even on boot list). I dropped as much as I dared from the start-up apps (including Ubuntuone) and this shaved a whopping 4 seconds :confused: off my boot time (now 64s). The BIOS takes the first 17s so I can ignore that and the 3s pause you get from grub to enable you to enter it. That still leaves 44s for boot. I may be getting greedy if i would like it shorter (takes nearly 3 mins to boot into Vista on same machine!!).
There are a couple of other notable things about this Laptop.
1) It has the PAE kernel (I have 4Gb RAM on a 32 bit machine) but it was much the same on the generic kernel.
2)I DID AN UPGRADE FROM KARMIC. I may try a clean install soon and see if it helps.

---

### Post by sarin_cv on 2010-05-12
for me it takes 32 seconds to boot... autologin is enabled for me... I have a pretty good configuration... I have installed lucis beta1 and updated to LTS.... someone please check my bootchart... I don't understand anything frm it...
[COLOR=black][FONT=&quot]
[http://picasaweb.google.com/sarincv/...82226442974098]("http://picasaweb.google.com/sarincv/Downloads#5467982226442974098")[/FONT][/COLOR]

---

### Post by SeanBlader on 2010-05-12
> **sarin_cv said:**
> for me it takes 32 seconds to boot... autologin is enabled for me... I have a pretty good configuration... I have installed lucis beta1 and updated to LTS.... someone please check my bootchart... I don't understand anything frm it...
[COLOR=black][FONT=&quot]
[http://picasaweb.google.com/sarincv/...82226442974098]("http://picasaweb.google.com/sarincv/Downloads#5467982226442974098")[/FONT][/COLOR]

Sarin, it looks like you have a bunch of Windows NTFS partitions mounting at boot. I bet that's what's slowing you down. Do you use them every time you are in linux? Try unmounting them and restarting and see if that helps.

Also is that the first boot after an update of some sort? It doesn't look like ureadahead is working properly.

And, it also looks like there's a lot of duplicates, is that a fresh install, or an upgrade? What I recommend is definitely having your /home folder on it's own partition, then you can format a much smaller OS partition with the rest of the folders every time you install a new Ubuntu. Since all your settings are saved in your home folder anyway, you'll boot every time to an interface that you recognize. I take about 2 hours now to setup a new Ubuntu every time there's a release candidate, and then I'm back to working with an all new and fresh operating system that still only has 1 gnome panel and all me previous OS settings, it's very efficient.

---

### Post by migs73 on 2010-05-12
Sean
Before I went to do my fresh install, I wanted to check the best way to do it (see my post here [http://ubuntuforums.org/showthread.php?p=9286690#post9286690](http://ubuntuforums.org/showthread.php?p=9286690#post9286690))
What do you think?
Also where do I get the boot info? I'll post it here to see if it makes any sense as to why my boot is so slow.

---

### Post by SeanBlader on 2010-05-13
The boot info is from boot chart, I'm not even sure how to get more details or turn off some of them, but unless you have really old hardware it should boot faster. And I was just comparing Saris's to mine, and I noticed that he had those really long NTFS lines, and I remember reading somewhere that mounting takes up time in your boot sequence.

---

### Post by sarin_cv on 2010-05-13
> **SeanBlader said:**
> Sarin, it looks like you have a bunch of Windows NTFS partitions mounting at boot. I bet that's what's slowing you down. Do you use them every time you are in linux? Try unmounting them and restarting and see if that helps.

Also is that the first boot after an update of some sort? It doesn't look like ureadahead is working properly.

And, it also looks like there's a lot of duplicates, is that a fresh install, or an upgrade? What I recommend is definitely having your /home folder on it's own partition, then you can format a much smaller OS partition with the rest of the folders every time you install a new Ubuntu. Since all your settings are saved in your home folder anyway, you'll boot every time to an interface that you recognize. I take about 2 hours now to setup a new Ubuntu every time there's a release candidate, and then I'm back to working with an all new and fresh operating system that still only has 1 gnome panel and all me previous OS settings, it's very efficient.

Yes...I use those partitions everytime... but I will try disabling auto mounting... secondly, it is not the first boot after update... beta 1 was a fresh install and then i updated to LTS... home folder is having it's own partition of 10 GB... root is also 10 GB...

---

### Post by N_L on 2010-05-13
My problem is that it hangs at black screen with _ for long time after I select right kernel.

---

### Post by migs73 on 2010-05-13
Still can't find a boot chart, but here is the last 20s or so of output from my 'messages' on my system log from last boot;

May 13 14:47:31 dell-laptop kernel: [   26.337285] type=1505 audit(1273758451.128:5):  operation="profile_load" pid=936 name="/usr/share/gdm/guest-session/Xsession"
May 13 14:47:31 dell-laptop kernel: [   26.341748] type=1505 audit(1273758451.132:6):  operation="profile_replace" pid=937 name="/sbin/dhclient3"
May 13 14:47:31 dell-laptop kernel: [   26.342079] type=1505 audit(1273758451.132:7):  operation="profile_replace" pid=937 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
May 13 14:47:31 dell-laptop kernel: [   26.342263] type=1505 audit(1273758451.132:8):  operation="profile_replace" pid=937 name="/usr/lib/connman/scripts/dhclient-script"
May 13 14:47:31 dell-laptop kernel: [   26.351821] type=1505 audit(1273758451.140:9):  operation="profile_load" pid=938 name="/usr/bin/evince"
May 13 14:47:31 dell-laptop kernel: [   26.356784] type=1505 audit(1273758451.148:10):  operation="profile_load" pid=938 name="/usr/bin/evince-previewer"
May 13 14:47:31 dell-laptop kernel: [   26.359362] type=1505 audit(1273758451.148:11):  operation="profile_load" pid=938 name="/usr/bin/evince-thumbnailer"
May 13 14:47:31 dell-laptop kernel: [   26.566207] composite sync not supported
May 13 14:47:31 dell-laptop kernel: [   26.602392] composite sync not supported
May 13 14:47:31 dell-laptop kernel: [   26.698153] apm: BIOS not found.
May 13 14:47:32 dell-laptop kernel: [   27.717995] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
May 13 14:47:32 dell-laptop kernel: [   28.081899] composite sync not supported
May 13 14:47:32 dell-laptop kernel: [   28.111310] composite sync not supported
May 13 14:47:32 dell-laptop kernel: [   28.158633] composite sync not supported
May 13 14:47:32 dell-laptop kernel: [   28.183939] ppdev: user-space parallel port driver
May 13 14:47:45 dell-laptop kernel: [   40.690293] padlock: VIA PadLock not detected.
May 13 14:47:48 dell-laptop kernel: [   43.395832] composite sync not supported
May 13 14:47:48 dell-laptop kernel: [   43.425953] composite sync not supported
May 13 14:47:48 dell-laptop kernel: [   43.451387] composite sync not supported
May 13 14:47:49 dell-laptop kernel: [   44.931858] composite sync not supported
May 13 14:47:54 dell-laptop kernel: [   50.012111] composite sync not supported


Note there is a 13s gap after 'ppdev: user-space' to 'padlock: VIA PadLock' and then 10s of 'composite sync not supported' entries.
Most of the stuff previous to this happens concurrently with no gaps in the timestamp.
Can anybody help??

---

### Post by sarin_cv on 2010-05-13
> **sarin_cv said:**
> Yes...I use those partitions everytime... but I will try disabling auto mounting... secondly, it is not the first boot after update... beta 1 was a fresh install and then i updated to LTS... home folder is having it's own partition of 10 GB... root is also 10 GB...

I removed automounting from /etc/fstab and tried booting several times... still the same issue...then I did a fresh install and now the boot time is reduced to 25 seconds.... but is that it?

---

### Post by migs73 on 2010-05-14
I have just finished a clean install,with a separate /home partition, and my boot time has dropped from 1min 8s to 45s from pushing the on button. The first 15-17s of this is BIOS time anyway so Ubuntu boot time about 25-30s.
Clean install seems to be the way.

---

### Post by pszpak on 2010-05-15
I had this problem and disabled my floppy drive in the BIOS like posters in this thread suggested. I went from a 20 second wait after entering my name and password to less than 3 seconds. 

I also commented out the floppy in fstab, but this had no effect on login times.

I'm on 10.04 using amd64.

---

### Post by camdude on 2010-05-15
My logon is instant, yet my boot is a little on the slow side. However, NO TEXT should appear at all, as Ubuntu now has a non-interactive boot up (unless you press a key when it first starts booting)...

---

### Post by ktechman on 2010-05-20
Disabled Floppy in the Bios and now from log-in to desktop went from 21 seconds to 3 seconds.  


Ktechman

---

### Post by Kilz on 2010-05-22
Great thread, I would have never thought disabling the non existent floppy in the bios would help.

---

### Post by marcusklaas on 2010-05-25
Yes very good thread.. but stupid that this bug hasn't been resolved yet.. Normally it wouldn't take that long to boot, but now that I disabled floppy it was like lightning fast in comparison. Thanks!

---

### Post by perspectoff on 2010-05-25
> **Skyline969 said:**
> This I find weird now. Login is instant for me, but boot is what takes a long time.

Probably has to do with Plymouth, the non-functional bootup screen they attempted to port from Red Hat.

When it's working, bootup is quick. When it's not, it takes forever. Since it doesn't work on any of my computers, they all loadup more slowly than Karmic.

---

### Post by meldroc on 2010-05-27
I haven't been focusing much effort on my bootup time issues.  I'd love to have 3-second bootups on my laptop, but as I currently stand, my laptop goes from cold-power-up to a working desktop in just over a minute, which isn't bad.  And the time from login at gdm to desktop is very quick - like a couple seconds.  It's the Plymouth splash screen that takes longer than it ought to, but not so long that I find it too horribly annoying - that's worth about 30 seconds on my system.

I did improve the appearance of the Plymouth splash screen on my system using the framebuffer hack (my laptop has an Nvidia GPU in it), so it displays at 1024x768, which doesn't look horrible.  It would be nice if I could get it to display at my laptop's native 1440x900, but the BIOS doesn't recognize that mode, so it's not accessible from GRUB or the framebuffer driver.  I have to wait until Xorg fires up with the Nvidia driver before it switches to that mode.

---

### Post by DividerOfZero on 2010-05-29
The FDD BIOS disable worked for me to fix the slow login>desktop time. Now I just need to fix the random mouse/keyboard freeze that occurs...:confused:

---

### Post by Burfee on 2010-06-17
the disable FDD solution did the trick on my desktop but i don't have the option in my laptop's BIOS.

Can someone please tell us, the ones with laptops without this option in the BIOS, what else can we do, please?

---

### Post by NonMSman on 2010-06-21
You guys might want to try Karmic Koala  which is Ubuntu 9.10.  

I recommend it to everyone.  ( 10.04 )  Is way too slow, the GUI is all Mac-ed up, and every single person that loads it has endless situations causing extreme pain.

I told all my clients to avoid the 10.04 upgrade at all costs.  One of my first clients that did upgrade had to fix his problem with FDISK.  Karmic Koala is still being supported, so there is no valid reason to upgrade to 10.04.   

Almost every user that does wishes they had not done so.  If my clients do UPGRADE I siimply tell them they are on their own.  That or call an apple guy.  Meanwhile Karmic Koala is still outperforming 10.04 in almost all fronts.  10.04 is kind of like Canoical's version of Vista !  The big engine that couldn't...  

Give em a break.  Wait for version 11.??.  They made a boo boo.  Its going to take a while before they fix it.  If they don't then see ya at the Debian forums .
:lolflag:

---

### Post by howefield on 2010-06-25
> **NonMSman said:**
> and every single person that loads it has endless situations causing extreme pain.

You must have a source for this gem ?

You can't assume that everyone who loads a particular OS has "endless situations causing extreme pain" purely based on your experience(s).


:lolflag::lolflag:

---

### Post by linuxhippy on 2010-06-26
I've been very impressed with XUbuntu 10.04's boot up speed.  I'm running an Athlon 64 desktop that's 3 years old and doesn't have a floppy drive (this setting is also disabled in the BIOS).  Here are my times:

Grub2 screen to login: [COLOR="Red"]18 seconds[/COLOR]
login to CPU load = 0: [COLOR="Red"]9 seconds
[/COLOR]


I've used XFCE for years with different distros and this seems to be the most powerful OS with speed.  I downloaded the Ubuntu 10.04 CD and then did a fresh install on one partition (not including swap) and then used aptitude to install XUbuntu:

sudo aptitude install xubuntu-desktop

---

### Post by XSAlliN on 2010-06-26
XFCE is not an OS, it's a GUI like Gnome, KDE, LXDE, etc... closer to Gnome in looks but targets the performance approach, same as LXDE is closer to KDE and has same target. So yeh, XFCE and LXDE outperforms the other two in any way... not just boot but also a general performance boot, without even applying extra tweaks. You might say, they're the Classic/Basic version from Windows - yet not that ugly... :) 

I still like Gnome best + extra performance tweaks, even being a slower approach - which is to be expected, but I also care about looks.

---

### Post by linuxhippy on 2010-06-26
> **XSAlliN said:**
> XFCE is not an OS

You misunderstood...XUbuntu is just Ubuntu with some tweaks to make it behave faster since it has XFCE desktop which is faster after login to desktop to start than GNOME.  The other OS I was talking about was Fedora XFCE spin.  This version of Fedora runs XFCE but takes longer to boot than XUbuntu.  I didn't want to mention names but now I have.

---


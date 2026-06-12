---
title: "It won't go away!!"
date: 2009-12-22
forum: General Help
---

### Post by benmode on 2009-12-22
I was using Vista on my HP G70 laptop, I bought some recording equipment and started using pro tools LE but it was slow as crap. I'm pretty sure this laptop should be able to handle it so I blamed vista. 
I installed ubuntu, It's pretty cool but I can't properly install pro tools on it, so now I wanna try XP.

the problem is ubuntu seems to have taken over for good! My XP disc doesnt work at all, ubuntu just boots like normal as if there's no disc. I tried making new XP discs and they just lead to a black screen for a while, followed by a blue error screen. 

I've tried searching for help but with no luck. most people are having problems with booting into windows, but I completely erased windows when i installed ubuntu.

 I tried to learn about grub, tried fiddling about with a super grub disk, not really knowing what i was doing. i may have made things worse for myself. haha.

anyway, i'd really appreciate some help with getting rid of ubuntu, i've spent days on this now and im getting really stressed.

---

### Post by synapsys on 2009-12-22
Ubuntu has nothing to do with your computers ability to boot from a cd. This happens before grub, and is done with the bios. Are you using a valid (legal) xp disc? Also, is your bios set to boot from cd and not hard drive?

---

### Post by s.fox on 2009-12-22
Hello.

Can you please confirm you are changing the BIOS so that your computer boots from cd?

Thank you.

-Silver Fox

---

### Post by audiomick on 2009-12-22
hi.

First thing, the cd drive must be enabled as a boot device ( BIOS option ), but I think yours is if you are getting a black screen and errors.

maybe you have to re-format first. I don't know how a windows installer reacts to a HD that is formatted for Linux, but I can imagine it wouldn't be happy. Boot into the Ubuntu live cd, system> administration> gparted to open the partitioning tool. Remove all the linux partitions and make an ntfs one.

I know that pro tools is the standard programm, but have you looked at ardour?
[http://en.wikipedia.org/wiki/Ardour_%28audio_processor%29](http://en.wikipedia.org/wiki/Ardour_%28audio_processor%29)

If is available from the Ubuntu repositories via synaptic package manager

---

### Post by 73ckn797 on 2009-12-22
If you are trying to install a Windows program straight into Ubuntu, it will not work. You would have to install Wine or a virtual machine. I do not know whether Pro Tools would work in Wine. You would have to install VirtualBox and then install Windows into it. You could then load Pro Tools.

The BIOS setting, as mentioned, will allow booting from a CD.

---

### Post by audiomick on 2009-12-22
> **73ckn797 said:**
> I do not know whether Pro Tools would work in Wine.
I doubt it very much

>  You would have to install VirtualBox and then install Windows into it. You could then load Pro Tools.

True, but it would have to be a fast machine, and I think that latency would be a big issue doing live recording, not to mention getting audio interfaces to work properly.

Like I said, look at ardour.

---

### Post by 73ckn797 on 2009-12-23
> **audiomick said:**
> I doubt it very much



True, but it would have to be a fast machine, and I think that latency would be a big issue doing live recording, not to mention getting audio interfaces to work properly.

Like I said, look at ardour.

Agreed. I was pointing out, what I felt was, the obvious that had not been mentioned.

---

### Post by benmode on 2009-12-23
Hi thanks for all the swift replies. 
 
I have my BIOS set to boot from the cd.
I just tried removing the linux partitions in GParted and created an NTFS one, still the XP disc wont work! It is a disc i've used before and it works fine on my other computers.
 
What I'm getting now is a black screen with:

GRUB loading.
erroe: no such partition
grub rescue>
 
ugggg. anymore suggestions?
 
I've had a look at Arour, I couldn't get my M-box2 to work with it. There might be a way of doing that but I'd really rather just go back to windows. there are loads of other programs i use (sibelius, auralia, reason, guitar pro...) that wont work in ubuntu and i dont wanna switch to the free stuff.

---

### Post by audiomick on 2009-12-23
> **benmode said:**
> 
GRUB loading.
erroe: no such partition
grub rescue>
 

Whatever the reason is, it is not reading the CD...:confused:

Does the CD drive show any signs of life at all?

---

### Post by benmode on 2009-12-23
Yeah it does, you can hear it spinning like crap, the ubuntu cd works properly still too. 
I tried a different XP disc meant for dell computers, that gets alot further but still doesnt work. no luck with windows 98 disc either. BLEHHHH!
 
Right now the only partitions i have are /dev/sda1 140GB ntfs and some "unallocated" 9GB one.
is there anything else i need to do in GParted?

---

### Post by mikem94590 on 2009-12-23
Ignoring the fact that you can likely get Ubuntu to work for you via means of emulation (WINE, CrossOver, VirtualBox, etc.), you should be able to boot to your WinXP CD simply by placing it in the CD drive and restarting.

I had a friend who had this problem once, and this is what he did;

[LIST=1]
[*]Put XP CD in drive.
[*]Completely turn off the computer
[*]Turn on the computer and boot into your BIOS config menu
[*]Wait a few moments
[*]Use your BIOS option to "quit saving changes" or whatever, and "save changes"
While you won't make any changes by doing this, it will have spun the CD, and the BIOS will not completely restart the computer when you restart.
[*]You should boot into your XP CD.
[/LIST]
You could always grab an ISO for GParted and delete your Ubuntu partition, but I doubt that that would do anything, and you'd have the same problem, just without the ability to boot into any operating system.

---

### Post by egalvan on 2009-12-23
first, I'd like to reiterate the point that *synapsys* made:
Ubuntu has nothing to do with the machine not booting the XP CD.

Second, if I was trying to fix this problem, this is what I would do...

First, run "check media" from the Ubuntu LiveCD...
if this passes OK, then

Second, run "memtest" from that same LiveCD.
if this passes OK, then

Third, boot dban (Darik's Boot and Nuke) to TOTALLY ERASE the drive.
This will leave your machine in a clean state.

If all of these tests go well, and that Dell XP CD still does not work,
then I am stumped. (Those Dell re-install CD's are what I use on all my Dell stuff, they work great.)

but personally, I think MS Windows is getting snitty when it sees partitions it doesn't approve of...
 I've had this problem, which is why I use dban 

"Let's nuke the whole installation from orbit, it's the only way to be sure" -- Cpl Hicks.

---

### Post by egalvan on 2009-12-23
and take a look at Ubuntu Studio, a distro aimed at audio/video professionals.

---

### Post by rfrayer on 2009-12-23
Ive had this problem with other linux distros the solution is to plop in the livecd and totally whipe out the disk any and all partitions.

that is if your totally reverting back to xp.

> **benmode said:**
> I was using Vista on my HP G70 laptop, I bought some recording equipment and started using pro tools LE but it was slow as crap. I'm pretty sure this laptop should be able to handle it so I blamed vista. 
I installed ubuntu, It's pretty cool but I can't properly install pro tools on it, so now I wanna try XP.

the problem is ubuntu seems to have taken over for good! My XP disc doesnt work at all, ubuntu just boots like normal as if there's no disc. I tried making new XP discs and they just lead to a black screen for a while, followed by a blue error screen. 

I've tried searching for help but with no luck. most people are having problems with booting into windows, but I completely erased windows when i installed ubuntu.

 I tried to learn about grub, tried fiddling about with a super grub disk, not really knowing what i was doing. i may have made things worse for myself. haha.

anyway, i'd really appreciate some help with getting rid of ubuntu, i've spent days on this now and im getting really stressed.

---

### Post by rfrayer on 2009-12-23
oh and word of advice. Id keep ubuntu and install vmware workstation with xp on that.

---

### Post by benmode on 2009-12-23
sorry im not interested in ubuntu studio. I've tried using wine to install pro tools LE, but not the others. I havent read about anyone successfully installing pro tools in ubuntu though.
 
I've tried wiping the partitions in GParted, Tried wiping the entire hdd with Killdisk and then Dban. 
Still no luck so far!
I also tried creating an NTFS partition in GParted. 
the XP cds are still having problems, but i've put XP on a USB device and I can get a bit further now. It gives me two options - GUI mode XP setup or TXT mode.
 
when i select GUI mode (whatever that means! :S) it tells me this:
 
Windows could not start because the following file is missing or corrupt:
<Windows root>\system32\hal.dll.
Please re-install a copy of the above file.
 
... eh?
 
when i select TXT mode it goes to the blue screen tricking me into thinking it's working, but then it just stops at the BSOD telling me to try CHKDSK /F. 
 
I feel like I'm getting closer! haha. not quite there though. perhaps I should try someone else's XP discs?

---

### Post by jmore9 on 2009-12-23
I have found in the past that a copy of g[arted live , it is on its own cd, works just fine.

Just boot into the cd it auto loads and you do your partitioning as you wish.

Has options for ntfs,fat32, ext 3, etc

On a really stubborn drive i resort to the hard drives manufactures formating utility.

Hope some of the above helps

---

### Post by benmode on 2009-12-23
so the gparted live cd works better than using gparted through the ubuntu cd? it looked like gparted was working fine through the ubuntu cd. :S maybe it was lying to me haha.
 
the hard drive manufacturers formatting utility? hmm...
 
[http://www.softpedia.com/get/System/Hard-Disk-Utils/HDD-Low-Level-Format-Tool.shtml](http://www.softpedia.com/get/System/Hard-Disk-Utils/HDD-Low-Level-Format-Tool.shtml)
 
you reckon that could help me out? i really have no idea what's going on.

---

### Post by jSalv on 2009-12-23
If you really want to get rid of Ubuntu, then just format.
Then, enable the BIOS to boot from the cd (usually It's pretty F2 or DELETE whilst computer is booting up), then exit the BIOS saving changes (this should re-reboot your computer).

If XP doesn't work, it may be because your computer is too new and the HD is in a mode XP doesn't support.
You should check in the BIOS if you HDD mode is set to AHCI, and, in case it is, change it to IDE. This was the thing that last time kept me all night wondering.

If you still have problems after doing all of this, you are using a legal XP disc, and have formatted the HD, post again.

---

### Post by historyb on 2009-12-23
Hi,

I know this may sound simple but on my XP you must hit any key so it will boot from the CD, just a thought

---

### Post by ST3ALTHPSYCH0 on 2009-12-23
Have you tried deleting all partitions and then making a new partition with Fdisk on the XP disc? I installed win 98 last weekend and it absolutely wouldn't install on a partition created with Gparted (even with out cylinder rounding). Boot to command prompt with the XP disc and run Fdisk. Create a new primary partition and make it active. Reboot, and format from setup.

---


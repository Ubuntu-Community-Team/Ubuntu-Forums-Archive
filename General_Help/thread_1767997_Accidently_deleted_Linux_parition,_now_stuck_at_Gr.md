---
title: "Accidently deleted Linux parition, now stuck at Grub Rescue..."
date: 2011-05-26
forum: General Help
---

### Post by Suitsuke on 2011-05-26
Long and rediclously frustrating story short..

Deleted the Ubuntu partition by accident. Now at a loss as how to get Windows working again. I had all my files saved, and did a full format and reinstall to Windows. Thinking that it would just overwrite grub but this thing is like a virus.. I cant do **** at the grub rescure command prompt... it just sits there with a cursor... Even stuff like reboot and quit or exit don't even work... what the hell?

So I pop my Win7 install cd in and I find that for some reason I have no recovery console... just the option to install. I install but no grub, the little virus is still there and I just wasted an hour of my life while Win7 installed again because I still cant view it.

I deleted all the partitions and wiped the entire disc and grub is still there.. I was thinking that Windows would just replace grub automatically. Heh the Bootsector always seems to get owned on Windows and I expected grub to be just as useless but in it's own way, it's worse.

TL;DR

Please for the love of god someone tell me a really quick easy way to delete this bootloader and restore the Windows one so I can actually boot Windows now! I wish to be free of Linux, it was good while it lasted but oh my god this is rediculous!

EDIT: Oh and I cant get on the internet on Ubuntu, for some stupid reason it uses Roaming which has already cost me 65&#8364; over my normal phone limit.. I am at a loss as to how I will pay that but there has to be another way like removing the loader so it can be replaced with the Windows one.

---

### Post by wojox on 2011-05-26
Boot a live Linux CD and mount the HDD and open a terminal and run this:

```
sudo dd if=/dev/zero of=/dev/sda count=1 bs=446
``` 

That will wipe out your MBR. Then install Windows.

---

### Post by Suitsuke on 2011-05-26
Done.

Rebooted, Looks like Grub is toast.

Thanks a ton. I suggest in the next Distro to include that somewhere extremely obvious...

Thanks again, hopefuly a Windows 7 install now will be sucessful.

---

### Post by Suitsuke on 2011-05-26
Install wasn't sucessful. Now I just get the error after a Windows install:

*'A bootable device was not found, insert a bootable device and press any key...'*

What the hell am I supposed to do now? So now I have no Grub and Windows hasn't installed it's bootloader? What the... what's going on??!

---

### Post by oldfred on 2011-05-26
Your windows install should have created a NTFS primary partition with the boot flag. Some BIOS will not let you start booting without a boot flag on a primary partition.

---

### Post by Suitsuke on 2011-05-26
I booted back into Linux off a USB and it tells me that my NTFS parition is misaligned by 512 bytes and that it could drastically decrease system performance. Never seen an error like this before in my life.

Now doing an extended check for errors... I have no idea what's going on. S.M.A.R.T. status reports not a single error with the drive. All readings are 0 for every sort of error... the disc has only been powered on for a total of 14.3 days and it's only a month old... What could be happening?

Doing a Windows install didn't write a bootloader and I'm getting the same error all the time. About to try an old Vista disc just to see if that will boot or if I am having a failure somewhere or something. Ubuntu isn't complaining about anything except that misalignment. No matter how I format my WD7500BPKT it tells me the parition is misaligned.. any way I can fix this? Could this be the problem, that the first 512 bytes are misaligned and that means my bootsector is messed up?

This seems to be an issue because my drive is 'Advanced Format' there never was a problem before.. I deleted the entire parition back to inactive status so it has no MBR, GUID, or whatever. It's got nothing except it being formatted into NTFS and it's entirely clean.. should I try a Windows install now? Or because the device isn't paritioned with MBR will it just fail again? The warning message is gone now. After trying to format with an MBR it came back again so I put it back to how I just described it. No MBR etc, just NTFS formatted with no Master Boot Record. Will Windows make one?

---

### Post by oldfred on 2011-05-26
All the new installs start at sector 2048. Old installs of XP & Linux started the first partition at sector 63. What sector is your NTFS partition starting at.

Post this from liveCD.

sudo fdisk -lu

---

### Post by Suitsuke on 2011-05-26
[IMG]http://i904.photobucket.com/albums/ac244/Zeptinune/DSC03094.jpg[/IMG]

As you can see from this picture this is now the state of my drive. I have no idea what the hell is going on.. the drive is barely a month old. It's brand new and it's been powered on for a total of 14 days. I've never seen anything like this in 20 years of computing.

This is so confusing and frustrating... the S.M.A.R.T data on my drive is all Healthy with no errors at all. An error scan on Ubuntu came up with nothing either.. On Windows when I connect the drive to my other laptop via a 2.5" caddy the Partition Aligning Software from Western Digital says that the drive is 'Optimally Alligned' meaning that there is no problems with partition or byte alignment..

I will run that command on Linux. ( I have to plug the drive back into the computer again ). But I have no idea what I could do.. is my computer now broken or is my hard drive failing or is my boot sector a mess? I've tried a 'bootsect /nt60 C:' command on a Windows recovery CD to try and fix the bootsector. I've tried multiple deletes, formats and remounts on the drive to see if I can clear this error but it seems to get even more complicated the futher in I go...

I'm starting to freak out really... I don't want to send this drive to WD in Thailand to have it replaced when it's brand new.. I just want my Windows back. I cant believe this can all happen just from accidently deleting a Linux partition...

What do I do?

---

### Post by oldfred on 2011-05-26
Is the error this?

/dev/sdc5       209134233   259926015    25390732   83  Linux
Warning: Partition 5 does not end on cylinder boundary.

The above error does not mean anything with LBA. Cylinders have not been used on hard drives since LBA was implemented when drives exceeded 8GB. Back in those days I had to enter cylinders, heads, sectors from drive into BIOS to configure drive.

---

### Post by wojox on 2011-05-26
After you wiped out the MBR you did a fresh install of Windows?

---

### Post by Thewhistlingwind on 2011-05-26
You sound like you've got nothing to lose.

([http://sourceforge.net/projects/dban/](http://sourceforge.net/projects/dban/))

Zero it out.

 EDIT: (Warning: In case it wasn't obvious, this will goopify your data (theoretically) beyond the point of forensic recovery if you use anything stronger then the "zero" option. And the zero option itself wipes the disk.)

---

### Post by silex89 on 2011-05-26
Check out the hard drive on the BIOS, maybe the hardware configuration is messed up there....

---

### Post by Suitsuke on 2011-05-27
My bios is locked up like a fortress... I only have 4 options I can do..

I did a full fresh installation with my Acer Backup discs that I made with the backup program straight after I did the 'dd' erase Bootsector command from my Live Linux CD. After the Windows install it came up with this.

I'm now thinking that I'll probably use either Dban yeah to completely zero out the drive in the hopes that it will nullify any sort of corruption or problem it has and at least tell me that the whole drive is still ok. Or I will do the highest level 'dd' command and wipe the bootsector AND the partition table. Then do a reinstall of Windows.

When I put another drive in the machine it boots up like normal.. No problems at all. When I put another one without an OS in it, I just get the generic 'No boot disk found' etc. error. So It's definitely the drive. I'd say that the first few bytes are completely messed up and have a mixture of Windows and Grub on them or at least a mangled Windows one. I'll try the 'dd' command and then I'll try zeroing it.. if that doesn't work the WD in Thailand have offered to send me a new one now on the faith that I will send this one back to them so they can nuke it, refurbish it and sell it again.

Man this has not been my week...

---

### Post by linuxinstalledfromhdd on 2011-05-27
You can also boot from a live disc of Ubuntu, and use gparted to wipe your hard drive and wipe the MBR, and you can also try installing Ubuntu again from a disc, or reboot into a windows installation disc.  Boot from either a live USB stick of Ubuntu, or a live disc.

---

### Post by Suitsuke on 2011-05-27
I've tried installing Windows 7 from a USB, Xp gives me the 'ACPI' BSOD, because it only works on IDE mode. Vista and Win 7 both have the same problem that they don't write a bootloader for me...

A mate of mine suggested that the reason my bootloader has turned to dust is because I may have used a 32bit Disc to write a bootloader in the recovery console for my 64bit install. He stated that in the past when he's mixed and matched x86 and x64 that he gets jibberish messages or blank messages.

I'm about to try the 'dd' command but I'll need to find it on google first.

If gParted comes on the livecd I'll use that, I didn't know that it had it. :o I was using Disk utility.

---

### Post by linuxinstalledfromhdd on 2011-05-27
I don't know if it does or doesn't come pre-installed anymore.

Just in case it doesn't write this down.

sudo apt-get install gparted

As for your Windows USB, I can't help you there.  I have never used a Windows USB stick. 

I have wiped a harddrive that has had this problem before. I used gparted to wipe the MBR, and the entire disc. Be patient with it while it works.

---

### Post by Suitsuke on 2011-05-27
EDIT: Gparted showed 1 partition NTFS and I deleted it and remade it as  an NTFS. Though no matter what I do on it, it still leaves 1MiB in front  of whatever I format it as... Disk Utility shows the drive as  paritioned with an 'Unknown Scheme' and is no longer complaining about  it being off alignment.

The hard drive also seems to make a pretty hard click every now and then... I think it's on it's way out :'( maybe I just better send it back and use Linux for now...

---

### Post by linuxinstalledfromhdd on 2011-05-27
Remove everything. Click on "Device" and Create Partition Table.  After that you can install Ubuntu again or you try rebooting from your Windows USB.

---

### Post by Suitsuke on 2011-05-27
Ok after doing ONLY a Format MBR with Disk Utility and then a full paritioning with gParted the laptop boots up with just a flashing cursor.. no idea if this is an improvement or not.. but it's not giving me the jibberish message anymore. But it's not giving me the 'No Boot device message' either..

The drive has since made 3 what seems to be 'stalling' or loud clicking sounds in the past 15 minutes.. so now I am conflicted as to whether it should be sent back or whether I should keep it and try another install... as it may work now... I don't want it to blow up on me in 6 months when I should have sent it back now..

---

### Post by linuxinstalledfromhdd on 2011-05-27
Sounds like "stiction" physical noise?  If it is desktop computer, remove the cover and try to listen very carefully to the sound it is making.  If it is a laptop, you need to put your ear on it.  You can youtube for stiction demos so you can know what this sounds like in case you are in doubt.

---

### Post by Suitsuke on 2011-05-27
Here's my S.M.A.R.T. data. I haven't reinstalled Windows yet. Still getting the blinking cursor, nothing else.

The drive has made 2 more loud clicks now... for a total of at least 5.

```
http://i54.tinypic.com/2q02frm.png
http://i53.tinypic.com/23sgoq1.png
http://i55.tinypic.com/2koqdl.png
```

I think I'll send it back... it's a free new Drive. I only have to wait probably 7 full working days.. so 1 and a bit weeks.
I've emailed WD and told them I want to send the drive back, they stated they'd send me a new one as long as I sent the defect one back so they could fix it. It's 10 or so days to wait... or 12 or so. When I bought it in the first place I got it in less than half the time I expected.

The opportunity of a new drive with no fuss is hard to turn up. The lack of computer will probably be good for my health anyway. I'll use a persistent Linux USB to run my computer for now.

Thanks a ton for all the help.. I guess in the end if it's just easier and there's no fuss to send the drive back and get a replacement then that's the best way to go...

---

### Post by linuxinstalledfromhdd on 2011-05-27
Report to them you are having a Stiction issue on tech support, and start a trouble ticket with them so you can Return to Vendor RTV the unit.

---

### Post by Suitsuke on 2011-05-27
Am I going to get a new one if I do that?

---


---
title: "Guide for flashing/updating bios on Acer laptop using Linux?"
date: 2012-01-20
forum: General Help
---

### Post by gaz2011 on 2012-01-20
Hi,
  I'm a real newbie here that needs help. I have an Acer 4820T laptop. I'm looking for help on flashing/updating my bios through ubuntu 11.10. as the battery isn't being recognised at all. I don't have windows anymore so I can't do it through that unfortunately. Would any1 have a step by step for it? I would really appreciate it. Thanks

---

### Post by carl4926 on 2012-01-20
You really need to read the manual for your motherboard to see what option are available

---

### Post by dcstar on 2012-01-20
> **gaz2011 said:**
> Hi,
  I'm a real newbie here that needs help. I have an Acer 4820T laptop. I'm looking for help on flashing/updating my bios through ubuntu 11.10. as the battery isn't being recognised at all. I don't have windows anymore so I can't do it through that unfortunately. Would any1 have a step by step for it? I would really appreciate it. Thanks

If you can get an actual BIOS image file then there are utilities in Synaptic that ***might*** work, but you could wreck your machine in the process.

Unfortunately a lot of vendors these days only seem to support Windows for this sort of thing.

---

### Post by xyzzyman on 2012-01-20
If it was a phoenix or ami bios it's doable, but the Acer Timeline's use an InsydeH20 and there isn't a linux installer. You'll need to download the latest bios from acer and do the following to install from a usb flash drive:


1. If not already installed, you need gparted and unetbootin

```
sudo apt-get install gparted unetbootin
```

2. Use gparted to create a single FAT16 formatted partition on the flash drive.

3. Use unetbootin to install a bootable FreeDOS onto the flash drive:

[LIST]
[*]Select the distribution FreeDOS.
[*]Select your USB flash drive
[*]Click OK. This will download FreeDOS to create a DOS bootable flash drive.
[/LIST]

4. Copy your motherboard's BIOS update (Inside of the DOS directory for your acer BIOS) into the root of flash drive. These files will be located in B: or C: drive when you boot into FreeDOS.

---

### Post by gaz2011 on 2012-01-21
> **xyzzyman said:**
> If it was a phoenix or ami bios it's doable, but the Acer Timeline's use an InsydeH20 and there isn't a linux installer. You'll need to download the latest bios from acer and do the following to install from a usb flash drive:


1. If not already installed, you need gparted and unetbootin

```
sudo apt-get install gparted unetbootin
```2. Use gparted to create a single FAT16 formatted partition on the flash drive.

3. Use unetbootin to install a bootable FreeDOS onto the flash drive:

[LIST]
[*]Select the distribution FreeDOS.
[*]Select your USB flash drive
[*]Click OK. This will download FreeDOS to create a DOS bootable flash drive.
[/LIST]

4. Copy your motherboard's BIOS update (Inside of the DOS directory for your acer BIOS) into the root of flash drive. These files will be located in B: or C: drive when you boot into FreeDOS.

Thanks for reply. I have a mini usb stick that is already FAT32. Can I use it as it is or do I have to change it to FAT16? Not sure how to change it to be honest.
Thanks

---

### Post by raja.genupula on 2012-01-21
leave that job to unetbootin , i hope it can manage.

---

### Post by imachavel on 2012-01-21
well yes because often Bios updates are in the form of a windows file format that fits onto a floppy drive. Being that way, you'd have to format a flash drive by mounting it first, so that the file type could fit onto the floppy. It totally depends on your mobo and whether or not bios updates have been made for it, with windows some updates can just download, install, and then when you reboot the Bios is updated. Obviously in some cases you can revert to old bios settings if an update messes something up.

But first and foremost I'd have to say that advice is correct, these updates are made to apply through windows. Although obviously windows has nothing to do with bios settings, because bios is basic input output system. Maybe DRIVERS for bios is windows based, but bios loads before a drive is booted to mount an OS. I'm not sure but yes I suppose putting the update on a usb and booting to it would work. I don't see how the update being made for windows would effect that. But then if a senior forum member said it would, I'd take his advice. Although I personally couldn't image that, but once again:

look for an update for your bios:

1) if it's in a rom or what not file it's made for a floppy

2) if it's made to install through the already loaded gui on the OS then it's made to over write the bios lock from the gui, change the settings from windows, then when you reboot it sets the bios update. So how would you boot to the update?

Either way I only ASSUME a rom file or what not can be installed to a flash drive then booted to. But first thing you need to find out if bios updates are available for your mobo. And sometimes they are made available through 3rd party sites and not the manufacturer

---

### Post by imachavel on 2012-01-21
> **raja.genupula said:**
> leave that job to unetbootin , i hope it can manage.

did he find the update?

---

### Post by imachavel on 2012-01-21
> **xyzzyman said:**
> If it was a phoenix or ami bios it's doable, but the Acer Timeline's use an InsydeH20 and there isn't a linux installer. You'll need to download the latest bios from acer and do the following to install from a usb flash drive:


1. If not already installed, you need gparted and unetbootin

```
sudo apt-get install gparted unetbootin
```2. Use gparted to create a single FAT16 formatted partition on the flash drive.

3. Use unetbootin to install a bootable FreeDOS onto the flash drive:

[LIST]
[*]Select the distribution FreeDOS.
[*]Select your USB flash drive
[*]Click OK. This will download FreeDOS to create a DOS bootable flash drive.
[/LIST]

4. Copy your motherboard's BIOS update (Inside of the DOS directory for your acer BIOS) into the root of flash drive. These files will be located in B: or C: drive when you boot into FreeDOS.

ok you are just walking him through backing up his current bios settings

---

### Post by xyzzyman on 2012-01-21
> **imachavel said:**
> ok you are just walking him through backing up his current bios settings

No I forgot the rest of the steps:

5.) Boot from the USB drive. 

6.) Run the executable (It will be in the b or c drive)

His model's DOS updater is a single executable like all InsydeH20 bios updates. It's not like phoenix or AMI that have a seperate ROM file and an updater executable. Hence also why I said to copy the file from the DOS folder and not the Windows folder... Updating the BIOS from DOS is the preferred way anyways. The Windows updaters aren't as safe hence why most have a DOS folder for those who know what to do.

Still not sure how you get out of what I wrote that he was just backing up his current settings. He gave the model # of his system and that's it's an Acer. I would never recommend him to use a BIOS update on an OEM system on a 3rd party site in this type of forum. The Timeline series of Acer's Aspire's are known for requiring a BIOS update to properly recognize the battery so it's a fix that he does have to perform also, otherwise we'd be recommending against updating the BIOS.

@gaz2011: unetbootin will take care of it. It's just making sure that your thumb drive has a single partition (Some have multiple for pre-installed software that comes with the drive).

---

### Post by |{urse on 2012-01-21
a big nvm..

---

### Post by xyzzyman on 2012-01-21
> **|{urse said:**
> Maybe try flashing it from windows pe instead

download [http://www.livecdlist.com/windows-pe](http://www.livecdlist.com/windows-pe) 

burn it then boot to it 

download and run the bios update from acer

wonder if that would work?

What you linked to won't give him a simple ISO to download. He would then have to install the windows auotmated installation kit, and then create his own LiveCD... Which means he has to have Windows installed already to set it all up! lol 

Also the Acer windows updater executable for his InsydeH2O bios will fail running from a PE with a write error. If he makes a 64bit PE it will fail even sooner with an error as WOW64 won't be included to run the 32bit executable.

---

### Post by |{urse on 2012-01-21
> Instructions
To install the Windows AIK, you must first download the ISO, Write the ISO file to a DVD using a third party tool, and then install the Windows AIK from the DVD. For installation on Windows prior to Windows 7, this download requires that you run genuine Microsoft Windows. Click the Continue button in the Validation Required section to begin the validation process. After validation is complete, you will return to this page to continue the download. 

For the latest issues and known workarounds, see the Windows AIK Readme file ([http://go.microsoft.com/fwlink/?LinkId=139690](http://go.microsoft.com/fwlink/?LinkId=139690)).


yeah  just saw that, there are PE versions that are that easy i've downloaded before somewhere on the nets but im just now remembering they werent very legal lol

---

### Post by xyzzyman on 2012-01-21
Yeah, his only real option is to create a dos/freedos USB drive and flash using the DOS updater. Luckily that is the safest way to update the BIOS.

---

### Post by gaz2011 on 2012-01-22
Thanks for the help everyone. Wil give it a try & let you know how it went.
Cheers

---

### Post by gaz2011 on 2012-01-22
Dont want to sound stupid here. But when copying the bios update(it's a zip file) on to the flash, should i extract it 1st then use the dos file? I don't want to brick this lol

---

### Post by xyzzyman on 2012-01-22
> **gaz2011 said:**
> Dont want to sound stupid here. But when copying the bios update(it's a zip file) on to the flash, should i extract it 1st then use the dos file? I don't want to brick this lol

Yes you need to extract the file. You won't be able to even run the zip file.

---

### Post by gaz2011 on 2012-01-23
So I did this;

2. Use gparted to create a single FAT16 formatted partition on the flash drive.

3. Use unetbootin to install a bootable FreeDOS onto the flash drive:

    Select the distribution FreeDOS.
    Select your USB flash drive
    Click OK. This will download FreeDOS to create a DOS bootable flash drive.


4. Copy your motherboard's BIOS update (Inside of the DOS directory for your acer BIOS/ only was 1 file inside dos folder) into the root of flash drive. 


5.) Boot from the USB drive. 

Selected last option boot to free dos live cd. Option came up for A drive. Changed it to b drive & c drive but it says can not redirect output to file.

Anyone know why its not working?

---

### Post by xyzzyman on 2012-01-23
The time you've spent you could have just used your recovery discs and put windows on, flashed the bios, and reinstalled linux. :P

What are you typing to change drives? Have you done a DIR on A to see if the file wound up there? If it's FAT32 instead of FAT16 you may have issues also. I wasn't sure why but I've had issues before that I attributed to it. It's been awhile as if I don't have my DOS boot USB drive I just make one on a windows system without having to deal with freedos and it being a livecd image placed on it.

---

### Post by gaz2011 on 2012-01-24
i formatted it to FAT16 instead of FAT32. to change drive to b & c i pressed B:\>    C:\>

---

### Post by xyzzyman on 2012-01-24
> **gaz2011 said:**
> i formatted it to FAT16 instead of FAT32. to change drive to b & c i pressed B:\>    C:\>

You only type

```
b:
```

or 

```
c:
```

When you type > it's trying to redirect which is why you're getting a redirect error.

---

### Post by gaz2011 on 2012-01-24
I typed in b:    it says remove diskette in drive a: insert diskette in drive b:                         when i type c: nothing appears     ?? What u thinks wrong?

---

### Post by xyzzyman on 2012-01-24
> **gaz2011 said:**
> I typed in b:    it says remove diskette in drive a: insert diskette in drive b:                         when i type c: nothing appears     ?? What u thinks wrong?

Then most likely it's the way unetbootin is creating it. You should just give up, and use someone's Windows machine to make a traditional USB boot disk:

[http://www.sevenforums.com/tutorials/46707-ms-dos-bootable-flash-drive-create.html](http://www.sevenforums.com/tutorials/46707-ms-dos-bootable-flash-drive-create.html) Then you can copy the file over from windows inline with all the other files.

---

### Post by whatisupposetodo on 2012-02-28
Hi,

I am using ubuntu 11.10 with acer aspire 5315 and I need a bios upate because of fan is not working and it should work after update. I have downloaded and installed gparted and unetbootin and set my usb stick fat16 and its mounted. Then I installed freedos with unetbootin to the usb stick.

I have downloaded an update (.exe) for bios. I tried to boot with it ( Put it onto root of usb) but it says "boot error" when started. Same problem with an empty stick (Only freedos installed) Do I have to change it into .iso format or do I have to use another file in usb stick?

I cant find any C: or D: in 11.10 ether..

Thanks!

---


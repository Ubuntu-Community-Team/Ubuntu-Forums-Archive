---
title: "How do I remove Ubuntu?"
date: 2010-09-05
forum: General Help
---

### Post by booch221 on 2010-09-05
I Want to remove Ubunto 10 and make my computer only Windows again. I hope I don't have to run the Windows restore disk. I can't surf the net with Ubuntu. It's way too slow compared to Windoes XP. I've asked for help in other threads (see below), but no one ever answers my questions.

**Web pages slow to load with wireless connection**
[http://ubuntuforums.org/showthread.php?t=1567207](http://ubuntuforums.org/showthread.php?t=1567207)

**Browsing is very slow and other problems**
[http://ubuntuforums.org/showthread.php?t=1566614](http://ubuntuforums.org/showthread.php?t=1566614)

**Ubuntu is slower than Windows XP**
[http://ubuntuforums.org/showthread.php?t=1565950](http://ubuntuforums.org/showthread.php?t=1565950)

**extremely slow wireless 10.04 - atheros**
[http://ubuntuforums.org/showthread.php?t=1466833](http://ubuntuforums.org/showthread.php?t=1466833)

---

### Post by Donzieja on 2010-09-05
Did you install with WUBI.EXE? If so, just go into the C:/ Drive and delete the Ubuntu folder.

---

### Post by DjSesso on 2010-09-05
> **Donzieja said:**
> Did you install with WUBI.EXE? If so, just go into the C:/ Drive and delete the Ubuntu folder.

Must be or it wouldn't be slower.

---

### Post by 73ckn797 on 2010-09-05
If you did not install through Windows (WUBI) you may want to download "ndisgtk" from Synaptic Package Manager. From that you could try installing a Windows driver. I have had to do that on one computer and it will work fine. Use the XP driver if that is what you have.

---

### Post by booch221 on 2010-09-05
No, it's not a wubi installation. It's a dual boot and Ubuntu is the first on the list.

---

### Post by booch221 on 2010-09-05
> **73ckn797 said:**
> If you did not install through Windows (WUBI) you may want to download "ndisgtk" from Synaptic Package Manager. From that you could try installing a Windows driver. I have had to do that on one computer and it will work fine. Use the XP driver if that is what you have.

I went to [http://www.nongnu.org/synaptic/](http://www.nongnu.org/synaptic/)
but I don't see where to get this file. Do I do this in Windows or Ubuntu?

---

### Post by MooPi on 2010-09-05
I'm sorry but you have indicated that it was a Windows installer.
Your Quote:```
No, I did not check if the hardware worked under Linux. I didn't see anything on the download page about that. I burned a disk and ran it from there. That was awful. So I tried to install it from the disk, but that failed (I got an error message, something about the disk partition process failed). So then I used the Ubuntu Windows installer. 
```
 Your problem is most certainly a WUBI install situation, which is the windows installer.

---

### Post by 73ckn797 on 2010-09-05
> **booch221 said:**
> I went to [http://www.nongnu.org/synaptic/](http://www.nongnu.org/synaptic/)
but I don't see where to get this file. Do I do this in Windows or Ubuntu?
I was meaning that, when in Ubuntu, you go to the top panel and go to System/Administration/Synaptic Package Manager and find "ndisgtK' and right click and install. Then from that program, once it is installed and found under System/Preferences you can install a Windows wireless driver from the wireless CD or CD that came with the computer.

---

### Post by booch221 on 2010-09-06
> **MooPi said:**
> I'm sorry but you have indicated that it was a Windows installer.
Your Quote:```
No, I did not check if the hardware worked under Linux. I didn't see anything on the download page about that. I burned a disk and ran it from there. That was awful. So I tried to install it from the disk, but that failed (I got an error message, something about the disk partition process failed). So then I used the Ubuntu Windows installer. 
```
 Your problem is most certainly a WUBI install situation, which is the windows installer.

Yes, but I uninstalled WUBI and burned Ubuntu to USB drive and the installation worked.

---

### Post by TNT1 on 2010-09-06
> **booch221 said:**
> No, it's not a wubi installation. It's a dual boot and Ubuntu is the first on the list.

So boot into XP, and use the disk utility to delete the Linux partition, and resize the XP partition into it.

---

### Post by Rasa1111 on 2010-09-06
people have answered many of your questions.
Just because you dont grasp them, 
doesnt mean people havent tried. 

and when you make 4 threads that are *almost* all the same, with different titles, slightly different wording, 
 and~ when people try to give you answers but you don't accept or understand them~
 There's not much anyone can do for ya. 

I assure you, your issues are rare , and not "commonplace" with Ubuntu. 

man, many 'Super noobs' do perfect with it,
and see that it is amazing.
 Sorry you can't experience the same. 
Peace.

> So boot into XP, and use the disk utility to delete the Linux partition, and resize the XP partition into it.

+1

---

### Post by booch221 on 2010-09-06
> **73ckn797 said:**
> I was meaning that, when in Ubuntu, you go to the top panel and go to System/Administration/Synaptic Package Manager and find "ndisgtK' and right click and install. Then from that program, once it is installed and found under System/Preferences you can install a Windows wireless driver from the wireless CD or CD that came with the computer.
OK--I installed *ndisgtk.* Now when I go to System/Preferences what am I supposed to look for? 

Then I'm supposed to install a Windows wireless driver from the CD that came with my Linksys wireless router?

I'm not ready to give up on Ubuntu yet. When I plug the ethernet cable directly into my computer it works perfectly. 

When I try using the wireless connection the progress bar goes to about 70%, and the hangs. However, if I ever do get it to load **one** time, it will usually work from then on.

I could never get the washingtonpost.com to load. Then I went there with the ethernet cable plugged in, now I can go to the home page wirelessly, but not to any links on the homepage.

---

### Post by jeremy1138 on 2010-09-06
> **booch221 said:**
> OK--I installed *ndisgtk.* Now when I go to System/Preferences what am I supposed to look for? 

Then I'm supposed to install a Windows wireless driver from the CD that came with my Linksys wireless router?

I'm not ready to give up on Ubuntu yet. When I plug the ethernet cable directly into my computer it works perfectly. 

When I try using the wireless connection the progress bar goes to about 70%, and the hangs. However, if I ever do get it to load **one** time, it will usually work from then on.

I could never get the washingtonpost.com to load. Then I went there with the ethernet cable plugged in, now I can go to the home page wirelessly, but not to any links on the homepage.

I'm confused...  Are you trying to uninstall Ubuntu or are you trying to get your wireless network card working on Ubuntu?

If you're trying to get your wireless card working you should search the forums for the model number of your card to see what others have done to get it working.  That almost always works for me.

If you're trying to get Ubuntu uninstalled so that you can have a windows only machine, you will need to delete the ubuntu partitions and resize the windows partition to fill the empty space.

I believe you'll also have to use your windows disc to run the recovery console and run fixboot so that windows will boot.  Can someone confirm that please?  It's been a while since I had to do any of that.

Hope that helps!  :)

---

### Post by booch221 on 2010-09-06
> **jeremy1138 said:**
> I'm confused...  Are you trying to uninstall Ubuntu or are you trying to get your wireless network card working on Ubuntu?

If you're trying to get your wireless card working you should search the forums for the model number of your card to see what others have done to get it working.  That almost always works for me.

If you're trying to get Ubuntu uninstalled so that you can have a windows only machine, you will need to delete the ubuntu partitions and resize the windows partition to fill the empty space.

I believe you'll also have to use your windows disc to run the recovery console and run fixboot so that windows will boot.  Can someone confirm that please?  It's been a while since I had to do any of that.

Hope that helps!  :)
Sorry for the confusion. I like to give Ubuntu a try. If I can't get it to work, I will uninstall it.

---

### Post by 73ckn797 on 2010-09-06
> **booch221 said:**
> OK--I installed *ndisgtk.* Now when I go to System/Preferences what am I supposed to look for? 

Then I'm supposed to install a Windows wireless driver from the CD that came with my Linksys wireless router?

I'm not ready to give up on Ubuntu yet. When I plug the ethernet cable directly into my computer it works perfectly. 

When I try using the wireless connection the progress bar goes to about 70%, and the hangs. However, if I ever do get it to load **one** time, it will usually work from then on.

I could never get the washingtonpost.com to load. Then I went there with the ethernet cable plugged in, now I can go to the home page wirelessly, but not to any links on the homepage.

Go to System/Administration/Windows Wireless Drivers. It will prompt you for the source of the driver. Insert the CD for the wireless adapter in your computer, not the router. I do not know what kind of wireless card you are using. Is the computer an "out of the box" system (Dell, HP or similar?) or did you build it with parts? Did you install the wireless card later or did the computer have it already installed?

---

### Post by booch221 on 2010-09-06
> **73ckn797 said:**
> Go to System/Administration/Windows Wireless Drivers. It will prompt you for the source of the driver. Insert the CD for the wireless adapter in your computer, not the router. I do not know what kind of wireless card you are using. Is the computer an "out of the box" system (Dell, HP or similar?) or did you build it with parts? Did you install the wireless card later or did the computer have it already installed?

It's a Toshiba Satellite M55-S139 laptop with an Intel Celeron M processor 1.6 GHz and 1G RAM. It came with a wireless card installed.

> Go to System/Administration/Windows Wireless Drivers. It will prompt you for the source of the driver. Insert the CD for the wireless adapter in your computer
There is no Windows/Wireless Drivers under System/Administration/

---

### Post by 73ckn797 on 2010-09-06
> **booch221 said:**
> It's a Toshiba Satellite M55-S139 laptop with an Intel Celeron M processor 1.6 GHz and 1G RAM. It came with a wireless card installed.


There is no Windows/Wireless Drivers under System/Administration/

If you installed ndisgtk it will appear as I described in System/Administration/Windows Wireless Drivers. Make certain it really has been installed. If not then follow this: [https://help.ubuntu.com/community/WifiDocs/SolvingWireless](https://help.ubuntu.com/community/WifiDocs/SolvingWireless)

---

### Post by Rational1 on 2010-09-06
Sorry you are having problems, the answer is out there. In the future maybe research your purchase if possible. Bad driver support is generally not the communities fault. I had a Dell Mini12 with Poulsbo video, even though the community kept piecing together the horrible manufacturer driver blob, I did some research and found a laptop that worked "out of the box" with the proprietary wireless driver. Now I am on a smokin fast Dell 11z from their outlet store. 15 browser tabs, creating a document with graphics, listening to music, Full screen 1080x1440 video playing, 50% processor 41% memory not even a tiny blip. Linux/Ubuntu rocks beyond compare, the movie was just to see if it could do it at the same time. Compiz running with all my favorite bells and whisles active. Download 15.5Mb/s up 1.95Mb/s no sluggishness at all.

Good luck.

Dell 11Z, Intel Su4100 @ 1.3G, 160G hard drive, 2Gig ram, Crystal HD video, 6 cell battery 6+ hours runtime.

---

### Post by booch221 on 2010-09-06
> **Rational1 said:**
> Sorry you are having problems, the answer is out there...
Thanks. It's frustrating to try something and not have it work. Then when you seek help, people blame you. 

The most frustrating thing is **_some_** websites load very fast, and others hang. But in Windows XP everything loads fast. The problem with Windows is that it's slow to boot and open the browser.

I'm sure it's some just setting that needs to be tweaked...

---

### Post by 73ckn797 on 2010-09-06
> **booch221 said:**
> Thanks. It's frustrating to try something and not have it work. Then when you seek help, people blame you. 

The most frustrating thing is **_some_** websites load very fast, and others hang. But in Windows XP everything loads fast. The problem with Windows is that it's slow to boot and open the browser.

I'm sure it's some just setting that needs to be tweaked...

You will find solutions to most of your questions. There is a wealth of information available here.

Look around at the following links and you will be able to figure things out. You will get past the steep learning curve of Linux/Ubuntu and laugh one day at your reactions to issues you encounter.

[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)
[https://help.ubuntu.com/community/TitleIndex](https://help.ubuntu.com/community/TitleIndex)
[http://crunchbang.org/ubuntu-search-engine/](http://crunchbang.org/ubuntu-search-engine/)

---

### Post by booch221 on 2010-09-08
> **TNT1 said:**
> So boot into XP, and use the disk utility to delete the Linux partition, and resize the XP partition into it.

So I see three partitions:
The first one is 35 GB, Healthy (Unknown Partition) I assume that's Linux
The second one is 1.5 GB Healthy (Unknown Partition)
The third is (C: 38 GB  Healthy (System) I assume that's Windows

Do I just delete the first one?

---

### Post by dirghrabadia on 2010-09-08
I would rather use Gparted for partitioning matters, since it shows a bit more info then you just posted.

---

### Post by DeadlyOats on 2010-09-08
> **booch221 said:**
> So I see three partitions:
The first one is 35 GB, Healthy (Unknown Partition) I assume that's Linux
The second one is 1.5 GB Healthy (Unknown Partition)
The third is (C: 38 GB  Healthy (System) I assume that's Windows

Do I just delete the first one?

The first two partitions seems to be what need to be deleted.  The 35GB is your Linux partition.  I'm guessing the 1.5GB partition is the SWAP partition for Linux. (SWAP is to Linux, what Page File is to Windows.)

However, to be sure, log into Ubuntu, and look in System>Administration> and click on Disk Utilities.  It will list your hard drive, and all of the partitions, and what each partition is.

I'm guessing, you'll see that the 1.5GB partition is your Linux SWAP.  After you've confirmed that it is.  You'll know to delete both "(Unknown Partion)"s (from the WinXP Disk Management utility).

You can then, using the Disk Management utility, either create a new partition, and format it to NTFS.  WinXP will see it as Drive D or E (provided you only have one Windows Drive C).  Or you can do the already suggested, "resize the partition trick."

Good luck.

---

### Post by TNT1 on 2010-09-08
> **booch221 said:**
> So I see three partitions:
The first one is 35 GB, Healthy (Unknown Partition) I assume that's Linux
The second one is 1.5 GB Healthy (Unknown Partition)
The third is (C: 38 GB  Healthy (System) I assume that's Windows

Do I just delete the first one?

Yip, looks like the first is your linux.

---

### Post by TNT1 on 2010-09-08
> **DeadlyOats said:**
> The first two partitions seems to be what need to be deleted.  The 35GB is your Linux partition.  I'm guessing the 1.5GB partition is the SWAP partition for Linux. (SWAP is to Linux, what Page File is to Windows.)

However, to be sure, log into Ubuntu, and look in System>Administration> and click on Disk Utilities.  It will list your hard drive, and all of the partitions, and what each partition is.

I'm guessing, you'll see that the 1.5GB partition is your Linux SWAP.  After you've confirmed that it is.  You'll know to delete both "(Unknown Partion)"s (from the WinXP Disk Management utility).

You can then, using the Disk Management utility, either create a new partition, and format it to NTFS.  WinXP will see it as Drive D or E (provided you only have one Windows Drive C).  Or you can do the already suggested, "resize the partition trick."

Good luck.

Yip, I agree with that.

---

### Post by mdurham on 2010-09-08
Be careful, removing Linux will probably make your computer UNBOOTABLE, because Linux manages the booing for Linux and Windows. I have read that you will need to boot from your Windows recovery disk to sort out the MBR. I'm not a Windows person but there will be advice on this in this forum, just search for it.
Cheers, Mike

---

### Post by Off Topic on 2010-09-08
So suggesting shooting it would be out of line?

---

### Post by mdurham on 2010-09-08
> **Off Topic said:**
> So suggesting shooting it would be out of line?
I'm not sure what that means, but it's okay to remove the Linux partition if you have the Windows install disk to fix the MBR (Master Boot Record) after removing it.

---

### Post by TNT1 on 2010-09-08
> **mdurham said:**
> Be careful, removing Linux will probably make your computer UNBOOTABLE, because Linux manages the booing for Linux and Windows. I have read that you will need to boot from your Windows recovery disk to sort out the MBR. I'm not a Windows person but there will be advice on this in this forum, just search for it.
Cheers, Mike

Yes, you will need to, do a quick search here, it's an easy fix to repair the mbr from recovery console. You will need a windows xp boot disk though...

---

### Post by stinkeye on 2010-09-08
If your unsure which partition your Windows install is on
don't delete any partitions.
Just use this guide to restore your windows boot
and then delete the unwanted partitions in Windows which you seem to be more familiar with.
[**_[COLOR="DarkRed"]How to restore the Ubuntu/XP/Vista/7 bootloader[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1014708")
It's just a matter of booting from your windows install cd,
selecting the repair option and running 2 commands.
```
fixboot
fixmbr
```

---

### Post by booch221 on 2010-09-08
> **mdurham said:**
> Be careful, removing Linux will probably make your computer UNBOOTABLE, because Linux manages the booing for Linux and Windows. 


That's exactly what happened. I did this two days ago before the latest posts. I lost the ability to boot Ubuntu and Windows. So I formatted the C drive,  reset the BIOS to the default settings, and ran the computer system recovery disk, but it still wouldn't boot to Windows.  The Toshiba splash screen would appear, then the screen would go black, then the Toshiba splash screen would appear again, over and over.

Finally I reinstalled Ubuntu and when I started the computer it gave me the option of using Windows again. 

So that's where I am, back to a dual boot system, which would be fine if I could just get the wireless to work.

---

### Post by booch221 on 2010-09-08
I would like to do this
[**_[COLOR=DarkRed]How to restore the Ubuntu/XP/Vista/7 bootloader[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1014708")
but I can't get to a C prompt in Windows.

I don't have a Windows XP installation CD.
All I have is the recovery CD which loads the OS and all the programs and drivers. It doesn't give me any choices, it just starts the recovery process. So I'm unable to follow the instructions:

[SIZE=5][COLOR=red]How to restore the Windows XP bootloader[/COLOR][/SIZE]

For this you will need your Windows XP installation CD. Boot into it now.

You will get to a part where it asks if you want to repair or recover. To do so, press "r".

If prompted, enter your Windows XP administrator password. This will  leave you at at a command line, so type in the following two commands:

     Code:
     fixboot 
     Code:
     fixmbr 
Then type      Code:
     exit 
 then remove your XP cd. If everything has gone well, you should come to your XP bootloader.

---

### Post by Rasa1111 on 2010-09-08
> which would be fine if I could just get the wireless to work

Have you entered in your WEP key?

---

### Post by booch221 on 2010-09-08
> **Rasa1111 said:**
> Have you entered in your WEP key?
Yes. 

Some websites work and some don't. For example, I can get to my Yahoo page, but when I try to follow a link half the time it doesn't work. I can go to the Wall Street Journal, but not the Washington Post. I can get to the front page of the New York Times, but not to any of the stories.

However, in Windows XP, I can _all_ links very quickly. The problem is Windows takes a long time to boot, and open Firefox, once it does it's much faster than Ubuntu.

---

### Post by Rasa1111 on 2010-09-08
hmmm...
Not sure what the deal is there. 


> However, in Windows XP, I can all links very quickly. The problem is Windows takes a long time to boot, and open Firefox, once it does it's much faster than Ubuntu.

 Interesting,
my experience is just the opposite. 
Other than windows taking a long time to boot and open FF.. that it did! lol

 But on all PC's Ive installed Ubuntu on, (multiple handfuls)
Ubuntu has always run far faster than any XP or vista or windows 7,
in all areas. 

Sorry you're not experiencing the same. :(

---

### Post by alphacrucis2 on 2010-09-08
> **booch221 said:**
> Yes. 

Some websites work and some don't. For example, I can get to my Yahoo page, but when I try to follow a link half the time it doesn't work. I can go to the Wall Street Journal, but not the Washington Post. I can get to the front page of the New York Times, but not to any of the stories.

However, in Windows XP, I can _all_ links very quickly. The problem is Windows takes a long time to boot, and open Firefox, once it does it's much faster than Ubuntu.


Try disabling IPV6 in the Ubuntu Firefox. Type ```
about:config
``` in the Firefox URL bar. It will respond with a warning saying something like "Here be Dragons" 

Click OK to agree that you will be careful and type ipv6 in the filter. It should display a field called network.dns.disableipv6. By default it is set to false. Double click it to change it to true and see if that helps.

---

### Post by booch221 on 2010-09-09
> **alphacrucis2 said:**
> Try disabling IPV6 in the Ubuntu Firefox. 
I tried this, it didn't help.

My computer has Atheros® 802.11b/g wireless-LAN. In some other threads it was said there is an issue with the driver.  

> **73ckn797 said:**
> I was meaning that, when in Ubuntu, you go to  the top panel and go to System/Administration/Synaptic Package Manager  and find "ndisgtK' and right click and install. Then from that program,  once it is installed and found under System/Preferences you can install a  Windows wireless driver from the wireless CD or CD that came with the  computer.

I installed "ndisgtk". I don't have a CD with the driver on it but I did download the Windows driver from the Toshiba support site and put it on my jump drive. I'm unable it install it. There are over a dozen files in the zipped download but everyone of them says *not a vaid driver .inf file* when I try to install it in Windows Wireless Drivers.

---

### Post by 73ckn797 on 2010-09-09
> **booch221 said:**
> There are over a dozen files in the zipped download but everyone of them says *not a vaid driver .inf file* when I try to install it in Windows Wireless Drivers.
Are there any directories in the zipped file? Do you have the Toshiba recovery disk? You may find the driver on it. It could also take a lot of searching to find it.

I inserted my Toshiba disk for my Satellite and found a driver under ```
/media/disk_/comps1
``` though it is an "exe" file.

Maybe you could go to the Atheros site and look there: [http://www.google.com/custom?safe=vss&cof=L%3Ahttp%3A%2F%2Fwww.atheros.com%2Fimages%2FSearchLogo.gif%3BLW%3A282%3BLH%3A164%3BAH%3ACenter%3BGL%3A0%3BVLC%3A%230000FF%3B&sitesearch=Atheros.com&q=drivers&btnG=Go](http://www.google.com/custom?safe=vss&cof=L%3Ahttp%3A%2F%2Fwww.atheros.com%2Fimages%2FSearchLogo.gif%3BLW%3A282%3BLH%3A164%3BAH%3ACenter%3BGL%3A0%3BVLC%3A%230000FF%3B&sitesearch=Atheros.com&q=drivers&btnG=Go)

---

### Post by booch221 on 2010-09-09
I did a lot of searching and most of the proposed solutions require a Windows  installation CD.
 

My computer did not come with Windows XP installation CD, it just came with a Toshiba Recovery CD, which is not the same thing. And I could not create a Boot Disk because my laptop doesn't have a floppy drive.
 

I finally figured out how to remove Ubuntu from my computer and get it to boot in Windows XP.  
 

You need a free program called **MbrFix**. To use it, You must log in as administrator in Windows Safe Mode.
 
 
[LIST]
[*]Start your computer.
[*]Arrow down to Windows
[*]Hit **Enter **and tap the **F8 **key immediately.
[*]Log in as administrator.
[/LIST]
 

 Open your browser and go to:
 [http://www.sysint.no/products/Download/tabid/536/language/en-US/Default.aspx](http://www.sysint.no/products/Download/tabid/536/language/en-US/Default.aspx)
 Download **MbrFix**. If you can't find it, Google  *MbrFix, * as it's available at cnet.com and other sites.
 

 
[LIST]
[*]Then extract the contents to C:\
[*]Go to **Start**, click on **Run**     and type 'command'
[*]This will open a terminal.
[*]Type 'cd\'
[*]You will get a C:\> prompt
[*]Enter: MbrFix /drive 0 fixmbr /yes
[*]Now the GRUB menu will be gone and     you will automatically boot into Windows.
[/LIST]
 Next: 
[LIST]
[*]Delete Ubuntu partition(s) by going to to the     Control Panel>Computer Management>Disk Management
[/LIST]

---

### Post by booch221 on 2010-09-12
Someone in another forum told me about this method. I haven't tried it myself, but it sounds a lot simpler. You need a Win98SE boot disk (which also works with Windows XP) which you can get here:

[http://www.getupload.org/en/file/16543/Win98SE-bootdisk-zip.html](http://www.getupload.org/en/file/16543/Win98SE-bootdisk-zip.html)

Scroll to bottom of page, wait 40 sec's click download and then burn the image to a CD. 

Boot from the CD and type:
**FDISK /MBR [press enter]**

This will remove the Master Boot Record. The next time you start your computer it will boot in Windows. Delete the Ubuntu partition(s) as described in Post #39.

---

### Post by Dex73 on 2010-09-12
"I can't surf the net with Ubuntu. It's way too slow compared to Windoes XP."

Slower? Really! Have you checked out Chrome? Some people hate it, but I've learned to love it!

Anyway, I've messed around with partitions in the past, had to cut in and say, you should consider using an external hard drive to save files and wiping that machine clean with a fresh copy of XP, though this does sound possible. Good Luck or at least better than mine!

---

### Post by booch221 on 2010-09-12
> **Dex73 said:**
> "I can't surf the net with Ubuntu. It's way too slow compared to Windoes XP."

Slower? Really! Have you checked out Chrome? Some people hate it, but I've learned to love it!


Yes, I tried Chrome and Opera with Ububtu--nothing worked. The problem was not the browsers, they all worked fine with the ethernet cable plugged in--it was the wireless that didn't work. I use Chrome with Windows and I love it's speed. Fast to launch, fast to load pages.

---

### Post by markMDW on 2010-09-12
I've used Xubuntu with Firefox on a laptop that was extremely slow with XP on it, probably due to malware of some sort.  With Xubuntu it was just like a brand new lightning fast machine, even with Firefox.  Seamonkey is also great and comes with a complete email suit.

As for uninstalling a Wubi installed version of Ubuntu, all you should have to do is simply go into Windows, Add/Remove Programs, and Remove the Wubi installation.  I did that several times and always able to get a clean bootable Windows 7 installation (can't vouch for XP).  Since then I might add that I've reinstalled Ubuntu directly and have it coexisting just find with Windows7 on dual boot (not from a wubi install).  This is just some simple advice, I'd trust the other more expert comments in this thread if you've ran into problems with the uninstall.  But Ubuntu should have been as fast as XP even on Wubi installation.  Good Luck!

---


---
title: "Serious 10.04 Update Problems - Please help !"
date: 2012-03-25
forum: General Help
---

### Post by Johnny M! on 2012-03-25
25-March-2012
 

 10.04 UPDATE PROBLEM
 

 

 I run Ubuntu Linux 10.04 Long Term Support Release –the  last good Update was on 10-March-2012 which included successful Kernel update to 2.6.32-39.   Everything A-OK!
 

 On 24-March-2012, I ran another System Update which included Kernel 2.6.32-40.   I always leave the last good Kernel as a boot option until I know the new Kernel is also good (in Menu.lst).
 

 After the 24-March Update, Ubuntu would not boot with ether Kernel ( 2.6.32-39 or  2.6.32-40).   The startup seemed normal but the Monitor Screen would go Blank (No Video Output and No Hard Drive Activity Light) just prior to where the Login Window should appear (to put in UserID and Password).
 

 Lucky for me – I had a good Backup on Acronis True Image Home 2011 and reloaded back to my 10-March-2012 Point in Time.  
 

 Through a process of trial and error (reloading my emergency recovery point multiple times), I managed to update the Kernel to 2.6.32-40 and pull down Firefox 11.    Those two updates are now good.   I made a new good Acronis Image.
 

 Here are the remaining updates that are interfering with my Ubuntu startup – and I have no idea why any of them would be freezing up my computer ??????
 

 With Kernel 2.6.32-40 and Firefox 11 OK; here is how I tried to get the remaining updates installed:
 

 I selected only these three related updates (isolating them from the rest) and tried an update and reboot:
 

 
[LIST]
[*]cpp-4.4
[*]gcc-4.4
[*]gcc-4.4base
[/LIST]
 

 Result – Startup Freeze at same point (no Login Screen – Blank Monitor and No Hard Drive Activity Light).   Ahh-Ha; the Culprits have been identified (at least that's what I thought).
 

 

 Here we go again – Another Acronis Emergency Recovery to my last  known good point in time.
 

 

 Next Attempt to update – I do NOT select the above culprit items (4.4 series); but select the remaining items as follow and proceed to Update:
 

 Important:
 

 
[LIST]
[*]gdm-guest-session
[*]libfreetype6
[*]libgcc1
[*]libgpmp1
[*]libpng12-0
[*]libstdc++6
[*]ubufox
[*]xulrunner-1.9.2
[/LIST]
 

 Recommended:
 

 
[LIST]
[*]app-install-data-commercial
[*]app-install-data-partner
[*]apt
[*]apt-transport-https
[*]apt-utils
[*]cron
[*]xserver-common
[*]xserver-xorg-core
[/LIST]
 

 

 Install the Updates and Reboot – OH NO - NO GO !!!!!!!!!
 System Freezes at the same point – now I'm stumped !!!!!!!!
 Obviously there is one of more items in the 4.4 series of three updates
 and one or more items in the next set of Updates that is causing my Computer to Freeze during the startup process.
 

 Yet Another Acronis Emergency recovery to my last know Good Point (Ubuntu 10.04 2.6.32-40).
 

 

 Can anyone out there in Ubuntu World help me out here.   
 Why would any of those (above) Updates be causing my computer to freeze ?
 

 Any and all suggestions appreciated !
 

 Thank You,
 Johnny M!
 

 

 

 PS:  I dual boot via GRUB into either Windows XP Pro (working flawlessly) or Ubuntu 10.04.    Both Operating Systems have been trouble free.   This is the first time (other than trying to boot with mis-mapped Kernels) that I've ever had such serious problems with an Ubuntu Update !

---

### Post by gordontytler2 on 2012-03-26
I have a similar problem after upgrading to 2.6.32-40. I believe my problem is due to an issue with the driver for ATI Radeon HD 3470. The computer appears to start normally but the signal to the monitors disappears. If I go back to the 20.6.32-39 version this now has the same problem.  I can make my monitors work by selecting 2.6.32-40 (recovery mode). I then select "resume normal boot" and type xstart to start gnome.

---

### Post by Johnny M! on 2012-03-26
Thanks for the reply [gordontytler2]("http://ubuntuforums.org/member.php?u=1592698")
 Appreciate your Help here!
 

 

 Yes – I have had recent Video Issues.
 Here is a quick overview:
 

 Santa Clause got me a new Video Card for Christmas 2011
 XFX Radeon HD 6870 2GB 256bit (Very Nice).
 

 In early Jan-2012:
 I replaced my VisionTek Radeon HD 5770 1 GB 128bit with my new AMD 6000 Series Video Card.
 I installed the latest AMD Catalyst Control Center 11-12 with AMD Driver 8.92 in Windows (all OK)
 and
 When I went into Ubuntu – my new Card didn't synchronize with (not recognized by) the existing 'fglrx' (AMD/ATI Open Source Video Driver)  install -  the Graphics reverted to some primitive mode.
 

 So in Synaptic Package Manager, I tried updating 'fglrx' including uninstalling and reinstalling the 'fglrx' Package.   No Luck – it wouldn't take; reason unknown.
 

 So I followed the instructions in this Self-Help You-Tube Video
  “Install ATI Drivers - Ubuntu 10.10”  
 [http://www.youtube.com/watch?v=eS9Nmet_sqQ](http://www.youtube.com/watch?v=eS9Nmet_sqQ)
 and got the latest AMD Video Driver installed OK:
 

 In Terminal:
 ls /var/lib/dkms/fglrx/ 
   AMD Display Driver ver 8.92
 

 

 All works well when I boot (via GRUB) into Ubuntu 10.04, but I did have problems (no Video) trying to boot from the raw Ubuntu DVD as an emergency boot test, and from my initial post this topic – I'm having similar problems after installing certain Updates and trying to boot.
 

 I think I'll try again to reinstall the 'fglrx' Package and Disk Jockey and see if that rectifies the situation.
 Wish me luck – if it works out I'll let you know.
 

 BVR
 Johnny M!
:guitar:

---

### Post by Johnny M! on 2012-03-26
OK - Here's what happened:

I used the Package Manager to install Jockey (Hardware Drivers) and 'fglrx" (AMD Proprietary Driver)
rebooted - OK, all well

Driver Version reverted from AMD 8.92 to fglrx 8.7 something (verified in Terminal)
But the Catalyst Control Center (under System - Admin) didn't work and Jockey (Hardware Drivers) didn't show the fglrx Driver (or any drivers).

But I went ahead and Ran Update Manager - all the rest of the Outstanding Updates downloaded and installed OK.

Reboot

Uninstalled fglrx and went back to AMD
[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)
and got their latest driver for my Radeon HD 6870 Card

AMD Video Driver 8.95 installed OK - System looks and works Great !

Have no idea why the updates worked today - and not past two days ????

I probably need to grab Ubuntu 12.04 come 26-April (my 10.04 LTR is getting a little old)!

Good Luck out There !


BVR
Johnny M!
):P

---


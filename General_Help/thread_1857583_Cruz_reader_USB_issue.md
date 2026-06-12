---
title: "Cruz reader USB issue"
date: 2011-10-10
forum: General Help
---

### Post by goplayer on 2011-10-10
Hello,
 
I hope this is the right place to ask the question. I was trying to connect a cruz reader (running android 2.2) to USB on Ubuntu. The connection gets established and I can see the SD cards without any problems. However I can't to get ADB to recognize and see the device. I made a rules file in /etc/udev/rules.d/ and tried different settings but to no avail--lsusb does not show the device. Has anyone been able to get ADB working with the cruz reader on ubuntu 10.04 LTS? Any help is greatly appreciated. 
 
Thanks

---

### Post by cubsfan53 on 2011-10-10
goplayer --

I also have the Cruz Reader (R101v2). I'm on 11.04 and all I had to do was plug in the usb cable to tether it...the sdcards (both of them - 1 internal and 1 external(sdcard port)) will show up in Nautilus.

Note that there should be a pop-up in the notification bar on the Reader acknowledging being attached, but do not deselect Debugging Mode.

Also, if you got the ADB driver from the Reader website please not that one is a Windows driver.

I'm running from memory here, so post back if you problems.

Rick

---

### Post by goplayer on 2011-10-10
Thanks Rick. When I connect tether the cruz reader to the computer I get a popup window asking me whetehr I should open the files with F-stop for photo editing--nothing about disabling debug or anything like that. The SD cards are seen and show up on the desktop. The ADB I downloaded is for linux downloaded from the android SDK site nto the cruz manufacturer site. 
What I want do is to remove some of the bloatware that came loaded with the device and the only way to do this it seems is through ADB, that's why I am trying to do this.
Again, thanks so much for taking the time to respond.
 
Cheers.

---

### Post by cubsfan53 on 2011-10-10
goplayer --

>  I was trying to connect a cruz reader (running android 2.2)
Sorry , I missed this earlier. do you have a Reader or Tablet. My understanding is that the Reader would not be upgradable to 2.2 due to only having 256MB RAM. I can try to help on the Reader as I have one, just not on the Tablet.

>  What I want do is to remove some of the bloatware that came loaded with the device and the only way to do this it seems is through ADB, that's why I am trying to do this.

Yes I quite understand as the RAM is so skimpy, and this is where any downloaded apps are installed. Couple of things -- 

Simplest way is if you have access to a Windows PC is to use the Velocity Micro utility and their windows ADB Driver. Here-[
HTML]http://cruzsupport.velocitymicro.com/link/portal/5462/5758/Article/794/How-can-I-uninstall-an-app-that-came-on-my-Cruz-Reader[/HTML]

My understanding is that you would still need to have root access on the device to see the installed apps in ROOT/system/app using ADB. This would require that the device be rooted with a custom ROM. I found the forums at slatedroid.com to be very instructive for this purpose, but it is not for the faint of heart. There is a sub-forum specifically for the Cruz Reader. In the Firmware Development area there is a thread about removing bloatware which might interest you.

I've been trying to crate a cheap "faux" tablet with my Reader. I have rooted it and have over-clocked the cpu, installed a custom ROM that allows me to have root access and installed a script that moved apps from the internal 256MB storage to the sdcard as well as any newly installed app that doesn't require being in the 256MB storage. I'm working on getting UbuntuOne to sync so that I can install and test an office suite to be more prouctive.

Sorry to be so long winded. Let me know if you have any other questions.

Rick

PS - If you do have a Reader with 2.2 could you let me know how you got it to work?
Thanks

---

### Post by goplayer on 2011-10-10
I have the cruz reader with android 2.0 not 2.2 sorry. I installed the Macho cruz which I have downloaded from links on Slatedroid. It is running fine and I was trying to root it but need access through ADB. I do have access to windows and would probably have to do this through windows but was hoping that it would be possible through ubuntu. In a nutshell I am trying to do the same thing as you did--essentially convert it to a cheap tablet with apps installed on the external SD card rather than then very limited internal space which is as you say skimpy with hardly any room for anything.
Again thanks for taking the time to answer my question.

---

### Post by cubsfan53 on 2011-10-11
goplayer--

Sorry for the delay in getting back to this. Did Some reading about the MachCruz Rom.

From what I read if this is the original ROm and not Pandabomb's version you should have root privileges already. 

I installed openjdk6 from the repositories and Android SDK on my system (laptop running 11.04 and the Reader is rooted using jgm's 4.0 ROM from slatedroid forums). Using this setup I was able to detect the reader (Tablet-P) and to get free memory and the list of pre-installed apps.

```
rick@rick-laptop:~/AndroidSDK/android-sdk-linux_x86/platform-tools$ ./adb devices
List of devices attached 
Tablet-P	device

rick@rick-laptop:~/AndroidSDK/android-sdk-linux_x86/platform-tools$ ./adb shell
# exit
rick@rick-laptop:~/AndroidSDK/android-sdk-linux_x86/platform-tools$ .adb shell
.adb: command not found
rick@rick-laptop:~/AndroidSDK/android-sdk-linux_x86/platform-tools$ ./adb shell
# free
              total         used         free       shared      buffers
  Mem:       200496       190380        10116            0        12000
 Swap:            0            0            0
Total:       200496       190380        10116
# ls /system/app/
gtalkservice.apk
VpnServices.apk
Vending.apk
UserDictionaryProvider.apk
UerWallpapers.apk
Term.apk
TalkProvider.apk
Talk.apk
Superuser.apk
SetupWizard.apk
SettingsProvider.apk
Settings.apk
SdkSetup.apk
PackageInstaller.apk
NetworkLocation.apk
Music.apk
MediaUploader.apk
MediaProvider.apk
MarketUpdater.apk
Launcher.apk
LatinIME.apk
HTMLViewer.apk
GoogleSettingsProvider.apk
GoogleSearch.apk
GooglePartnerSetup.apk
GoogleContactsSyncAdapter.apk
GoogleCheckin.apk
GoogleBackupTransport.apk
GoogleApps.apk
GlobalSearch.apk
GenieWidget.apk
Gallery.apk
EnhancedGoogleSearchProvider.apk
DrmProvider.apk
DownloadProvider.apk
Development.apk
ContactsProvider.apk
Contacts.apk
Calculator.apk
Browser.apk
ApplicationsProvider.apk
AlarmClock.apk
# 

```

I followed the instructions here [HTML]http://www.slatedroid.com/topic/11775-cruz-reader-only-step-by-step-for-update-root-and-setcpu/page__st__240[/HTML]
Post #242

Let me know if this is what you did or if you have any other questions and I'll try to help.

Rick

---

### Post by cubsfan53 on 2011-10-11
goplayer--

Another thought- since you should be rooted already, you could install Titanium Backup Pro. It wouldn't hurt to have backups for what you want to uninstall and it will allow you to uninstall any app including the pre-installed. The caveat is to be careful to not uninstall any app the system might need.

Rick

---

### Post by goplayer on 2011-10-12
Rick,
I finally was able to get ADB to see the device. I had to reflash the reader. I suppose what might have happened is that I might have accidentally turned the debug off or the usb off and I couldn't figure out how to turn them back on. Anyway I think I am OK now.
Thank so much for all your help and suggestions I truly appreciate you taking the time.

Cheers and have a wonderful day.:)

---

### Post by cubsfan53 on 2011-10-12
goplayer--

No worries! Hope you enjoy, I can't wait to get Ubuntu One working and an Office App.

Rick

---

### Post by jasonrisenburg on 2012-01-13
Hello I have got a cruz erader too with 2.0, is it possible to use ubuntu instead of updating android on it?

---


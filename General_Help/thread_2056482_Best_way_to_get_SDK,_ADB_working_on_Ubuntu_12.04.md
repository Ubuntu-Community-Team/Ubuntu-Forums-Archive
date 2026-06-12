---
title: "Best way to get SDK, ADB working on Ubuntu 12.04"
date: 2012-09-11
forum: General Help
---

### Post by AndyOpie150 on 2012-09-11
I been trying to read up on this subject, but it seems like here (Ubuntu Forums)is where I will get the best answer to my questions.

A. Which version of the Java JDK works best on Ubuntu 12.04 (JDK 6 or 7)
B. How would I get the Android SDK set up properly to allow the use of the adb and fastboot commands so I can give commands to my phone through the computer.
C. Will this allow the use of the Android Emulators from the SDK to function properly.

---

### Post by rifter on 2012-09-11
I was reading about this too.  The problem is that for some reason Oracle decided not to let Ubuntu create deb packages for java, which is like the bad old days.  Here's the community description:

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

     Now, following that, I went to the following site and was able to add a repository for java.  What it really does is downloads the script they wrote, which downloads and installs the latest version:
[http://www.duinsoft.nl/packages.php?t=en](http://www.duinsoft.nl/packages.php?t=en)

     Now I have java on my system and in my browsers.  However the problem I see now is that the whatprovides is not updated so apt/synaptic have no clue that I have java, and the problem I had when I started is still there in that anything I want to install that needs java will go and force icedtea and iceweasel and whatever else with the openjdk stuff on me.  I have always thought it was great that there is an open java project, but the problem is that their software has never ever worked for me.  It not only didn't work for the java sites and programs I needed to run, but the plugin messed up browser performance and casued lockups.  So while there are many reasons to hate oracle, and yes the closed nature of java is mostly to blame here, I've always ended up getting the "real" java.

     So I hate to piggyback on your question but I think the answer of "oh and by the way how do I do this so that the system knows we have java installed" is an unspoken part of your question and the links above should help you in any case.  I would guess that if I made my own .deb I could say it provides java.. that may be what I have to do.  If there is an easier solution I would be glad to hear it.  I'm really not sure why we can't have something in the repository anyway because java and flash always downloaded the software from their respective sites anyway, which would, I would think, have avoided the distribution issue...

---

### Post by AndyOpie150 on 2012-09-11
Thanks for all the links and Quid pro quo.

EDIT: I read something about Soupkit over at XDA-Developers and managed to download the .zip, but I was in the middle of trying all the Ubuntu 12.04 distros and forgot where I saw the info and download link at. I think it was originally designed for the Kindle fire but might work on the Ubuntu distro. I need to remember where the threads are at so I can read up on it some more.

---

### Post by AndyOpie150 on 2012-09-12
Well, so far I have managed to get the SDK, Eclipse with the ADT plugins and the Java JDK6 installed. I can now give my phone shell commands through the computer (swapped recovery's on the phone using the terminal just to verify).

Installed Wine.

Now it's on to seeing if I can figure out how to set up QtADB to work, then try to find something similar to APK Tool that will work in Linux.

Then I will try and see if the Android OS Emulators I downloaded with the SDK Manager will work in Linux.

Any help would be greatly appreciated.

---

### Post by lykeion on 2012-09-12
Hi, sorry if I don't get what you are asking for here, but as far as your first three questions:
A) JDK 6 is recommended
B) Just download Android SDK and extract the archive to any folder
C) Yes

I don't see why you'd need to install wine or use external programs like QtADB or any "APK tool"

**Running the emulator**:
1. Open terminal and go to folder where you extracted Android SDK, then go to subfolder "tools"
2. Create AVD:
```
./android create avd -n MyAVD -t 1
```
3. Launch emulator with created AVD:
```
./emulator -avd MyAVD
```

**Install an .apk file on device**:
Use this command (from the same "tools" subfolder as above)
```
./adb install filename.apk
```

More info on the tools included in Android SDK here:
[http://developer.android.com/tools/help/index.html](http://developer.android.com/tools/help/index.html)

Not sure what your questions on fastboot are, but here's a link to get you started:
[http://source.android.com/source/building-devices.html](http://source.android.com/source/building-devices.html)

---

### Post by AndyOpie150 on 2012-09-13
Thanks lykeion.
I just got ScreenCast configured so I can display my Android phones screen on the computers screen (I use this for making video tutorials and Intro's). This additional info will help greatly.

Things are coming along nicely. Now if I can find a Utility program similar to "APK Multi-Tool", but for Linux, so I can extract/open/edit .apks and .jar files, I'll be steaming right along in the right direction.

 The plan is to create ROM's for my phone from porting over ROM's from other Android devices, and eventually from source code. Maybe learn to develop .apks as well
Seeings how I'm fairly new to computers and Android devices I need to get as much help as I can from the Utility Programs so it will be one less thing I need to learn, and I can concentrate on learning how to develop the ROM and kernel (I'm 49 and don't have as much time to learn, plus my memory capacity has diminished greatly)

As I have no formal education beyond the Tenth Grade I also don't have the knowledge of how to go about achieving my goal, other than trail and ERROR and the occasional help from people such as yourself.

Got a chance to port one ROM over, with the help of several others with the same device as me. Now I'm hooked.

Note: Fastboot commands seem to be very useful for kernel development on the android device and to get you out of a boo boo (That's the only way I seem to know how to learn. Bricked my first android device just one month after owning it and don't plan on doing that again).

---

### Post by lykeion on 2012-09-14
Well, good luck and if you have any more specific question maybe I or someone else at this forum might be of help. But you might get more help at a more specialized Android forum like: [http://forum.xda-developers.com](http://forum.xda-developers.com)

---

### Post by AndyOpie150 on 2012-09-14
I'll try to keep my questions here directed solely to what applications are compatible with Ubuntu 12.04 or How to get some package or application to work in Ubuntu 12.04, or what is best for doing a particular task in Ubuntu 12.04.

This will take me a year or so of learning just to end up where I think I should be as far as ROM development. Plenty of Questions for other forums.

---

### Post by AndyOpie150 on 2012-09-17
Managed to get QtADB to work. I Had already installed Wine, before downloading the linux version of QtADB.

I had to right click the .exe and select properties. Then I selected permissions and clicked on the Execute box. Clicked out and double left clicked the .exe. This gave me a pop up window that asked for the path to the adb.exe and the aapt.exe. I selected the SDK/platform-tools folder, where the .exe's are located.

After plugging in my phone to the computer and double left clicking on the QtADB.exe I can now drag and drop any file on my computer to anyplace on my phone and vice-a-versa. That includes the SD card directory. I can also delete or edit any file as well, no need to select the USB option in the dropdown.

---


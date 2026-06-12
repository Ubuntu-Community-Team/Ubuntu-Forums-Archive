---
title: "Google Earth installs fine but crashes instantly upon launch"
date: 2010-09-17
forum: General Help
---

### Post by MockY on 2010-09-17
I just installed Google Earth on a laptop running Lucid Lynx using the googleearth-package method (method 2 from [**THIS**]("http://tombuntu.com/index.php/2010/05/02/how-to-install-google-earth-in-ubuntu-10-04/") site).
The install was successful but as soon as I see the splash screen, it crashes and gives me the following message:
```

** (process:10047): DEBUG: NP_Initialize
** (process:10047): DEBUG: NP_Initialize succeeded
Google Earth has caught signal 11.

We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data have been written
 to this text file:

    /home/user/.googleearth/crashlogs/crashlog-4c93c369.txt

Please include this file if you submit a bug report to Google.


```
The error log that it produces looks like this
```

Major Version 5
Minor Version 2
Build Number 0001
Build Date Sep  1 2010
Build Time 11:25:42
OS Type 3
OS Major Version 2
OS Minor Version 6
OS Build Version 32
OS Patch Version 0
Crash Signal 11
Crash Time 1284748547
Up Time 1.43881

Stacktrace from glibc:
/usr/lib/googleearth/libgoogleearth_free.so(+0xd090b)[0xb781390b]
[0xb786c400]
/usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so(NP_GetMIMEDescription+0x2da)[0xa704a6ea]
/usr/lib/googleearth/libQtWebKit.so.4(+0x747d18)[0xb63e0d18]
/usr/lib/googleearth/libQtWebKit.so.4(+0x6062ff)[0xb629f2ff]
/usr/lib/googleearth/libQtWebKit.so.4(+0x604516)[0xb629d516]
/usr/lib/googleearth/libQtWebKit.so.4(+0x60476a)[0xb629d76a]
/usr/lib/googleearth/libQtWebKit.so.4(+0x712beb)[0xb63abbeb]
/usr/lib/googleearth/libQtWebKit.so.4(+0x5b1595)[0xb624a595]
/usr/lib/googleearth/libQtWebKit.so.4(+0x5a185c)[0xb623a85c]
/usr/lib/googleearth/libQtWebKit.so.4(+0x5b1981)[0xb624a981]
/usr/lib/googleearth/libQtWebKit.so.4(+0x5b199a)[0xb624a99a]
/usr/lib/googleearth/libQtWebKit.so.4(+0xaa2c4b)[0xb673bc4b]
/usr/lib/googleearth/libQtWebKit.so.4(+0x16ad57)[0xb5e03d57]
/usr/lib/googleearth/libQtWebKit.so.4(+0x1749d5)[0xb5e0d9d5]
/usr/lib/googleearth/libQtWebKit.so.4(+0x183282)[0xb5e1c282]
/usr/lib/googleearth/libQtWebKit.so.4(+0x1bc22d)[0xb5e5522d]
/usr/lib/googleearth/libQtWebKit.so.4(+0x29ac5d)[0xb5f33c5d]
/usr/lib/googleearth/libQtWebKit.so.4(+0x2a9410)[0xb5f42410]
/usr/lib/googleearth/libQtWebKit.so.4(+0x2a9f72)[0xb5f42f72]
/usr/lib/googleearth/libQtWebKit.so.4(+0x2b7fea)[0xb5f50fea]
/usr/lib/googleearth/libQtWebKit.so.4(+0x4be45a)[0xb615745a]
/usr/lib/googleearth/libQtWebKit.so.4(+0x4bf243)[0xb6158243]
/usr/lib/googleearth/libQtWebKit.so.4(+0x4c0449)[0xb6159449]
/usr/lib/googleearth/libQtWebKit.so.4(+0x4c2a75)[0xb615ba75]
/usr/lib/googleearth/libQtWebKit.so.4(+0x4c36b8)[0xb615c6b8]
/usr/lib/googleearth/libQtWebKit.so.4(+0x4c6773)[0xb615f773]
/usr/lib/googleearth/libQtWebKit.so.4(+0x501706)[0xb619a706]
/usr/lib/googleearth/libQtWebKit.so.4(+0x5017fb)[0xb619a7fb]
/usr/lib/googleearth/libQtWebKit.so.4(+0x539f0b)[0xb61d2f0b]
/usr/lib/googleearth/libQtWebKit.so.4(+0x54c290)[0xb61e5290]
/usr/lib/googleearth/libQtWebKit.so.4(+0x547cc3)[0xb61e0cc3]
/usr/lib/googleearth/libQtWebKit.so.4(+0x6fd155)[0xb6396155]
/usr/lib/googleearth/libQtWebKit.so.4(+0x6fd83e)[0xb639683e]
/usr/lib/googleearth/libQtCore.so.4(_ZN11QMetaObject8metacallEP7QObjectNS_4CallEiPPv+0x3f)[0xb74f75a7]
/usr/lib/googleearth/libQtCore.so.4(_ZN14QMetaCallEvent13placeMetaCallEP7QObject+0x24)[0xb74ff5ec]
/usr/lib/googleearth/libQtCore.so.4(_ZN7QObject5eventEP6QEvent+0x185)[0xb750003d]
/usr/lib/googleearth/libQtGui.so.4(_ZN19QApplicationPrivate13notify_helperEP7QObjectP6QEvent+0xa0)[0xb6c6fe20]
/usr/lib/googleearth/libQtGui.so.4(_ZN12QApplication6notifyEP7QObjectP6QEvent+0x22e)[0xb6c79962]
/usr/lib/googleearth/libQtCore.so.4(_ZN16QCoreApplication14notifyInternalEP7QObjectP6QEvent+0x70)[0xb74f1d50]
/usr/lib/googleearth/libQtCore.so.4(_ZN23QCoreApplicationPrivate16sendPostedEventsEP7QObjectiP11QThreadData+0x22d)[0xb74f2989]
/usr/lib/googleearth/libQtCore.so.4(_ZN20QEventDispatcherUNIX13processEventsE6QFlagsIN10QEventLoop17ProcessEventsFlagEE+0x37)[0xb751794b]
/usr/lib/googleearth/libQtGui.so.4(+0x1d3ca4)[0xb6d04ca4]
/usr/lib/googleearth/libQtCore.so.4(_ZN10QEventLoop13processEventsE6QFlagsINS_17ProcessEventsFlagEE+0x47)[0xb74f0fbf]
/usr/lib/googleearth/libQtCore.so.4(_ZN10QEventLoop4execE6QFlagsINS_17ProcessEventsFlagEE+0xff)[0xb74f1223]
/usr/lib/googleearth/libQtCore.so.4(_ZN16QCoreApplication4execEv+0x9d)[0xb74f2c05]
/usr/lib/googleearth/libQtGui.so.4(_ZN12QApplication4execEv+0x25)[0xb6c6f7a1]
/usr/lib/googleearth/libgoogleearth_free.so(_ZN5earth6client11Application3runEv+0x4bc)[0xb781eb0c]
/usr/lib/googleearth/libgoogleearth_free.so(earthmain+0x27d)[0xb7812d3d]
/usr/lib/googleearth/googleearth-bin(_init+0x12e)[0x80486d2]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6)[0xb5b2fbd6]
/usr/lib/googleearth/googleearth-bin(_init+0x9d)[0x8048641]

```
I looked around and I'm not alone with this issue, but no one seems to have the answer. I found a website that claims solve the issue, but the directories mentioned does not exist. Take a look [**HERE**]("http://www.kaliphonia.com/content/notes/how-to-fix-google-earth-crash-on-ubuntu-1004-lucid-lynx")

Anyone have an idea or a solution?

---

### Post by AlphaLexman on 2010-09-17
Check out: [http://www.google.com/support/forum/...0dd9254e&hl=en](http://www.google.com/support/forum/...0dd9254e&hl=en)
The 'best answer' section.

---

### Post by LowSky on 2010-09-17
you really should have used method 1 to install

---

### Post by MockY on 2010-09-17
> **AlphaLexman said:**
> Check out: [http://www.google.com/support/forum/...0dd9254e&hl=en](http://www.google.com/support/forum/...0dd9254e&hl=en)
The 'best answer' section.
The requested URL was not found on this server.

---

### Post by MockY on 2010-09-17
> **LowSky said:**
> you really should have used method 1 to install
Why would that be better? As far as I am aware, the version available in that repo is outdated. Furthermore, I've seen people reporting the same issue when installing it with that method as well.

---

### Post by AlphaLexman on 2010-09-17
> **MockY said:**
> The requested URL was not found on this server.
Sorry, follow the link in my post here: [http://ubuntuforums.org/showthread.php?t=891425](http://ubuntuforums.org/showthread.php?t=891425)

---

### Post by MockY on 2010-09-17
Hmm. I hurried up and unchecked the "Show tip on startup" before GE crashed and now it runs just fine as far as I can tell (have not used it much yet). So for some reason, the tip window that opens automatically when GE is launched seems to crash it. Very odd, but so far so goos. No crash so far once I unchecked it (though you have to be very quick to do it).

---

### Post by AlphaLexman on 2010-09-17
Then look at the files in:
```
~/.googleearth/crashlogs/
```

---

### Post by Skipnaz on 2010-09-18
MockY
I had the same problem. I had to untick the box and press the button. It took me about 10 tries to linup my cursor directly where the tic box appears but I got it and its working. Strange bug

---

### Post by snakeman21 on 2010-09-19
> **Skipnaz said:**
> MockY
I had the same problem. I had to untick the box and press the button. It took me about 10 tries to linup my cursor directly where the tic box appears but I got it and its working. Strange bug

This did not work for me.  I tried several times, and successfully unchecked the box on more than one occasion.  But Google Earth still crashes every time I start it, and always re-checks the box.

Edit:  I stumbled across this:  [http://tombuntu.com/index.php/2010/05/02/how-to-install-google-earth-in-ubuntu-10-04/](http://tombuntu.com/index.php/2010/05/02/how-to-install-google-earth-in-ubuntu-10-04/)

I am currently trying this method.  I will report back shortly.

SUCCESS!  I Think I found the answer.  Go into you Google Earth directory, and find the uninstall file.  It should be organized as the last file.  Run this file, and then follow my link.  It gives you a link to download a .deb file.  Choose your architecture (i386 or amd64) and download this .deb and install it normally.  Everything should work.  Alternatively, you could enable the Medibuntu repository and simply use apt-get to install.  Then, save the .deb file to a flash drive so you can share it with your fellow Google Earth-craving linux nerds.  :D

---

### Post by Skipnaz on 2010-09-19
snakeman21
I also had to press the button to the right of the checkbox. If you did both I don't know what to tell ya

---

### Post by snakeman21 on 2010-09-19
> **Skipnaz said:**
> snakeman21
I also had to press the button to the right of the checkbox. If you did both I don't know what to tell ya

Yeah I did that.  But if you check my post, I found a solution anyways, so all is well.  :D

---

### Post by sepedatua on 2010-09-25
Perhaps in your case the directory is:
```
 
/home/user/google-earth

```

---

### Post by aranwe on 2010-09-30
> **snakeman21 said:**
> This did not work for me.  I tried several times, and successfully unchecked the box on more than one occasion.  But Google Earth still crashes every time I start it, and always re-checks the box.

Edit:  I stumbled across this:  [http://tombuntu.com/index.php/2010/05/02/how-to-install-google-earth-in-ubuntu-10-04/](http://tombuntu.com/index.php/2010/05/02/how-to-install-google-earth-in-ubuntu-10-04/)

I am currently trying this method.  I will report back shortly.

SUCCESS!  I Think I found the answer.  Go into you Google Earth directory, and find the uninstall file.  It should be organized as the last file.  Run this file, and then follow my link.  It gives you a link to download a .deb file.  Choose your architecture (i386 or amd64) and download this .deb and install it normally.  Everything should work.  Alternatively, you could enable the Medibuntu repository and simply use apt-get to install.  Then, save the .deb file to a flash drive so you can share it with your fellow Google Earth-craving linux nerds.  :D

It work for me. Tnx

---

### Post by petegreenhorn on 2010-10-04
Hi if anyone is interested in my solution to this ,here it is 
Quickly close the useful tips box goto-tools options-general and untick show tips at startup. end of problem . Not an expert but i reackon it should be a fairly simple fix for the guys at google

---

### Post by snakeman21 on 2010-10-04
> **petegreenhorn said:**
> Hi if anyone is interested in my solution to this ,here it is 
Quickly close the useful tips box goto-tools options-general and untick show tips at startup. end of problem . Not an expert but i reackon it should be a fairly simple fix for the guys at google

That was mentioned.  From what I've read, it **usually** works.  In my case, however, it didn't work.  I did find a solution in case disabling the startup tips does not work.

---

### Post by YAFU on 2010-10-11
Hello.
Same problem in Kubuntu 10.04 Lucid 64bits and Google Earth from Medibuntu or official .bin.
My crash log shows:
> Major Version 5
Minor Version 1
Build Number 3533
Build Date Nov 11 2009
Build Time 16:41:31
OS Type 11
OS Major Version 2
OS Minor Version 6
OS Build Version 35
OS Patch Version 0
Crash Signal 11
Crash Time 1286822132
Up Time 36.4524

Stacktrace from glibc:
/usr/lib32/googleearth/googleearth-bin[0x805caa6]
[0xf77cc400]

In my case, the problem is with Lucid ia32 libraries. To solve, uninstall "lib32stdc++5" and "ia32-libs-gtk" if you have them installed. Then download "ia32-libs" Maverick package from Ubuntu Packages:
[http://packages.ubuntu.com/maverick/ia32-libs](http://packages.ubuntu.com/maverick/ia32-libs)

and install it.

The problem with Google Earth is closed at start is resolved. But as in Maverick I have some other problems, such as seeing a few lines on maps. I have also read that Ubuntu 10.10 users do not have that problem. Perhaps it only happens on Kubuntu.
Greetings.

---

### Post by systembreak on 2010-10-21
Why make it so complicated, the .deb file from Medibuntu works. Download the .deb file from here:

[http://packages.medibuntu.org/lucid/googleearth.html](http://packages.medibuntu.org/lucid/googleearth.html)

---

### Post by davidsrsb on 2010-11-09
That is an ancient 5.1.x package.
The current 5.2.x has the very useful terrain profile feature among other features

---

### Post by snakeman21 on 2010-11-10
> **davidsrsb said:**
> That is an ancient 5.1.x package.
The current 5.2.x has the very useful terrain profile feature among other features

I love the 3d terrain and 3d buildings... So cool!  I actually used 3d buildings to get my bearings when I had to travel through NYC.

---

### Post by snakeman21 on 2010-11-10
> **aranwe said:**
> It work for me. Tnx

NP.  Happy I could help!

---

### Post by okkie on 2010-11-11
I have been struggeling for more than a year now.Will try and report back.
Thanks

---

### Post by okkie on 2010-11-11
I went to synaptic to uninstall the standard package to get the .deb file from medibuntu and the following happened:
see screenshots [ATTACH]175297[/ATTACH]

[ATTACH]175298[/ATTACH]

---

### Post by snakeman21 on 2010-11-11
> **okkie said:**
> I went to synaptic to uninstall the standard package to get the .deb file from medibuntu and the following happened:
see screenshots [ATTACH]175297[/ATTACH]

[ATTACH]175298[/ATTACH]

Looks like that had nothing to do with google earth, but instead a problem with dpkg.  Try following the link I posted and downloading the .deb directly.

---


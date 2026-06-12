---
title: "Ubuntu 10.04 and google earth"
date: 2010-05-01
forum: General Help
---

### Post by Maweni on 2010-05-01
Hi Folks,

I have been using Ubuntu for about a year and have had very few problems. Today I upgraded from 9.1 to 10.04 and have been very pleased till I started using Google Earth. Please look at the attached pic...

I have also tried removing and reinstalling with the latest version of Google Earth with no luck. Does anyone have any ideas on how I could fix this?

I am using ubuntu 10.04 notebook on a Toshiba Satellite notebook.

---

### Post by crete_des_izards on 2010-05-02
Snap! I get exactly the same problem. When GE starts up it all looks good, it's only when I start to zoom in that the problems appear, as you approach street-level it becomes completely unusable. I'm using a HP 6715s with AMD 64 & with an ATI card. I've tried turning atmosphere, 13/32 bit colour, safe graphics mode etc. on & off but it makes no difference.

---

### Post by scouser73 on 2010-05-02
My suggestion would be to remove and reinstall Google Earth.

**1** - Back up any place marks and to completely delete the **.googleearth** profile 
**2** - Go in to the **.config** folder and remove **GECommonSettings.conf** & **GoogleEarthPlus.conf**

---

### Post by Maweni on 2010-05-02
This did not work. I am still having the same problem.

Any other suggestions?

---

### Post by dcstar on 2010-05-03
> **Maweni said:**
> This did not work. I am still having the same problem.

Any other suggestions?

I use Google Earth installed via this method and it works fine:

[https://help.ubuntu.com/community/GoogleEarth#make-googleearth-package](https://help.ubuntu.com/community/GoogleEarth#make-googleearth-package)

---

### Post by SRTS on 2010-05-03
I noticed that compiz which is enabled by default can mess up java-related windows layouts and contents, both of sun-java and openjdk! Maybe your problem is similar? Just to make sure, you could go to System/Preferences/Appearence and set effects to "none" and try google earth again.

---

### Post by singercs on 2010-05-03
Thanks to dcstar, easy way to do it and is it ever fast.
works great.

---

### Post by captain_rob on 2010-05-03
Didn't work for me too. I totally removed GE, also the config settings. After that downloaded GE package. But the same problem exists. I am using no visual effects. And placing GE in safe mode gives no solution. In Ubuntu 9.10  I had no problem at all. GE worked perfectly, but now its unusable.:(

---

### Post by alliance1975 on 2010-05-05
I am having the exact same problem. GE worked fine under 9.10 and I thought all th eproblems were solved. I would guess it is the inferior ATI drivers that come with Ubuntu. For older cards like my xpress 200m they are the only alternative.

---

### Post by Bob2893 on 2010-05-06
I have a related problem, I think. G Earth opens for about 1 second then disappears completely. Openshot won't open at all. These two bugs on my HP Compac duo, 

Another machine, older P4 Compac, doesnt have these problems at all.

Bob

---

### Post by alliance1975 on 2010-05-06
Despite all the suggested uninstall, reinstall recommendations GE continues to misbehave. After a few minutes it just shuts down altogether. What's really annoying is that it worked before. Why was it changed?

---

### Post by alliance1975 on 2010-05-06
bump

---

### Post by edantes on 2010-05-08
> **alliance1975 said:**
> bump

Confirmed as a bug in the xorg ati driver:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/570879](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/570879)

---

### Post by alliance1975 on 2010-05-10
Thank you edantes. I am currently subscribed to launchpad bug report # 574034, "google earth does not render any zoom level with ATI Radeon Xpress 200M video graphics adaptor Ubuntu » “xserver-xorg-video-ati” package", in hopes that a solution will present itself. I will add #570879 to my subscriptions. I wish I could help but my knowledge of Ubuntu is limited to being a mere bystander.

---

### Post by Rob6 on 2010-06-28
I had the same plroblem. I edited my x configuration file - now it's ok. It's smth with your xorg.conf. Attach your /etc/X11/xorg.conf if u have it.

---

### Post by grenoml on 2010-06-28
Just ran into this problem here as well.

Ubuntu 10.04 desktop.

Installed package from medibuntu.

GE starts with message about low res.  But my screen is set at 1280x800 so I don't know why it's complaining.  Then the splash screen appears for about 1 second and then it dies with a segfault.

Major Version 5
Minor Version 1
Build Number 3533
Build Date Nov 11 2009
Build Time 16:41:31
OS Type 11
OS Major Version 2
OS Minor Version 6
OS Build Version 32
OS Patch Version 0
Crash Signal 11
Crash Time 1277761920
Up Time 4.53296

Stacktrace from glibc:
/usr/lib32/googleearth/googleearth-bin[0x805caa6]
[0xf7740400]
/usr/lib32/mesa/libGL.so.1(glXMakeCurrent+0x23)[0xf4cd2f33]
/usr/lib32/googleearth/libIGGfx.so(_ZN3Gap3Gfx18igOglVisualContext19internalMakeCurrentEv+0x2c)[0xf1ecbe8c]
/usr/lib32/googleearth/libIGGfx.so(_ZN3Gap3Gfx18igOglVisualContext21internalCreateContextEv+0x152)[0xf1ecc052]
/usr/lib32/googleearth/libIGGfx.so(_ZN3Gap3Gfx18igOglVisualContext4openEv+0x89)[0xf1eec4e9]
/usr/lib32/googleearth/libevll.so(_ZN5earth4evll13VisualContext11OpenContextEN3Gap3Gfx25igRenderDestinationFormatERKNS0_8InitInfoE+0xfb)[0xf1b42b1b]
/usr/lib32/googleearth/libevll.so(_ZN5earth4evll13VisualContext4initERKNS0_8InitInfoE+0x167)[0xf1b42cc7]
/usr/lib32/googleearth/libevll.so(_ZN5earth4evll17RenderContextImpl4initERKNS0_8InitInfoE+0x81)[0xf1a4e8a1]
/usr/lib32/googleearth/librender.so(_ZN12RenderWidget6SetApiEPN5earth4evll3APIE+0x47)[0xf4ed1817]
/usr/lib32/googleearth/librender.so(_ZN5earth6render12RenderWindow12createWidgetEv+0xa7)[0xf4eb8757]
/usr/lib32/googleearth/libgoogleearth_lib.so(_ZN5earth6client12ModuleWidget9showEventEP10QShowEvent+0x94)[0xf5c166f4]
/usr/lib32/libQtGui.so.4(_ZN7QWidget5eventEP6QEvent+0x392)[0xf6aa9662]
/usr/lib32/libQtGui.so.4(_ZN19QApplicationPrivate13notify_helperEP7QObjectP6QEvent+0xac)[0xf6a4b4dc]
/usr/lib32/libQtGui.so.4(_ZN12QApplication6notifyEP7QObjectP6QEvent+0x219)[0xf6a520f9]
/usr/lib32/libQtCore.so.4(_ZN16QCoreApplication14notifyInternalEP7QObjectP6QEvent+0x7b)[0xf74faa3b]
/usr/lib32/libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x165)[0xf6aaf4a5]
/usr/lib32/libQtGui.so.4(_ZN14QWidgetPrivate14show_recursiveEv+0x83)[0xf6aaf6c3]
/usr/lib32/libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0xbc)[0xf6aaf7bc]
/usr/lib32/libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x61)[0xf6aaf3a1]
/usr/lib32/libQtGui.so.4(_ZN7QWidget10setVisibleEb+0x1eb)[0xf6ab199b]
/usr/lib32/libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0x168)[0xf6aaf868]
/usr/lib32/libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x61)[0xf6aaf3a1]
/usr/lib32/libQtGui.so.4(_ZN14QWidgetPrivate14show_recursiveEv+0x83)[0xf6aaf6c3]
/usr/lib32/libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0xbc)[0xf6aaf7bc]
/usr/lib32/libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x61)[0xf6aaf3a1]
/usr/lib32/libQtGui.so.4(_ZN7QWidget10setVisibleEb+0x1eb)[0xf6ab199b]
/usr/lib32/libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0x168)[0xf6aaf868]
/usr/lib32/libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x61)[0xf6aaf3a1]
/usr/lib32/libQtGui.so.4(_ZN7QWidget10setVisibleEb+0x1eb)[0xf6ab199b]
/usr/lib32/libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0x168)[0xf6aaf868]
/usr/lib32/libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x61)[0xf6aaf3a1]
/usr/lib32/libQtGui.so.4(_ZN7QWidget10setVisibleEb+0x1eb)[0xf6ab199b]
/usr/lib32/libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0x168)[0xf6aaf868]
/usr/lib32/libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x61)[0xf6aaf3a1]
/usr/lib32/libQtGui.so.4(_ZN7QWidget10setVisibleEb+0x1eb)[0xf6ab199b]
/usr/lib32/libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0x168)[0xf6aaf868]
/usr/lib32/libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x61)[0xf6aaf3a1]
/usr/lib32/libQtGui.so.4(_ZN7QWidget10setVisibleEb+0x1eb)[0xf6ab199b]
/usr/lib32/libQtGui.so.4(_ZN7QWidget10showNormalEv+0x72)[0xf6a9ee62]
/usr/lib32/googleearth/libgoogleearth_lib.so(_ZN10MainWindow18readScreensizeInfoEv+0xbeb)[0xf5bf21db]
/usr/lib32/googleearth/libgoogleearth_lib.so(_ZN5earth6client11Application12SetupMainWinENS0_3Kvw7ProductEb+0x282)[0xf5c3be82]
/usr/lib32/googleearth/libgoogleearth_lib.so(_ZN5earth6client11Application3runEv+0x3a9)[0xf5c43df9]
/usr/lib32/googleearth/googleearth-bin[0x805c77a]
/lib32/libc.so.6(__libc_start_main+0xe6)[0xf59dbbd6]
/usr/lib32/googleearth/googleearth-bin[0x805be71]

---

### Post by grenoml on 2010-06-28
I tried building GE using googleearth-package as well.  I get the exact same result as before.

---

### Post by Rob6 on 2010-06-29
**grenoml**
Try installing fusion-icon (comzpiz), run it, choose metacity windows manager. Run GE
PS Wwhich video card do u have?

---

### Post by grenoml on 2010-06-29
There is no GPU.  This is OpenGL only - software rendering.  It's on a headless machine.

I'll try Compiz.  How would that help?

---

### Post by grenoml on 2010-06-29
Cannot use Compiz on machine with no GPU.  It won't let you do it.

But there is no reason that GE shouldn't work with OpenGL using software rendering.  And seeing all the huge number of postings about problems with Lucid and Google Earth in various forums whether w/GPU or without there is obviously something wrong with these latest versions of GE.

---

### Post by daniroma on 2010-07-08
I have installed GE as described by [dcstar]("http://ubuntuforums.org/member.php?u=7532"). [https://help.ubuntu.com/community/GoogleEarth#make-googleearth-package](https://help.ubuntu.com/community/GoogleEarth#make-googleearth-package)
My problem is that GE start, show notification window, then close without any message.
Can anyone tell me why is that happen?
Thank you.

I use 
Ubuntu 10.04 (lucid)-32bit, kernel 2.6.32-23-generic.

---

### Post by Dumpy Dumpster on 2010-07-11
Exactly the same problem as daniroma.
Uninstalled and reinstalled, but still the same problem.
Is it Google or 10.04 at fault?

---

### Post by llanitedave on 2010-07-11
> **Dumpy Dumpster said:**
> Exactly the same problem as daniroma.
Uninstalled and reinstalled, but still the same problem.
Is it Google or 10.04 at fault?

This definitely needs to be bumped.  I'm having the same problem on a Dell Vostro 1720 laptop in Lucid.  It's running fine however on my AMD64 desktop, and on Windows 7 on the same laptop.

It's pretty embarrassing to have to reboot and log into Windows just to run Google Earth!

---

### Post by Famicube64 on 2010-07-11
It's Google Earth that's the problem. The older version in the Medibuntu repo works still.

---

### Post by Elmer Fudd on 2010-07-16
Tried all remedies in this thread. Same problem. Starts, shows GE splash then shuts down.  Worked on 9.10.

Lucid
2.6.32

---

### Post by littleoak on 2010-08-04
seems we have the same problem, sometimes shows the first screen for about a second.

---

### Post by uRock on 2010-08-04
I installed the download from Google and it works fine for me. 64bit Lucid.

---


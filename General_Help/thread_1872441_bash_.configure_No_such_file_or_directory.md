---
title: "bash: ./configure: No such file or directory"
date: 2011-10-30
forum: General Help
---

### Post by NorthlandSauce on 2011-10-30
Hey people. My Linux college book doesn't really explain this so maybe it'll help here, kind of a noob question. I'm trying to install Android SDK and I get stuck at "bash: ./configure: No such file or directory" before I can move on installing it. 

ian@Sauce:~$ cd /home/ian/android
ian@Sauce:~/android$ ls
[COLOR=Red]android-sdk_r15-linux.tgz[/COLOR]
ian@Sauce:~/android$ tar -zxvf android-sdk_r15-linux.tgz
android-sdk-linux/
android-sdk-linux/platforms/
android-sdk-linux/add-ons/
android-sdk-linux/SDK Readme.txt
android-sdk-linux/tools/
android-sdk-linux/tools/emulator
android-sdk-linux/tools/etc1tool
android-sdk-linux/tools/layoutopt
android-sdk-linux/tools/android
android-sdk-linux/tools/proguard/
android-sdk-linux/tools/proguard/bin/
android-sdk-linux/tools/proguard/bin/proguard.sh
android-sdk-linux/tools/proguard/bin/retrace.sh
android-sdk-linux/tools/proguard/bin/proguardgui.sh
android-sdk-linux/tools/proguard/GPL.html
android-sdk-linux/tools/proguard/lib/
android-sdk-linux/tools/proguard/lib/proguardgui.jar
android-sdk-linux/tools/proguard/lib/proguard.jar
android-sdk-linux/tools/proguard/lib/retrace.jar
android-sdk-linux/tools/proguard/GPL_exception.html
android-sdk-linux/tools/proguard/license.html
android-sdk-linux/tools/proguard/ant/
android-sdk-linux/tools/proguard/ant/task.properties
android-sdk-linux/tools/lib/
android-sdk-linux/tools/lib/devices.xml
android-sdk-linux/tools/lib/emulator/
android-sdk-linux/tools/lib/emulator/snapshots.img
android-sdk-linux/tools/lib/jfreechart-1.0.9-swt.jar
android-sdk-linux/tools/lib/swing-worker-1.1.jar
android-sdk-linux/tools/lib/proguard.cfg
android-sdk-linux/tools/lib/chimpchat.jar
android-sdk-linux/tools/lib/jsilver.jar
android-sdk-linux/tools/lib/build.template
android-sdk-linux/tools/lib/libEGL_translator.so
android-sdk-linux/tools/lib/sdklib.jar
android-sdk-linux/tools/lib/androidprefs.jar
android-sdk-linux/tools/lib/x86/
android-sdk-linux/tools/lib/x86/swt.jar
android-sdk-linux/tools/lib/emma.jar
android-sdk-linux/tools/lib/guavalib.jar
android-sdk-linux/tools/lib/android.el
android-sdk-linux/tools/lib/libOpenglRender.so
android-sdk-linux/tools/lib/monkeyrunner.jar
android-sdk-linux/tools/lib/commons-logging-1.1.1.jar
android-sdk-linux/tools/lib/libGLES_V2_translator.so
android-sdk-linux/tools/lib/mkidentity.jar
android-sdk-linux/tools/lib/common.jar
android-sdk-linux/tools/lib/x86_64/
android-sdk-linux/tools/lib/x86_64/swt.jar
android-sdk-linux/tools/lib/httpcore-4.1.jar
android-sdk-linux/tools/lib/plugin.prop
android-sdk-linux/tools/lib/org.eclipse.equinox.common_3.4.0.v20080421-2006.jar
android-sdk-linux/tools/lib/org.eclipse.core.commands_3.4.0.I20080509-2000.jar
android-sdk-linux/tools/lib/org.eclipse.jface_3.4.2.M20090107-0800.jar
android-sdk-linux/tools/lib/ddms.jar
android-sdk-linux/tools/lib/sdkmanager.jar
android-sdk-linux/tools/lib/commons-compress-1.0.jar
android-sdk-linux/tools/lib/sdkuilib.jar
android-sdk-linux/tools/lib/uix.jar
android-sdk-linux/tools/lib/groovy-all-1.7.0.jar
android-sdk-linux/tools/lib/hardware-properties.ini
android-sdk-linux/tools/lib/traceview.jar
android-sdk-linux/tools/lib/layoutopt.jar
android-sdk-linux/tools/lib/httpclient-4.1.1.jar
android-sdk-linux/tools/lib/anttasks.jar
android-sdk-linux/tools/lib/jfreechart-1.0.9.jar
android-sdk-linux/tools/lib/emma_device.jar
android-sdk-linux/tools/lib/httpmime-4.1.1.jar
android-sdk-linux/tools/lib/ddmlib.jar
android-sdk-linux/tools/lib/jcommon-1.0.12.jar
android-sdk-linux/tools/lib/commons-codec-1.4.jar
android-sdk-linux/tools/lib/jython.jar
android-sdk-linux/tools/lib/swtmenubar.jar
android-sdk-linux/tools/lib/draw9patch.jar
android-sdk-linux/tools/lib/archquery.jar
android-sdk-linux/tools/lib/emma_ant.jar
android-sdk-linux/tools/lib/libGLES_CM_translator.so
android-sdk-linux/tools/lib/ddmuilib.jar
android-sdk-linux/tools/lib/pc-bios/
android-sdk-linux/tools/lib/pc-bios/bios.bin
android-sdk-linux/tools/lib/pc-bios/vgabios-cirrus.bin
android-sdk-linux/tools/lib/osgi.jar
android-sdk-linux/tools/lib/hierarchyviewerlib.jar
android-sdk-linux/tools/lib/hierarchyviewer2.jar
android-sdk-linux/tools/lib/sdkstats.jar
android-sdk-linux/tools/mksdcard
android-sdk-linux/tools/traceview
android-sdk-linux/tools/ddms
android-sdk-linux/tools/apkbuilder
android-sdk-linux/tools/source.properties
android-sdk-linux/tools/dmtracedump
android-sdk-linux/tools/NOTICE.txt
android-sdk-linux/tools/sqlite3
android-sdk-linux/tools/adb_has_moved.txt
android-sdk-linux/tools/emulator-x86
android-sdk-linux/tools/hierarchyviewer
android-sdk-linux/tools/monkeyrunner
android-sdk-linux/tools/hprof-conv
android-sdk-linux/tools/draw9patch
android-sdk-linux/tools/ant/
android-sdk-linux/tools/ant/build.xml
android-sdk-linux/tools/ant/pre_setup.xml
android-sdk-linux/tools/ant/NOTICE.txt
android-sdk-linux/tools/emulator-arm
android-sdk-linux/tools/zipalign
ian@Sauce:~/android$ ls
[COLOR=Blue]android-sdk-linux [/COLOR] [COLOR=Red]android-sdk_r15-linux.tgz[/COLOR]
ian@Sauce:~/android$ cd android-sdk-linux
**ian@Sauce:~/android/android-sdk-linux$ ./configure**
[B]bash: ./configure: No such file or directory

[/B]Help would be awesome, thanks.

---

### Post by azmyth on 2011-10-30
The results of you untar'ing doesn't show the configure file. Make sure it was extracted and make sure where it was extracted. Also, sometimes you have to do a chmod +x configure before it will run.

---

### Post by NorthlandSauce on 2011-10-30
Well I know it's in the right directory. chmod +x didn't work.

---

### Post by WorMzy on 2011-10-30
Like azmyth said, there was no configure in the tar. There is also no sourcecode, as far as I can tell. Are you sure you've got the right archive? What does the "SDK Readme.txt" have to say about whatever you've got there?

Edit: I found this: [http://developer.android.com/sdk/installing.html](http://developer.android.com/sdk/installing.html)

I recommend that you read through it.

---

### Post by lensman3 on 2011-10-30
This is fishing on my part, but is there a .configure  . Dot files don't list and to run the configure would be "./.configure".

I didn't see it being untar'ed either.

---

### Post by haqking on 2011-10-30
> **lensman3 said:**
> This is fishing on my part, but is there a .configure  . Dot files don't list and to run the configure would be "./.configure".

I didn't see it being untar'ed either.

a configure file would not be hidden (which is what the . means)

There is no configure file in that tar.

As mentioned above, best the OP reads the instructions for installing it

I would also start with reading the readme that was untar'd

---


---
title: "Installing Google Earth in 10.10"
date: 2011-01-17
forum: General Help
---

### Post by zbirdman777 on 2011-01-17
I've been attempting to install Google Earth for a couple of days now but no success.

Initially I downloaded the .deb package from google and installed that. Everything went smooth but Earth fails to launch. I tried running it through terminal and it returns. "Command not found".

So I completely removed it and installed the google earth package through terminal followed by the "ia32-libs" package. Compiled it with the following command:

"sudo make-googleearth-package --force"

there were a lot of errors and it finished. I think the error was that it couldn't retrieve information. Will try again if needed. I used dpkg to install it but I had exactly the same problem.

Did all of that again and used gdebi instead. Still google earth fails to launch.

I'm out of ideas at this point. Has anyone had any luck getting Google Earth to work and if so how?

---

### Post by jcolyn on 2011-01-17
Here ya go..first though delete the .deb package you downloaded from google..

If you want to install the latest current version of Googleearth follow these simple steps and you will have it up and running in no time.

First though you will need to purge any installs or attempts at installing Googleearth.

These terminal entries have to be entered exactly as typed below so you may want to copy/paste into your terminal.

To start: Open a terminal and enter ```
sudo apt-get install lsb-core
``` Once done enter ```
sudo apt-get install googleearth-package
``` After the package is installed enter ```
sudo make-googleearth-package --force
``` This process will take several minutes and you will see many warning notices but ignore them.

Once the above process is completed close the terminal and go to your /home folder where you will find a googleearth_xx.deb package. Double-click it and follow instructions.

Once installed you should have the Googleearth link in your Internet folder.

Enjoy

---

### Post by wizodd0 on 2011-01-17
> **jcolyn said:**
> 

First though you will need to purge any installs or attempts at installing Googleearth.


Ummm. How?

I've run every uninstall suggestion I can find, and then done this reinstall (tried others) but the BEST I get is it actually shows in the menu system and displays the flash screen upon execution--then it's gone.

There don't seem to be any log entries regarding it either.

---

### Post by jcolyn on 2011-01-17
> **wizodd0 said:**
> Ummm. How?

Open synaptic and type ```
googleearth 
``` in the searchbox. If either googleearth or googleearth-package has a green box next to it click it and check mark for complete removal. Do both. Once done follow the previous directions I posted..

---

### Post by wizodd0 on 2011-01-18
After uninstalling using synaptic, I deleted the .googleearth directory  and the /opt/google/earth directory and the icon which remained on the  menu.

I then reinstalled as per above,

Same results: splash&crash
log:

   	 	 	 	pre.western { font-family: "Times New Roman"; }pre.cjk { font-family: "DejaVu Sans",monospace; }p { margin-bottom: 0.08in; }  Major Version 6
Minor Version 0
Build Number 0001
Build Date Dec 10 2010
Build Time 22:42:27
OS Type 3
OS Major Version 2
OS Minor Version 6
OS Build Version 35
OS Patch Version 0
Crash Signal 11
Crash Time 1295388538
Up Time 1.0039

Stacktrace from glibc:
/usr/lib/googleearth/libgoogleearth_free.so(+0xac2a3)[0xb77292a3]
/usr/lib/googleearth/libgoogleearth_free.so(+0xac423)[0xb7729423]
[0xb7791400]
/usr/lib/googleearth/libIGGfx.so(_ZN3Gap3Gfx18igOglVisualContext22initGLWindowExtensionsEv+0x9f)[0xb2ce849f]
/usr/lib/googleearth/libIGGfx.so(_ZN3Gap3Gfx18igOglVisualContext4openEv+0xa3)[0xb2cf1313]
/usr/lib/googleearth/libevll.so(_ZN5earth4evll13VisualContext11OpenContextEN3Gap3Gfx25igRenderDestinationFormatERKNS0_8InitInfoE+0xff)[0xafcdcd8f]
/usr/lib/googleearth/libevll.so(_ZN5earth4evll13VisualContext4initERKNS0_8InitInfoE+0x18e)[0xafcdf75e]
/usr/lib/googleearth/libevll.so(_ZN5earth4evll17RenderContextImpl4initERKNS0_8InitInfoE+0x7e)[0xafc3e28e]
/usr/lib/googleearth/librender.so(_ZN12RenderWidget6SetApiEPN5earth4evll3APIE+0x47)[0xb4aab8c7]
/usr/lib/googleearth/librender.so(_ZN5earth6render12RenderWindow12createWidgetEv+0x16a)[0xb4a9030a]
/usr/lib/googleearth/libgoogleearth_free.so(_ZN5earth6client12ModuleWidget9showEventEP10QShowEvent+0x8d)[0xb7703b9d]
/usr/lib/googleearth/libQtGui.so.4(_ZN7QWidget5eventEP6QEvent+0x770)[0xb6ab8a60]
/usr/lib/googleearth/libQtGui.so.4(_ZN19QApplicationPrivate13notify_helperEP7QObjectP6QEvent+0xac)[0xb6a5569c]
/usr/lib/googleearth/libQtGui.so.4(_ZN12QApplication6notifyEP7QObjectP6QEvent+0x484)[0xb6a606c4]
/usr/lib/googleearth/libQtCore.so.4(_ZN16QCoreApplication14notifyInternalEP7QObjectP6QEvent+0x78)[0xb74ecba8]
/usr/lib/googleearth/libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x145)[0xb6aba6d5]
/usr/lib/googleearth/libQtGui.so.4(_ZN14QWidgetPrivate14show_recursiveEv+0x7d)[0xb6aba3cd]
/usr/lib/googleearth/libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0xc5)[0xb6aba4b5]
/usr/lib/googleearth/libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x61)[0xb6aba5f1]
/usr/lib/googleearth/libQtGui.so.4(_ZN7QWidget10setVisibleEb+0x1db)[0xb6abaa2b]
/usr/lib/googleearth/libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0x170)[0xb6aba560]
/usr/lib/googleearth/libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x61)[0xb6aba5f1]
/usr/lib/googleearth/libQtGui.so.4(_ZN14QWidgetPrivate14show_recursiveEv+0x7d)[0xb6aba3cd]
/usr/lib/googleearth/libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0xc5)[0xb6aba4b5]
/usr/lib/googleearth/libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x61)[0xb6aba5f1]
/usr/lib/googleearth/libQtGui.so.4(_ZN7QWidget10setVisibleEb+0x1db)[0xb6abaa2b]
/usr/lib/googleearth/libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0x170)[0xb6aba560]
/usr/lib/googleearth/libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x61)[0xb6aba5f1]
/usr/lib/googleearth/libQtGui.so.4(_ZN14QWidgetPrivate14show_recursiveEv+0x7d)[0xb6aba3cd]
/usr/lib/googleearth/libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0xc5)[0xb6aba4b5]
/usr/lib/googleearth/libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x61)[0xb6aba5f1]
/usr/lib/googleearth/libQtGui.so.4(_ZN7QWidget10setVisibleEb+0x1db)[0xb6abaa2b]
/usr/lib/googleearth/libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0x170)[0xb6aba560]
/usr/lib/googleearth/libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x61)[0xb6aba5f1]
/usr/lib/googleearth/libQtGui.so.4(_ZN7QWidget10setVisibleEb+0x1db)[0xb6abaa2b]
/usr/lib/googleearth/libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0x170)[0xb6aba560]
/usr/lib/googleearth/libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x61)[0xb6aba5f1]
/usr/lib/googleearth/libQtGui.so.4(_ZN7QWidget10setVisibleEb+0x1db)[0xb6abaa2b]
/usr/lib/googleearth/libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0x170)[0xb6aba560]
/usr/lib/googleearth/libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x61)[0xb6aba5f1]
/usr/lib/googleearth/libQtGui.so.4(_ZN7QWidget10setVisibleEb+0x1db)[0xb6abaa2b]
/usr/lib/googleearth/libQtGui.so.4(_ZN7QWidget10showNormalEv+0x5c)[0xb6aa816c]
/usr/lib/googleearth/libgoogleearth_free.so(_ZN10MainWindow18readScreensizeInfoEv+0xd2f)[0xb76f608f]
/usr/lib/googleearth/libgoogleearth_free.so(_ZN5earth6client11Application12SetupMainWinENS0_3Kvw7ProductEb+0x31c)[0xb773025c]
/usr/lib/googleearth/libgoogleearth_free.so(_ZN5earth6client11Application3runEv+0x4d6)[0xb7733406]
/usr/lib/googleearth/libgoogleearth_free.so(+0xaad1b)[0xb7727d1b]
/usr/lib/googleearth/libgoogleearth_free.so(earthmain+0x247)[0xb7728ed7]
/usr/lib/googleearth/googleearth-bin[0x804871b]
/lib/libc.so.6(__libc_start_main+0xe7)[0xb522ece7]
/usr/lib/googleearth/googleearth-bin[0x8048661] Suggestions?

---

### Post by adduds on 2011-01-18
> **jcolyn said:**
> Here ya go..first though delete the .deb package you downloaded from google..

If you want to install the latest current version of Googleearth follow these simple steps and you will have it up and running in no time.

First though you will need to purge any installs or attempts at installing Googleearth.

These terminal entries have to be entered exactly as typed below so you may want to copy/paste into your terminal.

To start: Open a terminal and enter ```
sudo apt-get install lsb-core
``` Once done enter ```
sudo apt-get install googleearth-package
``` After the package is installed enter ```
sudo make-googleearth-package --force
``` This process will take several minutes and you will see many warning notices but ignore them.

Once the above process is completed close the terminal and go to your /home folder where you will find a googleearth_xx.deb package. Double-click it and follow instructions.

Once installed you should have the Googleearth link in your Internet folder.

Enjoy

Worked first try mate! ty very much

i just:

```
 
sudo dpkg -i googleearth_6.0.1.2032+0.5.7-1_amd64.deb

```

after make forcing! ty muchly

---

### Post by zbirdman777 on 2011-01-19
That ended up working for me. I did however get a lot of errors again when building the package. The error was:

"Can't extract name and version from library"

It was on a lot of stuff. Regardless it still works now. I supposed I needed the lsb-core even though I'm not sure what that is. haha. Linux Standard Base 4.0 core support package. Oh well.

Thank you thank you!

---

### Post by zbirdman777 on 2011-01-19
That ended up working for me. I did however get a lot of errors again when building the package. The error was:

"Can't extract name and version from library"

It was on a lot of stuff. Regardless it still works now. I supposed I needed the lsb-core even though I'm not sure what that is. haha. Linux Standard Base 4.0 core support package. Oh well.

Thank you thank you!

---


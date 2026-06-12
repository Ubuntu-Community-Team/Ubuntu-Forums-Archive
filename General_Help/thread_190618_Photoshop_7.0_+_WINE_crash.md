---
title: "Photoshop 7.0 + WINE crash"
date: 2006-06-06
forum: General Help
---

### Post by seth0x2b on 2006-06-06
Hey guys. Photoshop worked with WINE on Breezy with no problem, I had WINE 0.9.9(I think).
I tried installing it on Dapper with the same WINE version, worked great, but when I try to run it, I get this:
```

seth@orion:~$ dx9wine ~/.dx9wine/drive_c/Program\ Files/Adobe/Photoshop\ 7.0\ CE/Photoshop.exe
fixme:actctx:QueryActCtxW stub!
X Error of failed request:  BadDevice, invalid or uninitialized input device
  Major opcode of failed request:  148 (XInputExtension)
  Minor opcode of failed request:  3 (X_OpenDevice)
  Serial number of failed request:  35
  Current serial number in output stream:  35
seth@orion:~$

``` Same error with WINE 0.9.9, 0.9.14 and dx9wine (version 0.9.1)

Any hints/advice are very welcomed
Cheers

---

### Post by veratyr on 2006-06-08
Trying to get photoshop 7.0 to work in wine and I get this same error. 

[http://bugs.winehq.org/show_bug.cgi?id=4579]("http://bugs.winehq.org/show_bug.cgi?id=4579")

"this error occurs in the wintab32 dll. Commenting out the DllMain portion of the code
seems to resolve the issue." 

So where and how do I do this exactly?

---

### Post by Shay Stephens on 2006-06-08
I had the same problem.  So I tried crossover office, and PS7 works well under it.  If PS7 has to run, try crossover office.

---

### Post by homersbrain on 2006-06-09
I too am dismayed at dapper not being able to run photoshp 7. You have to pay for crossover and the demo seems sluggish. Surely there is a way to get around this problem with wine - if it worked fine on breezy then dapper must have broken something. But what?

---

### Post by closeyourwindows on 2006-06-09
I got it to work using wine .92, I know its an older version and all, but it works.
I went to the winehq site and alien'd a rmp and .....
no problems.  I dont know what version you are running but I got 7 working just fine.  

if all else fails, there is always vmware!!!!

---

### Post by homersbrain on 2006-06-11
> I got it to work using wine .92, I know its an older version and all, but it works.
I went to the winehq site and alien'd a rmp and .....
no problems.

I tried this but I still get exactly the same errors. What could be different? Anyone else got photoshop to run in dapper?

---

### Post by taurus on 2006-06-11
Sorry but got Photoshop 6 running with CrossOver Office...

---

### Post by dronepower on 2006-06-12
Does photoshop CS2 work in anyway with wine or crossover office?

---

### Post by ZiZi on 2006-06-12
I get the same problem when trying to run Photoshop, although ImageReady starts with no problems on all tested versions of wine.

I also get the same (or very similar) output when trying to run other applications, even the native KDE apps. However, they don't crash and keep running without any obvious problems. It can be a problem somewhere in X itself, which doesn't affect common apps, but prevents some non-native from running.  

I did some searching, this behavior is discussed in various forums, just try searching "BadDevice", there is even a fix in [this forum]("http://www.ubuntuforums.org/showthread.php?t=185930") (or maybe [this one]("http://ubuntuforums.org/showthread.php?t=191872&highlight=BadDevice") is basically the same, but slightly better), so it seems that it's not the same problem as this Wine error.

However, Photoshop is a must-have in wine, it must be fixed ASAP!:-x ;-)

---

### Post by ZiZi on 2006-06-18
I fixed this via completely uninstalling wine, following [Wine installation How-To]("http://www.ubuntuforums.org/showthread.php?t=149585%20") (even though it is originally for 5.10 Breezy) and installing Photoshop via ```
wine /media/cdrom0/Setup.exe
```

Then (this is propably the biggest catch, because Photoshop won't work otherwise) it is necessarry to run Photoshop with overrided wintab32 settings:```
WINEDLLOVERRIDES="wintab32=n" wine Photoshop.exe
``` This hint is from [WineHQ Application Database]("http://appdb.winehq.org"), [Photoshop 7 on Dapper testing]("http://appdb.winehq.org/appview.php?versionId=1336&iTestingId=3893") in particular.

It is more comfortable to use ```
winecfg
``` Add the Photoshop executable to the app list and configure wine to use the **native** wintab32 library when trying to run it. Then you don't have to type the WINEDLLOVERRIDES section each time you want to use Photoshop.

Just for more info, I now run Photoshop 7.0 CE on Wine 9.15, no major problems so far. It even works to emulate Win XP instead of the default 98, it looks better and nothing seems to be broken.

---

### Post by Neo Ex on 2006-06-18
Thanks! That worked for me!

---

### Post by Shay Stephens on 2006-06-19
[QUOTE=ZiZi]I fixed this via completely...[/QUOTE]

Thank You!!!
I now have PS7 working in Dapper!  I didn't uninstall, I just changed the wintab32 deally-bobber and tried it and it booted up.

Now I am going to do a speed test between crossover office and wine doing the same thing in PS.  That should be interesting ;)

---

### Post by Shay Stephens on 2006-06-19
Update:
PS7 loads, but when I went to do some work in it, it crashed and burned.  I ran it under Crossover Office and didn't have any trouble and was able to finish my work.

So next I will try uninstalling wine and starting fresh to see if I can get a stable app that way.

---

### Post by homersbrain on 2006-06-21
It works for me too.

---

### Post by ZiZi on 2006-06-22
Minor update: I did some more testing and Photoshop only pretended to be running, the problems were in right-click menus - they were displayed, but the items didn't react to my clicks at all. Additionaly, Internet Explorer 6.0 stopped working, which made the installation worthless for my purpose - webdesign.

This was reported in the [WineHQ AppDB]("http://appdb.winehq.org"), so I figured out it was a problem of my wine version. The only thing I did was downloading various versions from [Sourceforge WineHQ Site]("http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=174803") and trying to downgrade wine step by step by repeating ```
sudo apt-get remove wine
sudo dpkg -i wine_<version>.deb
```

I ended up with version 0.9.11, which now runs IE6 properly and also Adobe Photoshop 7.0 CE with no major problems, right-click menu problem resolved with later mentioned issue, but still quite ready for work. I am sure all Phs users are aware of the floating windows, which keep being displayed even if the main window is minimized (simple solution though: hide them by <tab> and then minimize the window)

Rarely it happens to boost the CPU usage up to 100%, but it drops down after a looong while, but with no consequences. I hadn't experienced any crashes so far, therefore I'm keeping this version, you can try go lower, perharps it will work even better. I don't have any other wine apps installed, that's why I don't know about any other apps, which may stop working after this procedure.

UPDATE: Heh, somebody up there must have the sense of irony - right after posting this reply, I found some more issues - don't, repeat DON'T (I know you will;) try to resize the floating windows (layers, history, navigator etc.) by dragging their borders - this hangs my whole desktop and I am forced to Ctrl-Alt-Backspace it. But this ocurred time to time even with Breezy. However, this is still the best config I've ever had, works slightly better than in Breezy. My goal was to return to the status before dist-upgrade, therefore I'm going to celebrate 8-) ;)

---

### Post by Shay Stephens on 2006-06-22
I removed wine and loaded 0.9.11.  After adding wintab32 change it boots up fine.  I will give it some work to do tomorrow to see if it is more stable.  Thank you for the continued info :-)

[QUOTE=ZiZi]Minor update: I did some more testing and Photoshop only pretended to be running...[/QUOTE]

(edit)I couldn't resist, and did a speed test between crossover office (CXO) 5.0.1 and wine 0.9.11.  Used radial blur set to 100 and best quality on the same image in both, and both finished in 39 seconds.  So it looks like there isn't really a speed difference between the two, but CXO does seem to run and render PS7 more stable than wine at this point.

In wine, my pallets keep changing sizes (length) and the splash screen has overlapping text.  I'll see how it does tomorrow when I can throw some work at it.

---

### Post by Shay Stephens on 2006-06-22
I unloaded 0.9.11 and loaded 0.9.8.  It seemed more stable and the splash screen text was being rendered properly (not overlapping) but I am still getting unstable pallets.  I am going to try going back a little more 0.9.5 maybe?

---

### Post by Melvil on 2006-06-22
Does someone know where I can find the old PS7 tryout version for windows? Adobe removed the file a while ago from their ftp servers. I want to test and and check it's performance under wine, though.
How is the performance?

---

### Post by Shay Stephens on 2006-06-22
[QUOTE=Melvil]How is the performance?[/QUOTE]

I just ran a test with the machine rebooted and not running anything in the background.  I ran PS7 under CXO, Wine, and WinXP.

I used the radial blur filter set to: amount=100 method=spin quality=best
CXO 34 seconds
Wine 34 seconds
WinXP 25 seconds

I tried it under the 386 and 686 kernels too, but there was no change in completion time.  So wine is about 26%(?) slower than running PS7 under windows XP.

I also tried it with wine 0.9.16 and the timing was the same.  In 0.9.16 I don't get a splash screen, but the part that shows the modules loading and fonts and such is visible.  The pallets are still wonky.

---

### Post by wongpk on 2006-07-23
I got Adobe PHotoshop 7 works on Wine 0.9.17. Everything fine. But I don't know why I have to put Photoshop files on c:/windows/system32/ folder in order to run Photoshop. Any idea?

---


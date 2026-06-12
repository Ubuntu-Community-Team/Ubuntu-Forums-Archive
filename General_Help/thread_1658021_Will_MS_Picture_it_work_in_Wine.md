---
title: "Will MS Picture it work in Wine?"
date: 2011-01-02
forum: General Help
---

### Post by judge jankum on 2011-01-02
Will Microsoft Picture it work in Wine? My wife was about to buy it and I told her to wait and we'd see if it will work first. She's running Xubuntu 10.04..
                        Thanks much

---

### Post by cariboo on 2011-01-02
Check the winehq database to see if it will work.

---

### Post by kaldor on 2011-01-02
After reading up about Picture it I recommend you not buy into it. It stopped production in 2006 and a lot of free tools should work in place of it.

---

### Post by judge jankum on 2011-01-02
Just my luck" Almost bought a dinosaur lol! She has an old version from 2000 she fell in love with but the disk is bad...She's spent more than a few hours cussing Gimp so far...
 You guys know of another "simple" photo program, for touching up, resizing etc.?

---

### Post by kaldor on 2011-01-02
Give Shotwell a try? It's very iPhoto-like. ( *sudo apt-get install shotwell* )

I recommend she learn GIMP though... it's very powerful if she has the patience to learn.

Shotwell overview...

[http://yorba.org/shotwell/](http://yorba.org/shotwell/)

---

### Post by judge jankum on 2011-01-02
Thanks we'll give it a try!

---

### Post by deesto on 2011-03-22
I'd like to get Picture It working too, as it's the one $#!++y program I can't get my wife to give up, despite the plethora of other tools available.

I've just trying running it in wine, with the caveat that it's wine within a Maverick VM on a W7 machine.  It throws this error:
```
fixme:shell:SHCreateShellPalette stub
err:module:attach_process_dlls "piutil.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"D:\\Program Files (x86)\\Microsoft Picture It! 10\\pi.exe" failed, status c06d007e
```
I've tried to use winecfg to add piutil.dll as a "builtin,native" and then "native,builtin" library, but neither helped.

---

### Post by blueridgedog on 2011-03-22
> **deesto said:**
> with the caveat that it's wine within a Maverick VM on a W7 machine

So you boot into Windows7, run a virtual machine version of Ubuntu and then run windows programs under Wine in Ubuntu? 

I am confused.

---

### Post by deesto on 2011-03-22
> **blueridgedog said:**
> So you boot into Windows7, run a virtual machine version of Ubuntu and then run windows programs under Wine in Ubuntu? 

I am confused.Yes, that's correct.  Wht are you confused?  Now I'm confused. 8-[

If I can prove that the Windows app works under wine, I can get rid of Windows.

---

### Post by blueridgedog on 2011-03-22
> **deesto said:**
> If I can prove that the Windows app works under wine, I can get rid of Windows.

Ah...testing...got it.

---

### Post by Mark Phelps on 2011-03-23
> **deesto said:**
> If I can prove that the Windows app works under wine, I can get rid of Windows.

Then, since you're testing, you should look into Crossover Linux and Winetricks.  Both of those make Wine usage a lot simpler and can vastly improve the process of installing Windows apps.

However, keep in mind that Wine will always trail MS Windows in terms of the availability of apps. For example, it took until Office 2010 came out before Office 2007 finally worked decently -- and even then, there were still Office components that would not work.

Getting rid of Windows and using Wine is OK -- until you run into that one app that simply won't work.

Unless you know for sure that you'll never need to "upgrade" your MS Windows apps in Wine, you would do better keeping an MS Windows version around in dual-boot mode.

But ... it's your choice.

---

### Post by blueridgedog on 2011-03-23
> **Mark Phelps said:**
> 
Unless you know for sure that you'll never need to "upgrade" your MS Windows apps in Wine, you would do better keeping an MS Windows version around in dual-boot mode.

I use a windows virtual machine for such essentials.

---

### Post by deesto on 2011-03-23
Unfortunately, in this case, the alternatives of dual-boot and a Windows VM are not viable.  Having to boot up a VM, or re-boot entirely to another OS, just to launch a Windows app are not acceptable to the person I'm trying to please here, and when you think about it, I guess I can't argue the logic.  And that's why I've been stuck with Windows on this machine for so long.

I would like to convert this to a pure Linux environment, as all the other requirements can be filled directly by inherent apps.  But unless I can get Picture It working with Wine, I can't even think about going there.

Isn't Crossover Linux just an additional (paid) layer for wrapping apps up with a special environment for use with Wine? If so, isn't there some configuration trick via winetricks that can be done instead?  I can't seem to find any information on how to properly configure the custom .DLL the app uses (piutil.dll).

---


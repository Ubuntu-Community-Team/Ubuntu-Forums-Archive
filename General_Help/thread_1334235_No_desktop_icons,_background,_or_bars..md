---
title: "No desktop icons, background, or bars."
date: 2009-11-22
forum: General Help
---

### Post by spatuluk on 2009-11-22
Hi all!

Something weird has happened to my Ubuntu.. I upgraded to Koala (64 bit), and all was fine at first.  Then a couple of days later I did an update, restarted, and now my desktop doesn't seem to want to load.

I get a black background (no background image), and a 'busy' cursor.  Pidgin loads, and is connecting to the internet via wireless.  It doesn't have a top bar to allow minimising/closing/etc.  I can open firefox via Pidgin, and that's missing it's top bar too.  The font seems to be a generic font, rather than the font I selected for the theme I set up.

ALT+F2 does nothing, and CTRL+ALT+DEL doesn't do anything. I tried restarting (hitting the power switch makes the shutdown menu appear) and doing a package repair via the grub menu, and it didn't fix anything.

It seems that something is stalling gnome, but I don't know how to find out what it is.  

Any ideas?

Thanks

---

### Post by jeb800e on 2009-11-22
Can you restart your computer without having to "pull the plug" on it?
If not, try doing the REISUB technique next time you restart your system.

Hold down on Alt and SysRq, and type R E I S U B (no spaces) SLOWLY, ONE AT A TIME, while still holding down on Alt and SysRq. This will cause your computer to do a "gentle restart".

R = Keyboard switch to XLATE mode
E = Terminated all processes EXCEPT init
I = Kills all processes EXCEPT init
S = Sync all mounted filesystems
U = Remount all filesystems/Read-only mode
B = Immediate reboot/keeping all filesystems mounted and/or synced.

You can read more about this on Wikipedia.

---

### Post by jeb800e on 2009-11-22
This may (also) fix you system: Go to System < Preferences < Appearance. Click on "Visual Effects". Choose "None". I had a problem similar to this, an dthis fixed it, but I can no longer use any more visual effects unless I re-install the packages.

You can also go to Applications < Accessories < Terminal. Type "sudo aptitude". Type in your password (nothing will show up here). Once you are in Aptitude, press "u" on your keyboard. Now, press "b". If anything comes up here in a new tab within Aptitude, follow the instructions given within the application. Click on the "packages" tab, if there is one. If not, you are most likely in that tab anyways. Click the "g" button on your keyboard. Wait for a list to come up. Click "g" again. This should/may fix your problems you have been experiencing. You may be able to fix your visual effects back to original state now. Give it a try.

---

### Post by spatuluk on 2009-11-22
Thanks for the replies. The REISUB thing certainly allowed a restart, but upon restart, the same old problem was still there. 

I forgot to mention in the main text that none of the menus or taskbars are appearing, so I can't run terminal or change the appearance.  Not via the GUI, anyway.  The only things that're accessible are pidgin (which is only visible because it starts with the contact list window) and the mouse cursor.  My guess is that whatever draws the menus is hanging.  I'm not experienced enough to know what that would be.  

I can access a command line via recovery mode, so i might try renaming some config files.

edit: removing gconf didn't make any difference at all.

---

### Post by jeb800e on 2009-11-22
Try booting Ubuntu from an older Linux kernel through the GRUB bootloader.

---

### Post by jeb800e on 2009-11-22
Have you tried Ctrl + Alt + Backspace?

Also, there is another way to get to the terminal: Ctrl + Alt + F1. Enter the stuff I told you about in my second post now. To go back to GUI-mode (normal-mode), do Ctrl + Alt + F7.

Fast tip: You can have multiple terminals running at once. You can replace the "F1" in Ctrl + Alt + F1 with any F- key up to F6 (F7 will return you to GUI-mode, as said before). You can switch instantaniously between terminals this way.

---

### Post by spatuluk on 2009-11-23
Thanks for the replies!

The older Kernel refused to boot.  If forget why - I'll have to make a note when I try it again in a sec.

I tried aptitude; 'u' made some stuff scroll by, but nothing came up after pressing 'b', so pressing 'g' did nothing.  System is still borked.  :\

edit:
attempting to boot using an older kernel hangs before getting to any kind of windows.  One of the last logs it shows is 'nvidia (185.18.36)...   ...fail'

---

### Post by spatuluk on 2009-11-23
I managed to get to Nautilus via the downloads window in Firefox, and from there I launched gnome-panels and managed to set effects to normal, which made all the bars reappear (it was already set to 'none').  

Nothing I change seems to affect the background image or show the desktop icons, and a weird thing is that the terminal window won't let me type anything into it.  After restarting the computer, everything is back the way it was previously (nothing but a bar-less pidgin and a busy cursor).

I've tried hunting through the logs, but I can't see anything obviously wrong.

---

### Post by jeb800e on 2009-11-23
Okay. Go back into a Terminal and do the "sudo aptitude" stuff, but this time, right after typing in "sudo aptitude" and pressing enter, click "u" on the keyboard. If anything comes up, click "g". If a message comes up showing you what will be installed/removed/etc., just click "g", again. Now, go back to the "Packages" tab(or if nothing came up when doing a package list update, go directly here), if there is one. Click "g". Now, click "g" again. Wait for these downloads to take place, too. Let them install/remove.

---

### Post by lavadisco on 2009-11-28
I have this exact problem. I have a four-day old clean install of 64-bit Karmic on my laptop. 

This morning when I booted up, the files and icons I had on my desktop the day before are gone. However, when I open up Nautilus and navigate to the desktop, the files and icons are present. If I try and drag/drop or copy anything to the desktop, nothing happens. When I right-click on the desktop, the usual menu does not appear. When I open up any program, the usual min/max/close buttons in the upper right corner are not there. Nor can I grab the top of the window and drag it. Alt-F4 does not close anything. 

Strangely, enabling desktop effects to "normal" restores the min/max/close buttons and the ability to move windows. But the desktop still does not show any files nor does right-clicking on it bring up a menu. When I restart everything reverts back to the fully messed-up state.

I uninstalled both Emerald and Compiz to see if that was the problem, but no dice. I unticked and reticked show_desktop in gconf-editor under Apps/Nautilus/Preferences. No change. Tried all the Aptitude stuff suggested here, didn't help. Anybody have any more suggestions?

---


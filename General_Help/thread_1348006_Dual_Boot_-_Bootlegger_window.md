---
title: "Dual Boot - Bootlegger window"
date: 2009-12-06
forum: General Help
---

### Post by cjwescott on 2009-12-06
I am a new user to Ubuntu and I recently installed it and I am currently in the process of configuring it.

Question I have is why in my dual boot windows (GNU Grub V1.97~beta4), after installing updates, does the window now have two versions of Ubuntu to choose from.  I know have:

* 2.6.31-16-generic
* 2.6.31-16-generic (recovery mode)
* 2.6.31-14-generic
* 2.6.31-14-generic (recovery mode)

Why are there more options showing up?  This is confusing. Which do I pick?  What does each one mean?  Is there a way to eliminate one of the two which may be less current?

Chris

---

### Post by cjwescott on 2009-12-07
Bump.

---

### Post by blegs38552 on 2009-12-07
I have the same problem- can soemone come up with s simple explanation of how to fix this vexing problem? This also messed up my default boot, which used to be Windows 7, but due to the extra lines being added, became memtest.

---

### Post by cariboo on 2009-12-07
The reason you are seeing to entires for Ubuntu is that you have two kernels installed. This happened because you ran the updates. The way to remove unwanted kernels is to go to System-->Administration-->Synaptic Package Manager and search for in the op's case:

```
linux-image 2.6.31-14
```

Once the image is found right click it and mark it for complete removal, then click apply.

I would suggest you not remove the old kernel until you are sure the new kernel is working correctly.

---

### Post by cjwescott on 2009-12-07
Thank you for the reply.
 
Is there also a way to reorder the list in the Boot Logger?
 
Chris

---

### Post by 73ckn797 on 2009-12-07
> **cjwescott said:**
> Thank you for the reply.
 
Is there also a way to reorder the list in the Boot Logger?
 
Chris

You can install "startupmanager" found in Synaptic. It will allow you to designate which OS will be default. If you do not see this program in Synaptic, make sure you have enabled universe and restricted repositories in Software Sources.

---

### Post by blegs38552 on 2009-12-07
Thanks for your answer regarding the duplicate kernels.

Regarding the question or re-ordering the menu, Startup-Manager does not give me that option - it does allow me to select the default O/S, but I would like to see Windows 7 on top as option 0 - currently, it is at the bottom as option 4.

Lastly, I would like to suppress the memtest entry (hide it).

Thanks.

---

### Post by lisati on 2009-12-07
> **cjwescott said:**
> Is there also a way to reorder the list in the Boot Logger?
Thanks for this question which I see has already been addressed, and which clarifies something for me. 

Looking at the thread title I was worried for a moment that someone might have to do a lecture about the risks of bootlegging (e.g. OSes from dubious sources) :)

---

### Post by 73ckn797 on 2009-12-07
> **blegs38552 said:**
> Thanks for your answer regarding the duplicate kernels.

Regarding the question or re-ordering the menu, Startup-Manager does not give me that option - it does allow me to select the default O/S, but I would like to see Windows 7 on top as option 0 - currently, it is at the bottom as option 4.

Lastly, I would like to suppress the memtest entry (hide it).

Thanks.

You will need to read this link:
[https://help.ubuntu.com/community/Grub2?action=show&redirect=GRUB2](https://help.ubuntu.com/community/Grub2?action=show&redirect=GRUB2)

---

### Post by 73ckn797 on 2009-12-07
> **lisati said:**
> Looking at the thread title I was worried for a moment that someone might have to do a lecture about the risks of bootlegging (e.g. OSes from dubious sources) :)

This was my initial thought also.....:p

---

### Post by blegs38552 on 2009-12-07
OK - I don't doubt that the answer to my reordering question in somewhere in Ubuntu Documentation link, but I am now more confused than ever after having read this page. I would think that there must be a simple way to do this, but so far, no one has been able to tell me what it is.

I was able to get rid of the memtest entries by commenting out the menuitem lines in /etc/grub.d/20_memtest86+, which has reduced my menu items to 3 lines. I made Win 7 the default, but it is still at the bottom, and will probably remain there for a long time.

---

### Post by 73ckn797 on 2009-12-07
> **blegs38552 said:**
> OK - I don't doubt that the answer to my reordering question in somewhere in Ubuntu Documentation link, but I am now more confused than ever after having read this page. I would think that there must be a simple way to do this, but so far, no one has been able to tell me what it is.

I was able to get rid of the memtest entries by commenting out the menuitem lines in /etc/grub.d/20_memtest86+, which has reduced my menu items to 3 lines. I made Win 7 the default, but it is still at the bottom, and will probably remain there for a long time.


There is a way but grub2 is so new to most everyone. I have to relearn about grub2 after I had figured out grub. There is one file but it is not recommended to edit it. I looked at it but would be afraid of fouling something up since I do not know any of the programming involved with what I see listed in the file. I purposely have not named the file so that you do not end up with problems that would require extensive repair or a reinstall back to square one.

---

### Post by blegs38552 on 2009-12-07
I do know about the "file that should not be named" (that's for the Harry Potter fans out there). In order to hide the memtest entries, I did access a different file and ran sudo update-grub after, so I am not a total novice with this.

Unfortunately, this does nothing to answer my question regarding the menu order. I assume that the answer resides in one of the files in /etc/grub.d, but I have looked at each one of them and do not see anything. Perhaps there are a few lines that I can add to the last file (ends in 40, but I am writing this from Windows)and rename the file so that it loads higher in the pecking order. If so, can someone take through the exact steps needed to do this, and yes, I know that I will have to run sudo update-grub after.

---

### Post by 73ckn797 on 2009-12-07
Check out this link:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by 73ckn797 on 2009-12-07
[quote=blegs38552;8459779]I do know about the "file that should not be named" (that's for the Harry Potter fans out there). In order to hide the memtest entries, I did access a different file and ran sudo update-grub after, so I am not a total novice with this./quote]

I do not want to be blamed for you borking your system, as Harry Potterish as you seem to think it sounded. You seem to be well on the way to either learning what it will take to get things how you want them or messing something up with your desire to change the boot order list.

I leave it with you. I am only trying to help.

---

### Post by blegs38552 on 2009-12-08
It does not look like there is any simple way to reorder the menu items. Too bad - things were much easier in grub 1. It looks like one would have to create a custom file with menuitems, save it high up in the \etc\grub.d folder by starting the filename with a low number, disable some other files from executing, and running sudo update-grub.

In the old days with grub 1, you cut and pasted the menu item for Windows so that it was before the Ubuntu entries in menu.lst.Saved the file and rebooted, and the new menu was there.

I was able to supress the memory testing entries in grub 2 by commenting the menuitems out in the 20_ file (I don't remember the whole name, something like 20_memtest86 - this is being typed from a Windows PC at work) and running sudo update-grub.

I ahve also seen comments in this forum that grub 2 takes much longer to start up and boot than grub 1 did.

Now, can someone tell me once again exactly what benefits I derive from using grub 2 that mitigate the above complexities? I thoguht that the goal for Ubuntu was to become more user firendly for the average computer user.

---

### Post by 73ckn797 on 2009-12-08
> **blegs38552 said:**
> I ahve also seen comments in this forum that grub 2 takes much longer to start up and boot than grub 1 did.

Grub2 DOES seem to take longer.

---

### Post by t2000kw on 2010-05-24
I didn't read the entire thread, but if all you want is to make one OS the default one, you can use the Startup manager:

[http://www.ubuntugeek.com/startup-manager-change-settings-in-grub-grub2-and-usplash.html](http://www.ubuntugeek.com/startup-manager-change-settings-in-grub-grub2-and-usplash.html)

If it's not installed by default in your Ubuntu version, you can install it using Synaptics, then use it to set the default OS. 

I use it to set Windows as the default so my wife can reboot and walk away, then come back to Windows. I can take the time to switch to Ubuntu if I want, or go to Ubuntu. 

You can delete old kernels using Synaptics to make the menu less crowded. 

Donald

---


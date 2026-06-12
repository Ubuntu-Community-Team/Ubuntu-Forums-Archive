---
title: "Compiz Problem after 10.10 upgrade"
date: 2010-10-23
forum: General Help
---

### Post by Welcomed Rain on 2010-10-23
I have a 64bit desktop and 64bit laptop. I upgraded both to 10.10 and they both have the same problem with compiz. Even though I selected the cylinder distortion, the rotating desktops will not deform to a cylinder unless I select "Wallpaper" in compiz but when I do that, the cylinder is completely transparent AND objects (like windows or bouncing/squishing icons in AWN appear not to refresh. Like a window will not disappear after closing.

As an aside, I have four different wallpapers selected for the four different desktops, but none of them display when I select "Wallpaper" in compiz, I just get the transparent cylinder.

If I deselect "Wallpaper" in compiz, the problem with the refresh disappears immediately, as does the transparent wallpapers but the cylinder becomes disabled and I am left with a cube with a single wallpaper and no ability to decrease opacity during rotation.

This has happened with both my desktop and laptop. I have tried uninstalling all compiz components in Synaptic Package Manager and adding them back one at a time in case I added some conflicting components but this doesn't seem to help.

I did not change settings in the updates, so I have to assume that the problem has something to do with a bug in Compiz. The two computers have different video cards and the drivers are up to date, so I'm at a loss.

Has anyone else found this problem? Has anyone been able to display the cylinder distortion with four desktops with different wallpapers?

Thanks!

---

### Post by Welcomed Rain on 2010-10-26
I have partially fixed the issue. Previously, to show multiple wallpapers, you needed to NOT show the desktop. Apparently this has become an issue in 10.10. If I select to show desktop icons in Ubuntu Tweak, the cylinder deformation works as it should. I have not yet figured out how to get the multiple wallpapers to show, however. I'm still toying around with different settings to see if I can get that working.

---

### Post by londonbabs on 2010-11-01
I'd be interested to know if you're getting anywhere with that, keep us posted with any development if you can.
All I got, at best, is the same kind you described, I try to get different wallpaper for different workspace, but after a few tweaks, all I get is stuck window effect and/or complete transparency, I'm slowly giving up, we might have to wait for Ubuntu 11 or downgrade back to 10.04 where it worked (it seems a few people chose this solution already)

Thanks anyway

---

### Post by Welcomed Rain on 2010-11-22
I'm still having the issue (though I haven't spent a lot of time trying to figure it out). This seems to be a bug and I'm a little surprised I haven't heard more complaints about it. I have been using the multiple desktop wallpapers for several builds (a couple of years probably) and although Compiz changed how you selected multiple wallpapers to make it easier a release or two ago, I have not had issues. This seems to a bug and I keep installing updates and trying to activate the multiple desktops afterwards to see if it as been addressed by still nothing. Is no one but us two having this issue? I find that hard to believe since I'm having it on two different computers and the settings were unchanged.

I'll try to do some more investigation when I have time and post any results here.

---

### Post by wolke on 2011-01-01
I have the same exact issue. Seems to be a bug with the wallpapers plugin. 

I used to use the cube with 4 different wallpapers {show desktop=>false + wallpapers plugin}. No longer works, with or without cylinder distortion. I get a completely transparent background {I see the Skydome image from DesktopCube}

---

### Post by wolke on 2011-01-01
aaand i fixed it, with a workaround from:
[http://forum.ubuntu-fr.org/viewtopic.php?id=421649](http://forum.ubuntu-fr.org/viewtopic.php?id=421649)

the attachment is the file i got from here:
[http://www.mediafire.com/?usji79x5yiu5d3z](http://www.mediafire.com/?usji79x5yiu5d3z)  ( wallpaper plugin - 64bit module - File Size: 96.69KB )

replace:
/usr/lib/compiz/libwallpaper.a
/usr/lib/compiz/libwallpaper.la
/usr/lib/compiz/libwallpaper.so

with the ones in the file attached

---

### Post by WiebeS on 2011-01-04
> **wolke said:**
> aaand i fixed it, with a workaround from:
[http://forum.ubuntu-fr.org/viewtopic.php?id=421649](http://forum.ubuntu-fr.org/viewtopic.php?id=421649)

the attachment is the file i got from here:
[http://www.mediafire.com/?usji79x5yiu5d3z](http://www.mediafire.com/?usji79x5yiu5d3z)  ( wallpaper plugin - 64bit module - File Size: 96.69KB )

replace:
/usr/lib/compiz/libwallpaper.a
/usr/lib/compiz/libwallpaper.la
/usr/lib/compiz/libwallpaper.so

with the ones in the file attached

YEAH, that worked, thank you!

---

### Post by Dirjel on 2011-01-07
> **wolke said:**
> aaand i fixed it, with a workaround from:
[http://forum.ubuntu-fr.org/viewtopic.php?id=421649](http://forum.ubuntu-fr.org/viewtopic.php?id=421649)

the attachment is the file i got from here:
[http://www.mediafire.com/?usji79x5yiu5d3z](http://www.mediafire.com/?usji79x5yiu5d3z)  ( wallpaper plugin - 64bit module - File Size: 96.69KB )

replace:
/usr/lib/compiz/libwallpaper.a
/usr/lib/compiz/libwallpaper.la
/usr/lib/compiz/libwallpaper.so

with the ones in the file attached

This worked for me too.  Thanks for being able to read French, sir.

---

### Post by wolke on 2011-01-10
pas de quoi

---

### Post by etopsirhc on 2011-01-16
is there a 32 bit version of that fix ?

---

### Post by Welcomed Rain on 2011-03-11
Thank you wolke for finding a solution to this problem. I am amazed this bug didn't get more attention. I thought more people were using the multi-wallpaper feature of compiz and expected an outcry and quick fix but none never came. I really appreciate you posting the solution. This worked on both my desktop and laptop.

For those who might not be so informed about using the terminal, here is how you would go about copying the files over the corrupt files.

From the terminal, you will need to type the following and enter your password when prompted. Note that I unzipped the new files in the "Downloads" directory and if you used another directory, you would need to substitute the folder name and/or path in which you downloaded it:

sudo cp /home/your_home_directory_name/Downloads/usr/lib/compiz/libwallpaper.a /usr/lib/compiz/
/home/your_home_directory_name/Downloads/usr/lib/compiz/libwallpaper.la /usr/lib/compiz/
/home/your_home_directory_name/Downloads/usr/lib/compiz/libwallpaper.so /usr/lib/compiz/

That is all... You might have to restart your system and remember if you were showing the desktop before, you will need to "not show" desktop or desktop icons.

Thanks again for finding the fix...

---

### Post by MysticHLE on 2011-04-12
Worked for me too. Thanks! =D

This bug should be fixed already...there was an update today from the repo to the compiz-plugins, and I was saddened to see that this bug was still around even after the update...so I tried this. =P

---


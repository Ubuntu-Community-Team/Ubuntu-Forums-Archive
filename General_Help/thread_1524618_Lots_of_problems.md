---
title: "Lots of problems"
date: 2010-07-05
forum: General Help
---

### Post by Cant on 2010-07-05
(All of this happened right after I enabled RGBA transparency support in Ubuntu 10.04)
My desktop background is blank. Just white (slightly grey, though) and when I try to change my background it goes black for a few seconds and then white again. I've tried rebooting, logging back in, telling Wally to switch wallpapers but to no avail. It's just blank.
Also, (and I have a strong suspicion that this is just some option in Compiz that I accidentally clicked) when I move the cursor to the left side of the screen I switch windows.

---

### Post by -humanaut- on 2010-07-05
You need to disable the RGBA transparency and it is a compiz setting thats switching your windows its called screen edge.

---

### Post by Cant on 2010-07-05
> **-humanaut- said:**
> You need to disable the RGBA transparency and it is a compiz setting thats switching your windows its called screen edge.

But how is the RGBA transparency causing the wallpaper blankness?

---

### Post by BikeHelmet on 2010-07-05
Your videocard and/or drivers don't support it?

---

### Post by Cant on 2010-07-05
Disabling RGBA transparency didn't do anything. At all. And yes, my drivers and videocard support it.

---

### Post by Cant on 2010-07-06
Bump

---

### Post by Cant on 2010-07-07
Bump.

---

### Post by Furry_Fighter_20x66 on 2010-07-07
It looks like you have encountered the same problems I did. My problem was much much worse though. Any time I made any changes to the background image, in color chooser or appearance preferences, my system would freeze up leaving me having to do the Ralt-PrtScn-k combo to get back to a login screen. Even leaving it would cause the system to freeze up after a while. 

I would recommend purging it from your system, unless you want to help the guys working on it with bug reports or something. Go to System > Preferences > Gnome Color Chooser and on the "Engines" tab, uncheck the "Global" box. This will disable the RGBA transparency. Then get it out of your system by 'sudo ppa-purge ppa:erik-b-andersen/rgba-gtk'.

I'll just have to live without that fancy transparency until it becomes much more stable. But a big kudos does definitely go out to the people working on it -- it looks very impressive. 8)

---

### Post by Cant on 2010-07-07
> **Furry_Fighter_20x66 said:**
> ...Then get it out of your system by 'sudo ppa-purge ppa:erik-b-andersen/rgba-gtk'.

sudo: ppa-purge: command not found

---

### Post by Furry_Fighter_20x66 on 2010-07-07
My apologies. I forgot that PPA-Purge script isn't available in the repos. You can download and install it using dpkg from this link [https://launchpad.net/%7Exorg-edgers/+archive/ppa/+files/ppa-purge_0.2.6%7Ekarmic_all.deb](https://launchpad.net/%7Exorg-edgers/+archive/ppa/+files/ppa-purge_0.2.6%7Ekarmic_all.deb)

---

### Post by Cant on 2010-07-08
Ok, I've run the command. Do I have to log out/restart/whatever? I ask because nothing changed when the purge was completed.

---

### Post by Furry_Fighter_20x66 on 2010-07-08
Do a restart. You may have to change a few settings afterwards, but generally everything should go back to the way things were. (Fingers crossed.) I generally had some more problems but I solved them by going back into System -> Preferences -> Appearance and then re-selecting the same themes again.)

If you would like to bring some transparency, I received an email yesterday from someone here on the forums whom after reading my problems was telling me how to get a little of that functionality going, at least with menus using compiz. You can see in the picture an idea of how it will look when it is working.

If you go into System -> Preferences -> CompizConfig Settings Manager,
Select the Opacity, Brightness, and Saturation.
Under the Opacity tab, for Window Specific Settings, place the following in:
Windows: 'type=Tooltip | Menu | PopupMenu | DropdownMenu'
Window Values: 80 (or whatever percentage of transparency you would like)
Then to make things a little easier to read, return back to the main menu in CompizConfig and select "Blur Windows" from the effects.
In this setting make your Blur Filter to be a Gaussian and your Gaussian radius anything from a 4 to a 6 or so. Whatever your discretion.

At least it will make things a little more fancy until the problems that plague us with rgba can be solved.

---

### Post by Cant on 2010-07-09
> **Furry_Fighter_20x66 said:**
> Do a restart. You may have to change a few settings afterwards, but generally everything should go back to the way things were. (Fingers crossed.) I generally had some more problems but I solved them by going back into System -> Preferences -> Appearance and then re-selecting the same themes again.)

If you would like to bring some transparency, I received an email yesterday from someone here on the forums whom after reading my problems was telling me how to get a little of that functionality going, at least with menus using compiz. You can see in the picture an idea of how it will look when it is working.

If you go into System -> Preferences -> CompizConfig Settings Manager,
Select the Opacity, Brightness, and Saturation.
Under the Opacity tab, for Window Specific Settings, place the following in:
Windows: 'type=Tooltip | Menu | PopupMenu | DropdownMenu'
Window Values: 80 (or whatever percentage of transparency you would like)
Then to make things a little easier to read, return back to the main menu in CompizConfig and select "Blur Windows" from the effects.
In this setting make your Blur Filter to be a Gaussian and your Gaussian radius anything from a 4 to a 6 or so. Whatever your discretion.

At least it will make things a little more fancy until the problems that plague us with rgba can be solved.

Yeah.. Nothing happened. My background is still blank.

---

### Post by Furry_Fighter_20x66 on 2010-07-09
Hmm... Oh yeah. I forgot that afterwards I had to go back into System -> Preferences -> Appearance and select a different wallpaper and then the old one again to 'remind' the computer of my background image.

Also, if this fails, go into CompizConfig and make sure the Wallpaper option is unchecked. Then logout/login again.

Another step to try is under the Visual Effects tab of Appearance Preferences (where you select the background image). Set your Visual Effects back to none and see if your wallpaper starts to work again. I would also log out/in again as an added step even though it shouldn't be necessary.

Unless anyone reading has some thoughts otherwise, I am still thinking this is a setting problem left over from the install of RGBA because this happened almost immediately after installing RGBA, correct? If these three steps don't bring back your wallpaper then I have a few more things to try yet.

---

### Post by Cant on 2010-07-09
> **Furry_Fighter_20x66 said:**
> Hmm... Oh yeah. I forgot that afterwards I had to go back into System -> Preferences -> Appearance and select a different wallpaper and then the old one again to 'remind' the computer of my background image.

Also, if this fails, go into CompizConfig and make sure the Wallpaper option is unchecked. Then logout/login again.

Another step to try is under the Visual Effects tab of Appearance Preferences (where you select the background image). Set your Visual Effects back to none and see if your wallpaper starts to work again. I would also log out/in again as an added step even though it shouldn't be necessary.

Unless anyone reading has some thoughts otherwise, I am still thinking this is a setting problem left over from the install of RGBA because this happened almost immediately after installing RGBA, correct? If these three steps don't bring back your wallpaper then I have a few more things to try yet.

Still nothing oh god oh god oh god

---

### Post by Furry_Fighter_20x66 on 2010-07-09
Hey Hey... Easy Easy... Don't freak out. Like I said, there is more things to try yet. I still believe this is some quirky setting causing you trouble, but I am opening my mind to the possibility that problems may have arisen from somewhere else.

Now I will get you to try this. Go to System -> Administration -> Users and Groups. Make yourself a new user account, log out of your existing one and then log into the new one. This step is only to see if you can use the wallpaper properly with a new account. (Plus it never hurts to have a backup account in case you can't log into your main one.) If you have your wallpaper working with the new account that's a very good sign. It means your problem with your main account is some setting somewhere.

If it does work with the new account, then I'll next get you to move the old settings to backups in your main account so it can start fresh while keeping your documents and other relevant files intact. But first I will wait until you have had the opportunity to try creating this new account first. We won't waste time with this next step if the account creation trick doesn't work.

Keep me posted.

---

### Post by Cant on 2010-07-10
Didn't work.

---

### Post by Furry_Fighter_20x66 on 2010-07-11
Sorry for the delay in getting back to you. Was out today sick. In fact I am still not so great yet so I may be a little spotty on responding over the next few days.

So let's try a couple of more things.

Under System -> Preferences -> Appearance, turn the Visual FX to none and then go back into the wallpaper and select no wallpaper (The first image) and then select your regular wallpaper again. If this works, you can try turning back on the Visual FX again and see how things work. This was a problem and a fix that I found on one of the forums elsewhere.

Another step to try is to go into System -> Administration -> Hardware Drivers and disable the driver (the remove button). Reboot and login again. Try getting your wallpaper to work again. If it should start to work now, then go back into Hardware Drivers, reactivate your driver and keep working your way back to everything working until you have everything the way it was.

I would also like you to post the make of your video card now if none of these above work for you. If you are not certain, you can obtain it using a terminal and the command "sudo lshw"

Keep me posted.

---

### Post by Cant on 2010-07-11
> **Furry_Fighter_20x66 said:**
> Under System -> Preferences -> Appearance, turn the Visual FX to none and then go back into the wallpaper and select no wallpaper (The first image) and then select your regular wallpaper again. If this works, you can try turning back on the Visual FX again and see how things work. This was a problem and a fix that I found on one of the forums elsewhere.

This works for a few seconds, then blank. I have an nVidia G72M graphics card.

Edit: The driver thing doesn't work. It switches wallpapers properly now but after the wallpaper has changed it starts to "flash"(Dunno how to put this, it looks normal but becomes blank and then normal again in a blink of an eye..).

---

### Post by Furry_Fighter_20x66 on 2010-07-12
Hi Cant:

I'm still working on your problem, but I am suffering from a real massive hangover from a cocktail of over-the-counter drugs to fight this nasty flu bug I have contracted. In a nutshell; Thinking=pain. Same problem that plagues most politicians.

If you could, I would appreciate it if you could post the last 300 or so entries from one of your logs so I can see what was installed/removed from your system during this last few days since this all stated with RGBA. If the log doesn't go back far enough you can always rerun it with a higher number.

> tail -n 300 /var/log/dpkg.log > ~/Desktop/dpkg-log-to-upload.txt
Then just upload the file that it generates on your desktop to here. Thanks.

---

### Post by Cant on 2010-07-12
> **Furry_Fighter_20x66 said:**
> Hi Cant:

I'm still working on your problem, but I am suffering from a real massive hangover from a cocktail of over-the-counter drugs to fight this nasty flu bug I have contracted. In a nutshell; Thinking=pain. Same problem that plagues most politicians.

It's fine, I have all summer to get this problem solved.

The file is too big (347 Kb, WTF) but I removed some useless programs (mostly video & audio converters & transcoders) and installed Gnome color chooser and a few games.

---

### Post by Furry_Fighter_20x66 on 2010-07-12
If you could send it so I could see it, it might help me figure out what's going on. You can post that file either here as an attachment or you can send it to me as a private message. Thanks. You should be able to send a file that size easily.

---

### Post by Cant on 2010-07-17
Can I send it as an attachment to a PM? Because it's _way_ too long for the PM (32000 characters).

---

### Post by Cant on 2010-07-18
bump

---


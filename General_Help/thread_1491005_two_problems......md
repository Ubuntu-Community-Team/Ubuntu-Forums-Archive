---
title: "two problems....."
date: 2010-05-23
forum: General Help
---

### Post by learning_ on 2010-05-23
so, i'm obviously still learning some stuff, and i've come to a few problems. some of which i feel you may be able to help me with. btw, im using lucid, im sure that'll help somehow

1) empathy. it was installed, working just fine, everything was good. then i shutdown my system last night. when i pulled it back up tonight, it wasn't letting me log in to any of my accounts. i've tried to log in to the account directly (online) and thats working fine. i'm assuming its a problem with empathy.

2) Virtual Box. now this one is just a pain, and there are multiple problems with it. the most concerning is that i cannot mount anything onto any os i load onto it. i can't seem to figure out why. the other problem i have continually, when i restart my sys then try to start (for example) a Windows Os, it gives me an error saying something along the lines of "Not able to open because the kernel is not configured properly" or something like that. then it tells me to run [/etc/init.d/vboxdrv setup] ... so i do, and its all good. but its becoming bothersome.

3) Wine. i've been told that i can configure wine to do just about anything i want it to (regarding windows programs atleast) but i cannot figure out how to do that. just for an example, i downloaded iTunes, and i went through the sync process of iTunes with my music files, but it would not recognize my iPod. i tried many things but nothing i did allowed it to recognize that there was an ipod connected to the system. i'm guessing its a problem with mounting or something. 

well thank you in advance for the help.

---

### Post by inameiname on 2010-05-23
Let's see if I can help you:

1) If all else fails and you simply can't use empathy, just 'sudo apt-get remove empathy', and then 'sudo apt-get install empathy', and that should fix whatever might have happen. Of course you'll have to put in your accounts again, but hopefully that's all. Not really sure what might've happened.

3) While I don't use it, I have tried it and read that iTunes has issues with Wine. From what I recall there are certain versions of it that work fine, others will just mess things up. Maybe that's what's happened to you. I've installed it on a friend's computer and it had trouble recognizing her iPod as well. If the only reason you require it is to sync up with your iPod, not for downloading and buying music through it, why not just use Rhythmbox? And as for tweaking Wine, you can just go to 'configure' wine in the program menu, or perhaps try out "winetricks", which can help you do all sorts of things. Though, not sure what help they'd give you in this situation. 

Oh, and as for your # 2), I have never used Virtualbox, so I have no idea how to help, sorry. 

PS. Winetricks link is: [http://winezeug.googlecode.com/svn/trunk/winetricks](http://winezeug.googlecode.com/svn/trunk/winetricks)

---

### Post by learning_ on 2010-05-26
> **inameiname said:**
> Let's see if I can help you:

1) If all else fails and you simply can't use empathy, just 'sudo apt-get remove empathy', and then 'sudo apt-get install empathy', and that should fix whatever might have happen. Of course you'll have to put in your accounts again, but hopefully that's all. Not really sure what might've happened.

3) While I don't use it, I have tried it and read that iTunes has issues with Wine. From what I recall there are certain versions of it that work fine, others will just mess things up. Maybe that's what's happened to you. I've installed it on a friend's computer and it had trouble recognizing her iPod as well. If the only reason you require it is to sync up with your iPod, not for downloading and buying music through it, why not just use Rhythmbox? And as for tweaking Wine, you can just go to 'configure' wine in the program menu, or perhaps try out "winetricks", which can help you do all sorts of things. Though, not sure what help they'd give you in this situation. 

Oh, and as for your # 2), I have never used Virtualbox, so I have no idea how to help, sorry. 

PS. Winetricks link is: [http://winezeug.googlecode.com/svn/trunk/winetricks](http://winezeug.googlecode.com/svn/trunk/winetricks)

1) i tried removing empathy and reinstalling, problem remained. i can access the account elsewhere, such as through yahoo messenger on a windows comp, but wont work on empathy. i dont know why. the previous messenger service they used in older lts releases worked fine, i think i'll just install that.

2) well thanks anyway, im sure someone will know

3) i use rhythmbox to upload but there are bugs. the music is there, but it doesnt stay orginized the way i tell it to. i'm sure i'll figure it out at somepoint.

thanks for the winetricks, thats actually very helpful! ha

---

### Post by new_tolinux on 2010-05-26
> **learning_ said:**
>  btw, im using lucid, im sure that'll help somehow
I'm not, so menu-entries can slightly differ from version to version.
> **learning_ said:**
> 1) empathy. it was installed, working just fine, everything was good. then i shutdown my system last night. when i pulled it back up tonight, it wasn't letting me log in to any of my accounts. i've tried to log in to the account directly (online) and thats working fine. i'm assuming its a problem with empathy.
Instead of the suggested apt-get remove empathy I would suggest "sudo apt-get purge empathy" and then re-install it. The difference between "remove" and "purge" is that "remove" does remove the application, but not it's data. "purge" does remove the application _and_ it's data.

> **learning_ said:**
>  2) Virtual Box. now this one is just a pain, and there are multiple problems with it. the most concerning is that i cannot mount anything onto any os i load onto it. i can't seem to figure out why. the other problem i have continually, when i restart my sys then try to start (for example) a Windows Os, it gives me an error saying something along the lines of "Not able to open because the kernel is not configured properly" or something like that. then it tells me to run [/etc/init.d/vboxdrv setup] ... so i do, and its all good. but its becoming bothersome.
It would be nice if you could specify any error it gives you when you try to mount something.
I guess since you're using Lucid there have been some kernel-updates, so it should not be a big surprise that you'll have to reconfigure the kernel after that. Maybe you can check if the problem also occurs if you reboot the computer when you haven't installed any applications or updates after the last time you've reconfigured virtualbox.

> **learning_ said:**
>  3) Wine. 
I don't use it myself, I know next to nothing about it, so no luck there.

---

### Post by obscurant1st on 2010-05-26
1.
for the first one i would recommend the same. Like remove it using that purge option, then issue the command,
> sudo apt-get autoremove
sudo apt-get update

then install empathy again, i hope it works, if not why not use pidgin for some days, and then try it again. I know its a lame solution. but if its something like urgent, this will help!! :)

2.
I dont know man, you better ask help in IRC-> irc.freenode.net #vbox
Or just ask in their forums.

3.
Wine doesnt work with itunes to sync it with Itouch/iphone. I have tried it several times iwht no luck. Atleast i used VBox to sync it. But later i ended up installing Mac itself on my PC. :)

---

### Post by inameiname on 2010-05-26
Yeah, I agree. "sudo apt-get purge empathy" might work. Doesn't make any sense otherwise. 

Perhaps download and install Bleachbit. It's good to clean up all sorts of things, perhaps things other terminal means might miss in cleaning, idk.

If all else fails, I guess Pidgin (the older messenger app that Ubuntu used to have as default) works just fine too.

And as far as your ITunes woes, guess I don't really know. I've never really used Rhythmbox or with Windows, Windows Media Player, or whatever to sort and add/remove music on my mp3 players. It's far easier for me to skip those supposedly helper apps and just plug in, wait until the browser for the device pops up, and add/remove that way, like files, and save them in my Music folder in my home directory. IPods I've used in the past work that way just fine. But to each their own of course.

---

### Post by learning_ on 2010-05-29
well, i purged empathy, didnt work. ohwell, i got used to pigeon before with jaunty so i'll just install that in the mean time. 

I was using itunes as an example. I have actually reconfig'd the kernel a few times, vbox works like a dream now, so im just using that with itunes. with wine i was more talking any win app/programs. mostly going to be using wine for gaming.

---

### Post by learning_ on 2010-05-29
> **learning_ said:**
> well, i purged empathy, didnt work. ohwell, i got used to pigeon before with jaunty so i'll just install that in the mean time. 

I was using itunes as an example. I have actually reconfig'd the kernel a few times, vbox works like a dream now, so im just using that with itunes. with wine i was more talking any win app/programs. mostly going to be using wine for gaming.

ok there is one problem with vbox. when i try to run an os i have on there, it gives this error:

---

### Post by new_tolinux on 2010-05-29
> **learning_ said:**
> ok there is one problem with vbox. when i try to run an os i have on there, it gives this error:
Well..... then why not do what the error-message tells you to do?

---

### Post by learning_ on 2010-05-30
> **new_tolinux said:**
> Well..... then why not do what the error-message tells you to do?

i do, it continually pops up. i now have an quicklink to it because it happens every time. is there a reason for this?

---

### Post by 3rdalbum on 2010-05-30
People:

Please stop suggesting to the OP that he "sudo apt-get removes" Empathy and then reinstalls it. This will ONLY remove the program itself and replace it with a new copy that is probably 100% the same as what was just removed.

The problem is more likely to be in the Empathy preferences file. Unfortunately I'm not sure exactly where these all are, but there are definitely some in the .gnome2, .config, .local and .gconf/apps/empathy folders in your home directory. Perhaps you'd be able to find more of them. Delete these and the first time you start Empathy it will be as though it's never been run before.

I hope I'm not the first to tell you this, but Wine doesn't work with everything. In fact, I'd estimate that Wine only works with around 20% of Windows programs. There's a great animated graph on the Wine page on Wikipedia that shows the number of Windows programs reported as "don't work at all" as being bigger than the number of programs reported as "work perfectly".

I don't think you could ever sync an iPod with iTunes on Wine anyway; it probably requires very low-level access to the system, because remember on Windows you need an "iPod driver".

For your Virtualbox problem, install the "dkms" package and it will automatically rebuild the Virtualbox driver whenever you have a kernel update. You have another problem with Virtualbox, one that you never really explained - what do you mean by "you can't mount anything onto any OS you install"? Remember, a disk can only be directly mounted by ONE operating system at a time, which will always be the host OS and not the guest (exception: USB devices, if you are using the "Host Passthrough" function of Virtualbox; they can be mounted in the guest, but not in the host).

If you want to access another internal disk, you must mount it in the host OS and then set it as a Shared Folder in Virtualbox.

---

### Post by learning_ on 2010-06-01
> **3rdalbum said:**
> 

The problem is more likely to be in the Empathy preferences file. Unfortunately I'm not sure exactly where these all are, but there are definitely some in the .gnome2, .config, .local and .gconf/apps/empathy folders in your home directory. Perhaps you'd be able to find more of them. Delete these and the first time you start Empathy it will be as though it's never been run before.

I hope I'm not the first to tell you this, but Wine doesn't work with everything. In fact, I'd estimate that Wine only works with around 20% of Windows programs. There's a great animated graph on the Wine page on Wikipedia that shows the number of Windows programs reported as "don't work at all" as being bigger than the number of programs reported as "work perfectly".

I don't think you could ever sync an iPod with iTunes on Wine anyway; it probably requires very low-level access to the system, because remember on Windows you need an "iPod driver".

For your Virtualbox problem, install the "dkms" package and it will automatically rebuild the Virtualbox driver whenever you have a kernel update. You have another problem with Virtualbox, one that you never really explained - what do you mean by "you can't mount anything onto any OS you install"? Remember, a disk can only be directly mounted by ONE operating system at a time, which will always be the host OS and not the guest (exception: USB devices, if you are using the "Host Passthrough" function of Virtualbox; they can be mounted in the guest, but not in the host).

If you want to access another internal disk, you must mount it in the host OS and then set it as a Shared Folder in Virtualbox.

Thank you, you are the first to mention the empathy pref folders. i had no idea where to find those. i did delete them and now it works like it did before.

as far as wine, i know it wont work with everything perfectly. i was more just trying to figure out how i would go about configuring wine when i installed a program and how i would be able to determine whether it would work or not.

i know itunes would not work with wine, that was the first thing i found out about it. however i know it would work through vbox. 

as far as mounting, for awhile it would not let me mount usb devices for whatever reason. after so many kernel recompilations, i guess it just sort of ... fixed that. before when i would go to have it mount a disk, or a usb device, the menu would come up, but everything would be grayed out, not available to be selected. it seems to work ok now though.
how would i go about installing the dkms?

never mind, i just checked and found out what dkms is. apparently its installed by default and is up to date... now what?

---


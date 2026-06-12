---
title: "Log of boot process?"
date: 2006-01-31
forum: General Help
---

### Post by steevc on 2006-01-31
I'm having a problem with my rcX.d scripts. I think it's actually /etc/rcS.d/S48console-screen.sh as that contains the last message I see before the error. Would there be any problems with me temporarily renaming that link to see if I still get the error?

Is there a log file that might give me more details than I see when I do Ctrl-Alt-F8?

I've reported my issue [here]("http://www.ubuntuforums.org/showthread.php?t=120037"), but have had no responses so I'm trying a more general query.

Thanks

---

### Post by mlomker on 2006-01-31
You can edit the /etc/default/bootlogd file and set it to 'yes'.  That'll cause the boot.log to be created in /var/log.  I don't leave that enabled because it use to error out if you didn't manually delete the old .log file...not sure if that's still the case.

I'd recommend downloading **bum**, which allows you to easily toggle scripts on and off.

---

### Post by steevc on 2006-02-01
I installed bum and used that to activate bootlogd. bum didn't seem to show the rcS.d scripts.

Since then when I boot up it seems to be running everything! I actually see bootlogd fail in the Kubuntu startup screen, but I think it is running. All very strange.

My system started off on Hoary to which I added the Kubuntu stuff and later upgraded to Breezy. I'm tempted to start again with a fresh Breezy install in the hope that it will sort out some of my issues, but this will obviously involve lots of re-installing of all the extra stuff I added.

---

### Post by mlomker on 2006-02-01
Bum won't show the rcS.d scripts by design.  It's one of those philisophical linux arguments.  Oh, well.

---

### Post by steevc on 2006-02-03
I thought that bootlogd had stopped the error from happening. It doesn't, but it does allow the later scripts to run. I do get a bit of strange switching between screens.

If I look in /var/log/boot I see

Setting up general console font...       set_kernel_font: Invalid argument

Still don't know how to fix that, but it doesn't seem to be breaking anything that I can see.

---

### Post by Brando569 on 2006-02-05
yea theres a bug with bootlog that makes it say it failed but it still logs everything. as for editing the RcS.d scripts try the [Debian services control panel]("http://www.kde-apps.org/content/show.php?content=28542") its a great program that allows you to edit ANYTHING, but doesnt offer the descriptions for anything. for that i recommend this guide: [HowTo: Speed up ubuntu boot process - the way you can feel it.]("http://www.ubuntuforums.org/showpost.php?p=487138&postcount=1") thats what ive been using, they work great together. if the repo for the DSCP doesnt i have it attached, look in the folder called 'web' and install the deb in there ;)

---


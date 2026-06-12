---
title: "SkyClone - Sync ubuntu and android wirelessly without the cloud."
date: 2011-07-18
forum: General Help
---

### Post by not_insane on 2011-07-18
Hi,
I've been working for the past day or two on a simple project to keep ubuntu and android in sync. I call it SkyClone because Sky != Cloud and Clone = Keeping a folder the same as another somewhere else. I wrote it because I was slightly frustrated that the only way to keep files between ubuntu and android (namely music) was by buying an ubuntu one subscription (I dont want to pay to just sync two devices less than half a metre away from each other, and then send files over the internet to a cloud and back over my slow internet connection).

I don't know if there are bugs that need to be addressed (works for me though), so I'm putting it here for people to test it. Currently it is configured to sync files from a folder you specify on your linux box to the Music folder in your external storage device on android (for most people, that's your sd card). I may add more configuration options later for sync'ing multiple folders and stuff, but for now it just syncs your music automatically over wifi.

Please backup the contents of the Music folder on your phones sdcard just in case.

I have packaged the daemon as a deb, and the android client as an apk (android 2.2+). The source and installer downloads are available at [https://launchpad.net/skyclone](https://launchpad.net/skyclone)

1. Please install the deb through the terminal using "sudo dpkg -i (package name)", as it has prompts for setting up the config file.

2. The android apk should install but not show a launcher icon. This is because it integrates with the accounts & sync manager. Go to settings > accounts & sync > add account, select SkyClone and take it from there. After authenticating, wait a few seconds for it to register with the system and touch the account you just created and tick the checkbox marked "Sync Music".

3. Assuming you have a strong wifi signal (so the connection wont get interrupted), it should start syncing. Wait for it to finish syncing and check out your synced music!

If you have any problems, make sure your firewall allows incoming tcp traffic on port 7272 and DroidWall on your phone (if you have it) will allow SkyCloneClient to connect via wifi.

If it works, yay! Please do tell me.
If it doesnt, please do tell me so I can attempt to fix it! Include the contents of /var/log/syslog and logcat on the phone ("adb shell logcat" when the phone is connected with usb debugging turned on)

---

### Post by not_insane on 2011-07-31
I guess no-one is really interested in this sort of thing. Or it may have fallen down after I posted this in Tutorials & tips and it got moved. I have no idea if this works for anyone else, but if it does please do post here. May I also add, you need to have the android sdk to run adb shell logcat. I think theres an app on the market called alogcat that lets you get it from the device without the sdk.

---

### Post by markp1989 on 2011-08-17
just tested this on my 64bit desktop.

I had to install using sudo dpkg -i --force-architecture skycloned_1.0-1_i386.deb I got no prompts, Errors were encountered while processing:
 cd
 skycloned:i386



I'm having problems running the daemon on the machine.

when running I get error:
```

 skycloned -n
starting
error reading /etc/skycloned.conf: No such file or directory
mark@marks-desktop:~$ 


```

I could manually make the file but i have no idea what needs to be in it?

edit: just look at the postinst script in the deb file, added a password on the first line and a folder on the 2nd line, will test it and post back :)


edit1: got syncing to work, one thing I noticed is that "watchdog" complains about high cpu usage from skyclone during the syncs.

would it be possible to have a checkbox, to only sync when charging, as syncing 1 album has taken about 20% of my battery.

---

### Post by andypi on 2011-08-20
This is *exactly* what I'm looking for, though for everyday use I'm obviously keen for something which is mature and allows me arbitrary control over which folders are sync'd (not just the music folder, as here).

It's astounding to me that this is something that is still difficult to do, but I suspect google isn't too interested in helping people keep their devices in sync *without* using their cloud-based services.

What are your plans for this project?

---

### Post by not_insane on 2011-08-22
> **markp1989 said:**
> just tested this on my 64bit desktop.

I had to install using sudo dpkg -i --force-architecture skycloned_1.0-1_i386.deb I got no prompts, Errors were encountered while processing:
 cd
 skycloned:i386



I'm having problems running the daemon on the machine.

when running I get error:
```

 skycloned -n
starting
error reading /etc/skycloned.conf: No such file or directory
mark@marks-desktop:~$ 


```I could manually make the file but i have no idea what needs to be in it?

edit: just look at the postinst script in the deb file, added a password on the first line and a folder on the 2nd line, will test it and post back :)


edit1: got syncing to work, one thing I noticed is that "watchdog" complains about high cpu usage from skyclone during the syncs.

would it be possible to have a checkbox, to only sync when charging, as syncing 1 album has taken about 20% of my battery.

Hi,
I don't have access to a 64-bit install (gasp!), mainly because I'm on my netbook most of the time. You're free to compile it for x86_64, and I'm glad it worked for you.
I'm working on a gui for this as a "control panel", which will edit the /etc/skycloned.conf - I'll add an option for laptops to only sync while charging. The syncing process is quite intensive because it tries to suck the files off your laptop as fast as possible, and launches 5 simultaneous connections which download in parallel.

Also, it's important to note that the first sync may take a while and a bit of power, but after that, the server and the android client check md5 hashes of the files to see what's changed, so it should only sync changed files after that (should be less intensive)

> **andypi said:**
> This is *exactly* what I'm looking for, though for everyday use I'm obviously keen for something which is mature and allows me arbitrary control over which folders are sync'd (not just the music folder, as here).

It's astounding to me that this is something that is still difficult to do, but I suspect google isn't too interested in helping people keep their devices in sync *without* using their cloud-based services.

What are your plans for this project?
It's obviously not too difficult to do, and I felt the same way, this is my way of syncing files over my local network - I dont see the sense of files going to google and back just for my phone on my desk.

I plan to add a gui which will edit the /etc/skycloned.conf file and restart the server for the less technically inclined. I plan to add multiple folders support too, any other features you would like to see in the future?

---

### Post by andypi on 2011-08-22
If you're making a simple GUI, a simple pair of checkboxes, for each folder being sync'd

1) Sync from laptop to phone
2) Sync from phone to laptop

So that changes to folder contents are reflected in either or both directions. For example, you might only want to sync the phone's camera folder back to the laptop, while you might conversely sync your music folder from your laptop to the phone. For a 'shared' documents folder, you might want the sync to work in both directions.

---

### Post by badook on 2011-09-01
> **not_insane said:**
> I guess no-one is really interested in this sort of thing. Or it may have fallen down after I posted this in Tutorials & tips and it got moved. I have no idea if this works for anyone else, but if it does please do post here. May I also add, you need to have the android sdk to run adb shell logcat. I think theres an app on the market called alogcat that lets you get it from the device without the sdk.

I love the idea, but without a gui, I don't think it will ever be successful...but it's just what I was looking for, thanks :)

---

### Post by andypi on 2011-09-01
> **not_insane said:**
> I guess no-one is really interested in this sort of thing. Or it may have fallen down after I posted this in Tutorials & tips and it got moved. I have no idea if this works for anyone else, but if it does please do post here. May I also add, you need to have the android sdk to run adb shell logcat. I think theres an app on the market called alogcat that lets you get it from the device without the sdk.

I've now found a way of doing this which uses well-established software:

1) Run an SSH server on the Android phone using QuickSSH or SSHDroid.
2) Mount the phone's SD card on Ubuntu using sshfs.
3) Keep phone up-to-date using Unison (a fantastic piece of software I only just discovered).
Edit: I should add that Unison is run from the Ubuntu machine.

I plan to schedule and automate all of the above, such that my phone stays up-to-date without my intervening.

> **badook said:**
> I love the idea, but without a gui, I don't think it will ever be successful...but it's just what I was looking for, thanks :)

That really depends what you mean by "successful".

---

### Post by M.Thulin on 2012-04-25
i have not installed and tested yet.. will do soon though. 
what i would really like it if u add contact and calendar synch aswell. if i can avoid to use up DL volume for editing and synch'ing contacts i would love it. i dont like the idea of havint to go over a cloud anyway.. when the units are 1 meter apart, tops

i would pay for such an app.. i this going to happen?

---


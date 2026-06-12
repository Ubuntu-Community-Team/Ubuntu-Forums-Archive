---
title: "Update Manager not progressing"
date: 2011-05-18
forum: General Help
---

### Post by smcrossman on 2011-05-18
This is a fairly recent install of 11.04 (on 64 bit machine)...side by side with windows 7.  Still trying to get set up and things downloaded. For the last couple of days Update Manager gets to the Making changes screen the progress bar jumps up to about 50% immediately and then it just sits there.  If I open the details terminal it shows some stuff about the first package and then stops at an [END]  or similar command.  If I go into system monitor it shows the status as sleeping.  I've tried skipping the first file or two (yesterday they were firefox related). Rebooting and starting over. Nothing seems to make a difference.  Now the list of updates today is different than yesterday, probably because I went into Synaptic Package Manager and Ubuntu Software Center working my way through set-up & customization issues.
[http://www.ubuntu.com/support/community](http://www.ubuntu.com/support/community)
Do I need to uninstall or reinstall a particular package to get UM working again?  I'm not skilled in GUI, or even identifying packages, so having an app that pulls in the packages and updates them for me is really appreciated.

I saw another thread about [Xubuntu] and a similar issue, but didn't even know for sure which directory I would need to be in in Terminal to execute those commands to see if it was the same basic issue.

---

### Post by dabl on 2011-05-18
Assuming a working internet connection ...

Open a terminal window and issue these commands:

```
sudo dpkg --configure -a
```

```
sudo apt-get update
```

```
sudo apt-get dist-upgrade
```

```
sudo apt-get clean
```

Post back if any of them fail, or give error output.

---

### Post by smcrossman on 2011-05-19
Well, I don't think the 3rd one worked.  Here's what it listed.  I haven't actually gone in and tried the app yet.  Will do that in a bit....going through posts & mail then I will try update manager.

Reading package lists... Done
suzanna@suzanna-gateway:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
suzanna@suzanna-gateway:~$ sudo apt-get clean
suzanna@suzanna-gateway:~$

---

### Post by dabl on 2011-05-20
The output you showed indicates that there is no problem with your dpkg system -- and that your system is fully updated.  "apt-get clean" returns to the prompt with no output when it finishes emptying the package cache, so that looks correct.

After you installed Ubuntu, did you go in and change the source repositories to remove the CD as a source?  If yes, then possibly it is just the update manager that is misbehaving in some way.  If you will use the three "apt-get" commands that I gave you, in a terminal window or at a tty console, and do that once a week, you can safely ignore whatever nonsense the update manager is doing.  Some updates (mostly involving the video display system) require a system reboot to become effective.

---

### Post by smcrossman on 2011-05-20
Thanks!  As far as changing the repositories...no idea....but I did something that changed repositories when dealing with the NVidia driver issue.  Wonder if that was a general all repositories thing or just a selected set?  I am still totally lost with switching over and trying to absorb everything.  Update manager seems to be running fine....at least assuming I'm all upgraded, since it keeps telling me no updates.  That is a little uncomfortable since with Windows it takes longer to download and install the updates on a new install that the formatting, partitioning, installing and setting up combined!  LOL

I'll keep this thread linked so if I have issues again I have the code to try out first!

---

### Post by dabl on 2011-05-20
Good.

If your system is working correctly, including the Nvidia driver installation, then you would be well-advised to refrain from adding any additional repositories until you are more comfortable with Linux and the process of updating your system.  Once installed and configured to your taste, it is very reliable.  But when "tweaked" by a novice ... well, you might have to join the crowd on this forum again.  :)

---


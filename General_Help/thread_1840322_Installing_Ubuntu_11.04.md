---
title: "Installing Ubuntu 11.04"
date: 2011-09-07
forum: General Help
---

### Post by Wuxin on 2011-09-07
Can Ubuntu 11.04 be installed directly over 10.10 or do you have to uninstall 10.10 and start from scratch?  I have files, music, audio material, etc., neatly tucked away on my current set up and I'd have to reinstall all that material.  I'm still a bit ambivalent about making the upgrade--the forums seem to have mixed reviews about 11.04.  A friend told me he switched to Kubuntu 11.04 which he likes better.  But basically I want to know whether if I do decide to switch to Ubuntu 11.04 the install can be seamless?  (Would it maybe be a good idea to wait for 11.11?)

---

### Post by rolnics on 2011-09-07
Before I go any further, you're number 1 priority is backup your precious data.

I've recently upgraded my Lubuntu install via the command line and I didn't have any problems. Keep in mind though that this isn't my main install, so it's not used day in day out, but I've kept it updated all through 10.10. I also upgrade my other "testing" 10.10 install, as I'd never done an upgrade before, I usually do fresh installs. Again I didn't have any issues, I'm not counting Unity in that as it doesn't like my pc, although I've now installed Unity 2D which is another story.

Upgrading is really a personal thing, it depends on your computer hardware. All I can say it backup your data and give it a go, just be prepared for some breakage, which won't be a problem if you have your data backed up or shouldn't be!

---

### Post by nipunshakya on 2011-09-07
> **Wuxin said:**
> Can Ubuntu 11.04 be installed directly over 10.10 or do you have to uninstall 10.10 and start from scratch?  I have files, music, audio material, etc., neatly tucked away on my current set up and I'd have to reinstall all that material.  I'm still a bit ambivalent about making the upgrade--the forums seem to have mixed reviews about 11.04.  A friend told me he switched to Kubuntu 11.04 which he likes better.  But basically I want to know whether if I do decide to switch to Ubuntu 11.04 the install can be seamless?  (Would it maybe be a good idea to wait for 11.11?)

here is a link for you to get going with your upgrades...and it shows that you can upgrade 10.10 over 11.04...
[http://www.howtoforge.com/how-to-upgrade-ubuntu-10.10-maverick-meerkat-to-11.04-natty-narwhal-desktop-and-server](http://www.howtoforge.com/how-to-upgrade-ubuntu-10.10-maverick-meerkat-to-11.04-natty-narwhal-desktop-and-server)


alternatively, you can try the following too.....

**Upgrading Using the Alternate CD/DVD**

 Use this method if the system being upgraded is not connected to the Internet. 

[LIST=1]
[*]Download the **alternate** installation CD from [http://releases.ubuntu.com/natty/](http://releases.ubuntu.com/natty/) 
[*][Burn the ISO to a CD]("https://help.ubuntu.com/community/BurningIsoHowto#InUbuntu") and insert it into the CD-ROM drive of the computer to be upgraded. 

[LIST]
[*]If the ISO file is on the computer to be upgraded, you could avoid wasting a CD by [mounting the ISO as a drive]("https://help.ubuntu.com/community/ManageDiscImages#MountISOFiles") with a command like: 
sudo mkdir -p /media/cdrom sudo mount -o loop ~/Desktop/ubuntu-11.04-alternate-i386.iso /media/cdrom
[/LIST]
[*]A dialog will be displayed offering you the opportunity to upgrade using that CD. 
[*]Follow the on-screen instructions. 
[/LIST]
If the upgrade dialog is not displayed for any reason, you may also run the following command using Alt+F2: 
    gksu "sh /media/cdrom/cdromupgrade"


though i haven't tried any of the methods of the upgrade yet, i think it should work all fine......or you can wait for the LTS version to be released in April 2012 if you are not in a hurry...goodluck):P

Regards, WinuxUser

---

### Post by Wuxin on 2011-09-07
Thank you.  Yes, I do  have my data backed up although I don't know how easy it will be to transfer because I've never used it before!  I have my entire system backed up on a portable external drive.  They make it sound on the Ubuntu install page like you can make a seamless upgrade without having to do much of anything.  But it may not be as easy as it sounds.  I've also heard there are quirky features (even still) with Unity.  Like I say, my data is backed up but having to relay all that into a new setup might not be easy.

---


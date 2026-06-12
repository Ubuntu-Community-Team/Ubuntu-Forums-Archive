---
title: "Fresh installation on new drive, get settings from old drive?"
date: 2010-02-27
forum: General Help
---

### Post by jjloupe on 2010-02-27
I just installed a Caviar Black 1TB drive, did a new installation of Ubuntu 9.10. I do not have access to the internet on this computer, and was wondering if there is a way to get my old settings/files off the old drive onto the new?
 
Since it is a new install on the 1TB disk, I have no MP3 codec, so I can't play my music...this is bugging me, so I would at least like to get that capability back. Everything else would be a plus!

---

### Post by Barriehie on 2010-02-27
> **jjloupe said:**
> I just installed a Caviar Black 1TB drive, did a new installation of Ubuntu 9.10. I do not have access to the internet on this computer, and was wondering if there is a way to get my old settings/files off the old drive onto the new?
 
Since it is a new install on the 1TB disk, I have no MP3 codec, so I can't play my music...this is bugging me, so I would at least like to get that capability back. Everything else would be a plus!

Your program settings are stored in your $HOME dir and the program config files are stored in /etc/.

---

### Post by oldfred on 2010-02-27
/home has all your settings. If you can still boot or chroot into your old system you can list all the apps you have installed.

[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
I occasionally run this and copy the results file to a location that will be backed up so I have some history in case the worst happens.

If you had added any PPA's or other sources you have to enable them first or it will not download those packages.

I tried to do all my updates for my new install to Karmic from the command line and then I saved history ([COLOR=DarkRed]history[/COLOR] in the terminal) so I have a record of everything I have installed.

---

### Post by Barriehie on 2010-02-27
In regards to oldfred's post/link I run the command like this:
```

dpkg --get-selections | gawk '{ print $1 }' > ~/InstalledPackages.txt

```
The gawk command will ommit the second column of text and preceeding spaces.

Edit: Should you decide to implement some type of backup strategy I backup $HOME and /etc and run the above command 3 times a week.  The backup files are stored on another drive and also copied out to a thumb drive.

---

### Post by dcstar on 2010-02-28
> **jjloupe said:**
> I just installed a Caviar Black 1TB drive, did a new installation of Ubuntu 9.10. I do not have access to the internet on this computer, and was wondering if there is a way to get my old settings/files off the old drive onto the new?
 
Since it is a new install on the 1TB disk, I have no MP3 codec, so I can't play my music...this is bugging me, so I would at least like to get that capability back. Everything else would be a plus!

You will not get multimedia capabilities until you install the relevant packages onto the new machine.

It would have been easier to just copy the existing Ubuntu partition off the old hard drive onto the new drive using the Partition Manager.

---


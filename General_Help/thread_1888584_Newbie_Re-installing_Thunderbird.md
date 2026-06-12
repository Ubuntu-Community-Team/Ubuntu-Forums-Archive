---
title: "Newbie Re-installing Thunderbird"
date: 2011-11-29
forum: General Help
---

### Post by Quarkrad on 2011-11-29
Running 10.10.  I have rebuilt Ubuntu a number of times and reinstalled Thunderbird. I copy the contents of ./thunderbird from a backup copy to ./thunderbird in home on the new build.  The contents of ./thunderbird are in the form of a folder **xxxxxxxx.default** and two files, **appreg** and **profiles.ini** and I have never had trouble before.  I have just had to rebuild a family members Ubuntu 10.10 machine and from memory when I built it I installed Thunderbird from the Software Centre so I'm assuming they had Thunderbird 3.1.15.  Problem I have is the backup ./thunderbird does not have **xxxxxxxx.default**, **appreg** and **profiles.ini** inside, it has a folder called **Profiles**, then **appreg** and **profiles.ini**. The folder [B]xxxxxxxx.default[/B is inside the Profiles folder.  No matter what combination I use (put the Profile folder in home/./thunderbird or copy the xxxxxx.default from the Profile folder and put that in home/./thunderbird) it does not work.  It is possible that the version of Thunderbird on the machine I rebuilt was not 3.1.15?

---

### Post by bluexrider on 2011-11-29
I've never had the issue you are experiencing whenever the upgrade Thunderbird has always seen the files and imported my address book and profiles.   

But to make everything work you also have to have the "imqobi46.default" or something like xxxxxxxx.default file too.

It contains cache, data, mail, cookies, extensions, etc. If you are missing that it probably won't work correctly.

---

### Post by Habitual on 2011-11-29
I just copy all of ~/.thunderbird myself.

---

### Post by Quarkrad on 2011-11-29
Yes I have that folder.  Using your example, in the backup (./thunderbird) folder I have the Profile folder and the two other files. imqobi46.default is inside the Profile folder.  Inside imqobi46.default is all the normal config files/folders including a Chrome folder I created for a userChrome.css file.  If I delete everything in home/./thunderbird and then launch thunderbird it creates is own xxxxx.default folder and appreg, profiles.ini files. If I delete these and substitute with the contents of the backup ./thunderbird folder it will not launch.  I wonder if this is a permissions problem - although it never been an issue before.  I use gksudo nautilus to copy and paste between backup and /home.

---

### Post by bluexrider on 2011-11-29
I don't know it its a version to version thing like going from 3.1 to 5.0 or 5.0 to 3.1 I haven't had the issue either. My only problem was upgrading and missing out on the lightning plug-in.

I doubt its a permissions issue cause the program opens and sets up the config files. I would suggest going to mozilla to find the answer.

---


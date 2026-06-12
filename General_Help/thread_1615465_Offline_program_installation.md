---
title: "Offline program installation"
date: 2010-11-07
forum: General Help
---

### Post by Verbeck on 2010-11-07
is there a way to install programs offline other than apt-on cd and keryx? maybe a script to copy the files on a flash drive to /var/cache/apt/archives

---

### Post by jerkymotion on 2010-11-07
yes even i do have the same problem..
i don't have the internet connection on my home computer..i am newbie to the linux...
normally the packages that i download at the college does not run on my home computer as i don't have internet connection.....
how do download these packages so that i can install the software in my home computer as like in windows
so please help..every help will be appreciated

---

### Post by TVTrukChik on 2010-11-07
You can do this, assuming you have another Linux computer somewhere else with an internet connection.

Open Synaptic Package Manager.  Mark all the packages you'd like to download.  Then, choose "File/Generate package download script" from the menu.  Save the script on your flash drive.  Name the script whatever.sh and be sure to mark it as executable.

Go to a different Linux machine that has Internet access, and run the script on the flash drive.  It will download all the packages you marked in Synaptic.

Plug the drive into the machine without the internet connection, and start Synaptic again.  This time, choose "File/Add downloaded packages" from the menu, and choose your flash drive as the source for the packages.

---

### Post by krishnandu.sarkar on 2010-11-07
Try AptOnCD

---

### Post by Verbeck on 2010-11-07
[@ krishnandu.sarkar]("http://ubuntuforums.org/member.php?u=1063048")
i did say except aptoncd in the first post :|

> **TVTrukChik said:**
> You can do this, assuming you have another Linux computer somewhere else with an internet connection.

Open Synaptic Package Manager.  Mark all the packages you'd like to download.  Then, choose "File/Generate package download script" from the menu.  Save the script on your flash drive.  Name the script whatever.sh and be sure to mark it as executable.

Go to a different Linux machine that has Internet access, and run the script on the flash drive.  It will download all the packages you marked in Synaptic.

Plug the drive into the machine without the internet connection, and start Synaptic again.  This time, choose "File/Add downloaded packages" from the menu, and choose your flash drive as the source for the packages.
  
Thanx :D

---


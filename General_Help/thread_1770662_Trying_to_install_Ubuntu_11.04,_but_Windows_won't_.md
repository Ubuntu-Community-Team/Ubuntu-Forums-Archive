---
title: "Trying to install Ubuntu 11.04, but Windows won't let me dual boot"
date: 2011-05-29
forum: General Help
---

### Post by xVehemencityx on 2011-05-29
Howdy.

When I insert the liveCD for Ubuntu 11.04, and click install, all goes well up until I go to choose my partition.  It says something along the lines of "Windows 7 is currently installed on this computer.  Would you like to: Replace Windows 7 with Ubuntu, or do something else?"  Shouldn't there be an option to install Ubuntu alongside Windows 7?  That's what I'm looking for right now.

---

### Post by xVehemencityx on 2011-05-29
I also tried clicking "Try First" and then going through the installer, and the same problem arose.  I made sure Windows shut down cleanly to make sure that there weren't any issues because of that.

Any clues?

---

### Post by wolfen69 on 2011-05-29
Choose "do something else". Don't worry, it won't overwrite windows. Tell us what it says next.

---

### Post by xVehemencityx on 2011-05-29
Will do.  I'll boot it up real quick.

---

### Post by xVehemencityx on 2011-05-29
Alright, here we go.  

[IMG]http://i.imgur.com/NXzWN.png[/IMG]


And if I click on /dev/sda/, it lets me choose New Partition Table..., but that threatens to delete all of the current partitions, which I obviously don't want.

---

### Post by oldfred on 2011-05-29
Almost all win7 installs use all four primary partitions, so you have no space for anything else.

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first.
HP tools partition discussion:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
Shrinking a Windows 7 partition is best done in Windows. 
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

---

### Post by xVehemencityx on 2011-05-29
Wow, thank you sir.  I forgot all about being able to shrink partitions in windows.  (And sorry about taking so long to respond.  Apparently I never got the email saying that you responded.)

---

### Post by xVehemencityx on 2011-05-29
> **oldfred said:**
> Almost all win7 installs use all four primary partitions, so you have no space for anything else.

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first.
HP tools partition discussion:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
Shrinking a Windows 7 partition is best done in Windows. 
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)


Totally worked.  Thank you, my friend!

---


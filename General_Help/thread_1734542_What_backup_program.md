---
title: "What backup program?"
date: 2011-04-20
forum: General Help
---

### Post by j-peg on 2011-04-20
Hey i have tryed Ubuntu a cuple of times and i always seem to screw something up were i wish i could take my OS back a day or 2, or til last save. But i don't know what too use or what can do that easaly. It needs to be a program where i could maybe set it to automatik and erase all programs or settings i have installed/changed when i go back and retreive a backup.

I'm asking like this because i don't know how backup programs work, since i have never used any before, and have found out it is very nececary in Ubuntu.

---

### Post by Mark Phelps on 2011-04-20
A simple way to take your install back in time would be to image off the partition with a tool like Clonezilla, and then restore the entire partition.  That will certainly get you "back" to a previous state.

But, if you're asking for something like Windows System Restore, that will just return the system files to a previous state, not aware of anything like that.

Also, in Windows, apps are installed using a Windows Installer routine, so it is a simple matter to uninstall an app.  But in Ubuntu, you have several ways to install apps, including compiling from source code.  There is no way a single tool would be able to know what to do to back out apps installed by all the possible methods.

---

### Post by Fire_Chief on 2011-04-20
There are a few options that are modeled similarly to Apple's Time Machine backup.
[URL="http://backintime.le-web.org/"]
Back In Time[/URL]
[TimeVault]("https://wiki.ubuntu.com/TimeVault")
[FlyBack]("http://flyback-project.org/")

Cheers!

---

### Post by j-peg on 2011-04-20
Thanks alot :) I was talking about the programs because i have been using Wine for some programs and everytime, there always goes something wrong so that i can't uninstall the programs again if they don't work. Thats why i wanted something there would delete those files too, but i don't know witch programs i need to use. Also i want the "images" stored on the ubuntu partition on my computer, can these programs do that?

---

### Post by j-peg on 2011-04-20
Was just in reading about clonezilla seems to be what i need, looks like they all a pretty simular but clonezilla was alot better too describe the program ;)

---

### Post by Mark Phelps on 2011-04-21
Realize that Clonezilla support both "disk" backups and "partition" backups.  The first backs up ALL the partitions on a physical drive; the second backs up only the partitions you specify.

Mentioning this in case you have the Wine apps installed to a different partition.

---

### Post by j-peg on 2011-04-21
Thanks my wine programs are installed on the partition so it works great have allready restored twice ;) think that explains some of my ubuntu skills

---


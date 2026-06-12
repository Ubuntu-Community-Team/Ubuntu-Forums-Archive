---
title: "back up and restore"
date: 2012-03-05
forum: General Help
---

### Post by claire14 on 2012-03-05
hi i did a back up with simple back up suite and it has an exclude option on it [http://i42.tinypic.com/x4f2ia.png](http://i42.tinypic.com/x4f2ia.png) , should i of let it exclude those or not , its include list is [http://i43.tinypic.com/2elcu9t.png](http://i43.tinypic.com/2elcu9t.png) and it say's it took up 4gb on a tar file for over 120gb is that a compressed file over 120gb in a 4gb tar file , also i didn't see a back up complete on the screen but its stopped at [http://i44.tinypic.com/vncton.png](http://i44.tinypic.com/vncton.png) ,

also how do i back up from root folder from command line and restore from command line to an external hard drive  with any excludes that have to be done 

 thankyou if anyone helps

---

### Post by seawolf167 on 2012-03-05
It is just fine to leave the default excludes, you can modify the includes based on your personal preferences (i.e. I don't bother backing up my music or movies). For example on the excludes, /media is where things like flash drives are generally mounted, and you don't want to back them up with your system. You can see what each directory holds through a quick Google search (results like [this one]("http://www.thegeekstuff.com/2010/09/linux-file-system-structure/")).

There are many ways to [backup your system]("https://help.ubuntu.com/community/BackupYourSystem#Types_of_Backup"), take a look at them and use the one you feel the most comfortable with:

[LIST]
[*][SimplyBackupSuite ]("https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite")(as you already mentioned)
[*][rsync ]("https://help.ubuntu.com/community/rsync")(or grsync)
[*][tar]("https://help.ubuntu.com/community/BackupYourSystem/TAR")
[*][Duplicity]("https://help.ubuntu.com/community/DuplicityBackupHowto")
[/LIST]

---


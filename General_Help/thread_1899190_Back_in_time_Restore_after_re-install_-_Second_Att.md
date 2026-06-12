---
title: "Back in time Restore after re-install - Second Attempt"
date: 2011-12-23
forum: General Help
---

### Post by wbm on 2011-12-23
**Back in time - restore after re-install**             
                                                                Hello,
I have posted this exact question last year and got only answers that did not address my question.
Hopefully this year someone could please actually answer my question.

I have my system and software and data on my computer on an internal drive.
On that system I have Back in Time backup software.
I use Back in Time, to backup my data to an external drive.

Question:
If my computer dies or my internal drive fails, I have to completely re-install everything including my system and Back in Time.
If I want to restore my data from the good external drive, how can I do that with Back in Time?
Doesn't it keep the Snapshots info or preferences on my dead drive? Or  do I need to point my freshly re-installed Back in Time just to the data  drive and it will recognize the snapshots etc. automatically?
I'd like to know this before anything happens please.
Thanks!!!

In addition, since last year I went through this scenario. I did a complete re-install of the OS and Back in Time (Same drive name, user name, password). I could not find a way to get my data restored with Back in Time as I did not see an option to point Back in Time back to my Backup Drive and see my old Snapshots. It just asked me to set it all up fresh. Luckily I had my data copied to another drive before the fresh install.
Is Back in Time completely useless in this scenario or am I missing something? It appears to be great for the occasional accidentally deleted file, but for data disaster recovery it seems to be useless.

---

### Post by maverickaddicted on 2011-12-23
Have you tried other backup and restoration utility? I read your previous post and this post [http://ubuntuforums.org/showthread.php?t=1696206](http://ubuntuforums.org/showthread.php?t=1696206) and still unsure about the restoration process.

---

### Post by wbm on 2011-12-23
> **maverickaddicted said:**
> Have you tried other backup and restoration utility? I read your previous post and this post [http://ubuntuforums.org/showthread.php?t=1696206](http://ubuntuforums.org/showthread.php?t=1696206) and still unsure about the restoration process.

I am going to try Mint Backup next.
Probably I am just missing something with Back in Time. It would be such a glaring omission in a backup program, if one cannot restore in case of a system failure.
Mint backup has a button right when you start up the program that says restore. Sounds promising :)

---

### Post by cottfcfan on 2011-12-23
Back in Time will only restore the Data you ask it to save.
If I remember correctly I could not get Backintime on 10.10 to be compatible with the one in 11.04.
Since then I've used Luckybackup, (its in software centre).
To restore you can just copy the files straight back to your system.
For a more complete Backup try Clonezilla.

edit. After reading your 1st post again, you can't just install backintime on your new system and restore.
You need to set it up 1st the way you had it before. Your backups should then appear on the left hand side.
Just highlight the one you want to restore and hit the restore button.

---

### Post by wbm on 2011-12-23
> **cottfcfan said:**
> Back in Time will only restore the Data you ask it to save.
If I remember correctly I could not get Backintime on 10.10 to be compatible with the one in 11.04.
Since then I've used Luckybackup, (its in software centre).
To restore you can just copy the files straight back to your system.
For a more complete Backup try Clonezilla.

edit. After reading your 1st post again, you can't just install backintime on your new system and restore.
You need to set it up 1st the way you had it before. Your backups should then appear on the left hand side.
Just highlight the one you want to restore and hit the restore button.

Thank you for the other software suggestions. I will check them out.

Your edit was the first reply that I ever got that actually addressed my question! Thank you!!!
The problem with that approach is that I would have to exactly remember my backup structure (drive names, folder names etc.). I took screen-shots just in case that this would be the only way.

---

### Post by cottfcfan on 2011-12-24
You could just backup your entire Home Directory, that way it's easy to remember if anything goes wrong.

---


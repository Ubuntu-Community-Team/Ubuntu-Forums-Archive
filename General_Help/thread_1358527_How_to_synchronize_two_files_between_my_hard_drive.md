---
title: "How to synchronize two files between my hard drive and my SD card?"
date: 2009-12-18
forum: General Help
---

### Post by Crimson_Tider on 2009-12-18
Hi. I have an ODS spreadsheet file that I keep a copy of in two different places: one on my hard drive and the other on my SD card, which I basically use as my primary file storage in my EeePc netbook. I make changes to both files, and I want to synchronize them from time to time. I have tried using Conduit 0.3.16 for GNOME to do this, but it won't let me simply synchronize a file with another file. I don't want to have to open each file, visually scan each file for the changes, and then copy and paste the new data from one file to the other every time I need to synchronize them. Can anyone tell me an easy way to do this?

Please note that I am somewhat new to Ubuntu and Linux, so use simple words and explain thoroughly. Thanks!

---

### Post by StuartN on 2009-12-18
> **Crimson_Tider said:**
> I make changes to both files, and I want to synchronize them from time to time.

The short answer is that you can not do this. If the two files are different, then you select one of them (usually the most recently edited) and discard any changes made to the other (usually older) file. This is very easy to script, with something like **cp -u source1 source2 ; cp -u source2 source1**.

The long answer is that you could use comma-separated value spreadsheets and a version control system. This would allow you to branch and merge changes, but it is overkill for most regular spreadsheet users.

A third option is to place the master copy of the file on a server (perhaps even Ubuntu One) and only ever change that one copy, with backups before / after every change.

---

### Post by Soapy.Illusions on 2009-12-18
What about using a sym-link would that work

---

### Post by Crimson_Tider on 2009-12-18
> **Soapy.Illusions said:**
> What about using a sym-link would that work
What is sym-link?

---

### Post by dcstar on 2009-12-19
> **Crimson_Tider said:**
> Hi. I have an ODS spreadsheet file that I keep a copy of in two different places: one on my hard drive and the other on my SD card, which I basically use as my primary file storage in my EeePc netbook. I make changes to both files, and I want to synchronize them from time to time. I have tried using Conduit 0.3.16 for GNOME to do this, but it won't let me simply synchronize a file with another file. I don't want to have to open each file, visually scan each file for the changes, and then copy and paste the new data from one file to the other every time I need to synchronize them. Can anyone tell me an easy way to do this?

Please note that I am somewhat new to Ubuntu and Linux, so use simple words and explain thoroughly. Thanks!

Install the **unison** package.

---

### Post by stinkeye on 2009-12-19
[_[COLOR="DarkRed"]luckyBackup[/COLOR]_]("http://luckybackup.sourceforge.net/") has an easy to follow Gui and is in the karmic universe repo.

---

### Post by Crimson_Tider on 2009-12-20
I tried a couple of the things listed by other posters here, but after a little experimenting, I have learned about the existence of and how to use the "Record changes", "Show changes", and "Compare documents" commands in OpenOffice.org Spreadsheet.  So now I can use Conduit Synchronizer to synchronize the directories and all their contents on my SD card and hard drive, and as it does this it finds all the changed files, which it reports as "conflicts", and then I can just use the above commands on each of those files to synchronize their contents.

Thanks for all the ideas!

---


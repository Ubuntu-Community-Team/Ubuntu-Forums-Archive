---
title: "Does deja dup on 12.04 work at all?"
date: 2012-05-22
forum: General Help
---

### Post by gilgongo on 2012-05-22
I'm a little unclear after searching through the bugs - but is anyone able to use Deja Dup on 12.04 at all? I've tried it with a fresh install using U1 and it backs up manually OK, but if you put it on a schedule it crashes with an unknown error about SSL timeout after a while. Same again (different error) with S3. 

If I try running the same backup using duplicity on the CLUI it just core dumps immediately.

:(

---

### Post by wilee-nilee on 2012-05-22
> **gilgongo said:**
> I'm a little unclear after searching through the bugs - but is anyone able to use Deja Dup on 12.04 at all? I've tried it with a fresh install using U1 and it backs up manually OK, but if you put it on a schedule it crashes with an unknown error about SSL timeout after a while. Same again (different error) with S3. 

If I try running the same backup using duplicity on the CLUI it just core dumps immediately.

:(


Not sure, I use grsync, it saves in a accessible format only when asked to. 

It is just a gui for rsync.

---

### Post by gilgongo on 2012-05-22
I could use grsync, but I'd rather use my 5GB of free space on U1 (and I'm not sure if grsync does incrementals).

---

### Post by wilee-nilee on 2012-05-22
> **gilgongo said:**
> I could use grsync, but I'd rather use my 5GB of free space on U1 (and I'm not sure if grsync does incrementals).

It does it will save in the same file and remove or keep the old stuff depending on the settings. 

So say you had a download you have saved somewhere else, or don't need it will be removed if gone on the grsync run if it was there before, but gone from your setup being saved.

Both I believe are basically grsync gui's, I like grsync really because it saves as is you can open it and it looks the same, I use it to save my home.

---

### Post by ajgreeny on 2012-05-22
> **wilee-nilee said:**
> It does it will save in the same file and remove or keep the old stuff depending on the settings. 

So say you had a download you have saved somewhere else, or don't need it will be removed if gone on the grsync run if it was there before, but gone from your setup being saved.

Both I believe are basically grsync gui's, I like grsync really because it saves as is you can open it and it looks the same, I use it to save my home.
I agree fully with what I think wilee-nilee is saying.

I have been using grsync for a long time now (about 4 years or more) to backup my home and it has always been an incremental backup, with only files that are new, or have been changed in some way being copied across to my external hard disk.

Every so often I need to sift through the backups and remove those files I am certain I will never need again, or to purge those that I have perhaps moved in my file system, and would otherwise end up with duplicates, but that is never too much of a job.

There is an option in grsync to delete all files not on the source, ie, my home, but I do not want to use that as it will also delete files I do want to keep, but that I have removed from my home to save space.

---

### Post by gilgongo on 2012-05-23
OK so a I take it that this is a "no" to my original question. Deja Dup doesn't work on 12.04. Kinda strange as it's installed by default. 

Oh well.

---

### Post by ajgreeny on 2012-05-23
> **gilgongo said:**
> OK so a I take it that this is a "no" to my original question. Deja Dup doesn't work on 12.04. Kinda strange as it's installed by default. 

Oh well.
Actually, I can't answer that question as I have not tried deja-dup on any ubuntu version, and I am not yet using 12.04, just testing it on a small extra partition of my desktop machine which will not run unity 3D, so I'm using the classic desktop with gnome panel, etc etc.

It's looking good so far, and I can forget I'm using gnome 3 and all that it entails, as it is so very like gnome 2.  It maybe is the next port of call for me, rather than xubuntu or lubuntu, which I am also trying on the same desktop machine.  Yes, I have 5 OSs on the machine, but have kept their homes separate from each other, and justv link all my data files from my main OS (10.04) home partition to the others.

---

### Post by colin.p on 2012-05-23
I am using 12.04 and do backups with Luckybackup, Back in Time, as well as DejaDup. All three work fine even though I only have DejaDup on a scheduled backup. However, I really can't ever see me restoring with DejaDup, as the other two backup to a folder, on an external HD, that is the mirror of "home", so if I screw something up or do a clean install, then I drag it on over.

---

### Post by jadtech on 2012-05-23
its worked fine for me on 12.04, it works doing  back ups to ubuntu one like it should and restores no issues ..

---

### Post by colin.p on 2012-05-23
I would like to do off site backups, but out here in the 3rd world (rural) there is no such thing as broadband. What I do have is wireless internet, however with the speeds of 34 KBps and 1500 ms latency, I refuse to call it broadband (no matter what Xplornet says) and call it wireless "dialup".

---

### Post by donovajf on 2012-06-05
Actually there is a known issue with Deja Dup. 
[[FONT="Fixedsys"][SIZE="2"][COLOR="Blue"]repeatedly asks for encryption password when backing up, even though "remember password" is ticked[/COLOR][/SIZE][/FONT] ]("https://bugs.launchpad.net/ubuntu/+source/deja-dup/+bug/989750")

I am having this issue trying to restore my login directory. I have not seen an update on this since 5/5/2012

---


---
title: "Backup tool."
date: 2012-07-27
forum: General Help
---

### Post by eslavko on 2012-07-27
Hello...

I'm new to Ubuntu. I search the Ubuntu software center (and try) many backup programs. But can't find suitable one. Can someone point me to the right one?
In WinXp I use backup4all.

Now What I expect to can manage.

It must be able to restore (any) version of single file. Ie if I do backup daily and everyday change one file I want to be able to restore that file of any day.

BackupInTime seems close to that but as I see it make full backup every day. And this is little too much..

any help?

---

### Post by hakermania on 2012-07-27
I backup my data daily with the default backup tool that Ubuntu 12.04 comes along with (deja-dup). I am able to restore the files from any date before the current day:
[IMG]http://i.imgur.com/oIBZC.png[/IMG]


You can see some days to have 2 back-ups, but I did them manually (by hand), because I had important things going on and I didn't want to lost them :P

I hope I understood well your question... As for restoring that single file, I don't get where your problem is. Take for example the following situation:
Current Date: 27/7, Restore From: 23/7, Backed-up Folder: /home/alex/Documents/ Restore File: myfile1.txt

So, you want to restore the file myfile1.txt from 23/7 and replace the current myfile1.txt that you have at /home/alex/Documents. Why don't you restore the whole /home/alex/Documents to a random folder (e.g. /home/alex/Documents_temp), and then copy myfile1.txt to /home/alex/Documents and remove /home/alex/Documents_temp folder!

---

### Post by eslavko on 2012-07-27
For archiving the deja-dup is ok.
I have problem when restoring from them.

How to restore single file, and how to find it right release?
Just for example:
I made backup daily.
I have changed my file in monday and wednesday.

Today friday I want to restore monday backup. But I don't remember exactly what day was.. How to find all changes?

And how to restore just one file, not complete archive?!?

---

### Post by hakermania on 2012-07-27
> **eslavko said:**
> For archiving the deja-dup is ok.
I have problem when restoring from them.

How to restore single file, and how to find it right release?
Just for example:
I made backup daily.
I have changed my file in monday and wednesday.

Today friday I want to restore monday backup. But I don't remember exactly what day was.. How to find all changes?

And how to restore just one file, not complete archive?!?

I can't help you with those (I haven't searched it because I am happy with deja-dup), but I'm optimistic that you will find what you are searching for, there are many many backup-tools available!

---

### Post by raja.genupula on 2012-07-27
> how to restore just one file, not complete archive?!?

[http://askubuntu.com/questions/168795/specific-file-backup-from-a-backup-tar/168800#168800](http://askubuntu.com/questions/168795/specific-file-backup-from-a-backup-tar/168800#168800)

---

### Post by dcstar on 2012-07-27
> **hakermania said:**
> I can't help you with those (I haven't searched it because I am happy with deja-dup), but I'm optimistic that you will find what you are searching for, there are many many backup-tools available!

I use Unison for Disaster Recovery backups, nice and quick and only backs up changed files.

---

### Post by eslavko on 2012-07-27
> **raja.genupula said:**
> [http://askubuntu.com/questions/168795/specific-file-backup-from-a-backup-tar/168800#168800](http://askubuntu.com/questions/168795/specific-file-backup-from-a-backup-tar/168800#168800)

Ok that might work but how to find correct tar?!?

---

### Post by eslavko on 2012-07-27
I find BackupInTime to be thing I need.
It just does what I wan't.
But after more testing I find problem as it can't use my external USB drive. Actually it works but eat too much space. Backup source folder is aprox 4G bytes in size, and every snapshot add that amount to the disk. If the destination is internal hard drive then nothing bad happens as files already on drive is just hard linked. But on external drive is actually duplicated. Probably FAT32 is to blame.

And it's little slow...

Is there some other solution for that as I can't reformat drive to NTFS or other instead FAT32?

Thanks

---

### Post by moribashi on 2012-07-27
You could use Deja-dup which comes with Ubuntu. You also can restore one file: [https://live.gnome.org/DejaDup/Help/Restore/Revert](https://live.gnome.org/DejaDup/Help/Restore/Revert)

---

### Post by eslavko on 2012-07-27
> **moribashi said:**
> You could use Deja-dup which comes with Ubuntu. You also can restore one file: [https://live.gnome.org/DejaDup/Help/Restore/Revert](https://live.gnome.org/DejaDup/Help/Restore/Revert)

That's near perfect.
Just one thing is missing.
When selecting backup date there are all dates (all backups). Is there some workaround to have just dates when file is changed?

It's hard to find file if backup is done daily but the file is changed few months ago. BackInTime has nice solution to show diff too. 

There is probably way to skip 'same file' dates. (I can't tell but assume that solving FAT32 on BackInTime is harder to implement)

---

### Post by moribashi on 2012-07-27
If you are using deja-dup and want to restore previous version of the file you can use nautilus. Navigate to the folder where the file is and right click on it - select "Revert to previous version".

---

### Post by eslavko on 2012-07-27
> **moribashi said:**
> If you are using deja-dup and want to restore previous version of the file you can use nautilus. Navigate to the folder where the file is and right click on it - select "Revert to previous version".

I know that from few post ago. Just It's hard to find right archive date.
Is it possible to got list when file was changed? (I'm sure that is possible but the question is how to check that)

---

### Post by neomatrix7 on 2012-07-27
my question is ..... why I cant install last version of opera for ubuntu??? they stopped to support it or what???... chrome and firefox works well...but I still love opera...

---

### Post by Elfy on 2012-07-27
> **neomatrix7 said:**
> my question is ..... why I cant install last version of opera for ubuntu??? they stopped to support it or what???... chrome and firefox works well...but I still love opera...

Please do not derail support threads with issues that are off-topic. If you have a question please start your own thread.

---

### Post by eslavko on 2012-07-28
Is it possible to list all file changes in the backups made with deja-dup?

some command line?

If I understand correct then deja-dup made archive with only changed files. So is there some way to simple list specific file in archives?

---

### Post by eslavko on 2012-07-31
> **eslavko said:**
> Is it possible to list all file changes in the backups made with deja-dup?

some command line?

If I understand correct then deja-dup made archive with only changed files. So is there some way to simple list specific file in archives?

Nobody known or not possible?

---


---
title: "What are your Grsync Settings? Also, an oddity with Grsync?"
date: 2010-02-14
forum: General Help
---

### Post by Rytron on 2010-02-14
Hi.
I use Grsync between my Desktop and Laptop. My settings are as follows:
**Basic Options Tab**:
Preserve Time
Delete on Destination
Verbose
Show Transfer Progress
**Advanced Options Tab**:
Copy symlinks as symlinks

I noticed only yesterday that a particular .ods file that I though was being synchronised with my Desktop was a version from at least a few weeks ago. This is very odd because I update that .ods file almost on a daily basis. Also I use Grsync once a week to sync all my Desktop data to my laptop. Does anyone know why that particular file was ignored? Was it something to do with the 'Preserve Time' setting?

---

### Post by pbrane on 2010-02-14
I don't think it's your settings. I use rsync but I have the '-t' option which just preserves modification times. It should still transfer the file. Do you have and excludes? I don't transfer all files, I exclude certain file types and directories.

It's only that one file? Not sure why that one file would not be transfered. Maybe check permissions? Any output from grsync that may have some clues?

---

### Post by Rytron on 2010-02-15
> **pbrane said:**
> I don't think it's your settings. I use rsync but I have the '-t' option which just preserves modification times. It should still transfer the file. Do you have and excludes? I don't transfer all files, I exclude certain file types and directories.

It's only that one file? Not sure why that one file would not be transfered. Maybe check permissions? Any output from grsync that may have some clues?

Hi pbrane. I also noticed another file was not even synced (a .txt file). I do use an exclude list but this list does not have the suspect files on it.

Would you think there is a need to check 'Preserve permissions' & 'Always checksum'?

Ah ha! I have heeded to your advice on checking permissions. The .ods in question has read and write for me but only has read for 'others' and 'group'. I'm not sure if that matters! The .txt file in question has read and write access for me and none for 'others' and 'group'. Why would these two files have different file permissions?

---

### Post by Rytron on 2010-02-15
There are approximately 20 files in all that are not being synced. What is the best way to solve this?

Update:
I played around with permissions. I don't think the permissions had anything to do with this!

I have an exclude list. To my surprise I noticed that I had a folder titled
[COLOR="Orange"]Movies-TV[/COLOR] in the home directory and this was being treated the same as the [COLOR="Navy"]Documents/Movies-TV[/COLOR] folder. Therefore the [COLOR="Navy"]Documents/Movies-TV[/COLOR] folder was being excluded even though I did not want it excluded.

In the exclude list I have:
```
[COLOR="Orange"]Movies-TV[/COLOR]
```

I did not put it as [COLOR="Orange"]~/Movies-TV[/COLOR] as that did not get ignored. I also tried [COLOR="Orange"]/home/rytron/Movies-TV[/COLOR] but that too was not ignored.

What is the best way to list the exclude files? The main one I want to exclude is [COLOR="Orange"]/home/rytron/Movies-TV[/COLOR]

---

### Post by Rytron on 2010-02-15
How do i exclude only a specific folder? i.e. [COLOR="Purple"]/home/rytron/Movies-TV[/COLOR]

---


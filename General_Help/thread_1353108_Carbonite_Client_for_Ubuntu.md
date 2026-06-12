---
title: "Carbonite Client for Ubuntu?"
date: 2009-12-12
forum: General Help
---

### Post by vinay427 on 2009-12-12
Hi,

I was asked to help set up a server for a small business which uses Carbonite for their online backup.  Is there a Carbonite client for Ubuntu because I can't find any.  It doesn't need to be official.

Thanks,
vinay427

---

### Post by mac9416 on 2009-12-12
Hey vinay427,

According to the Carbonite website, "Carbonite will not support older versions of Windows (Windows 98, Windows 2000, and Windows ME) or **Linux operating systems**."

By "will not support," I am not sure if they mean "will not work on" or "will never work on." I would suggest you contact them and encourage them to support Linux.

Sorry that the news is not good.

---

### Post by vinay427 on 2009-12-12
> **mac9416 said:**
> Hey vinay427,

According to the Carbonite website, "Carbonite will not support older versions of Windows (Windows 98, Windows 2000, and Windows ME) or **Linux operating systems**."

By "will not support," I am not sure if they mean "will not work on" or "will never work on." I would suggest you contact them and encourage them to support Linux.

Sorry that the news is not good.

Ok, thanks a lot anyway!

---

### Post by cilbuper on 2010-02-10
Why don't you look into using Rsync?  I spent 5 mins researching it and found that it is EXTREMELY simple to backup the folders which I needed.  It will even work with Windows (I installed Cygwin which is a Linux like system that runs within Windows, similar to a virtual machine)

Do some research into rsync.  I run it over SSH into my web server/webhost.  It only uploads files files that have been updated, created or modified.  

If you have a web hosting plan, you can easily make rsync work for you at no extra charge!

Here is a short command which lets me upload from my windows machine (using cygwin) to my server:
```
rsync -azvv -e ssh /cygdrive/b/ username@RemoteDomain:/home/
```
It will then prompt you for your password for your remote server and it will do it's thing.

---

### Post by gunfyter on 2010-06-12
[wubi]                          [Carbonite backup WUBI DUAL BOOT c]("http://ubuntuforums.org/showthread.php?t=1503172&highlight=carbonite")                                                                                     

You might find this thread interesting....

But possibly not what you are looking for....

---

### Post by abexman on 2011-06-03
I realize Carbonite does still not support Linux. I'd like a service that automatically backs up all my files and settings, like Carbonite (I know it has some limits, like files 2gb+ and certain filetypes, but I am speaking generally) to an external server that is hopefully some level of secure. I like that Carbonite works in the background during idle cycles. I quickly looked at Spideroak and Ubuntu One but I fear they will require some level of setup and maintenance that I just don't care to do. Is there no option still?

---

### Post by bpb_21 on 2011-09-03
> **abexman said:**
> I realize Carbonite does still not support Linux. I'd like a service that automatically backs up all my files and settings, like Carbonite (I know it has some limits, like files 2gb+ and certain filetypes, but I am speaking generally) to an external server that is hopefully some level of secure. I like that Carbonite works in the background during idle cycles. I quickly looked at Spideroak and Ubuntu One but I fear they will require some level of setup and maintenance that I just don't care to do. Is there no option still?

I've had really good luck with Ubuntu One, especially being able to access documents and such from my mobile devices.  I haven't had to do any maintenance, per se.  I also like Dropbox, but I favor Ubuntu One because you can select any file/folder to be backed up and not just ones in the designated application folder.

---

### Post by bpb_21 on 2011-09-03
> **cilbuper said:**
> Why don't you look into using Rsync?  I spent 5 mins researching it and found that it is EXTREMELY simple to backup the folders which I needed...
Do some research into rsync.  I run it over SSH into my web server/webhost.  It only uploads files files that have been updated, created or modified...

Here is a short command which lets me upload from my windows machine (using cygwin) to my server:
```
rsync -azvv -e ssh /cygdrive/b/ username@RemoteDomain:/home/
```
It will then prompt you for your password for your remote server and it will do it's thing.

I've also got a server, just for backup, that I connect to using SSH but I've been using Deja Dup for my backups.  I'd really like a backup mechanism (like Carbonite) that makes individual files accessible from other devices (the other devices I'd be accessing it from are limited by SSH, so that's not an issue).

Does the Ubuntu app "Back In Time" support rsync?  I seem to remember reading that it does, but I don't know how to use SSH via Back in Time to connect to a remote server.  Back in Time only seems to look for local folders.  Is it just something I'm missing in the documentation somewhere?

---

### Post by DaveQB on 2012-02-13
> **abexman said:**
> I realize Carbonite does still not support Linux. I'd like a service that automatically backs up all my files and settings, like Carbonite (I know it has some limits, like files 2gb+ and certain filetypes, but I am speaking generally) to an external server that is hopefully some level of secure. I like that Carbonite works in the background during idle cycles. I quickly looked at Spideroak and Ubuntu One but I fear they will require some level of setup and maintenance that I just don't care to do. Is there no option still?

I don't think you'll find anything more simple than SpiderOak. Set & forget.

---


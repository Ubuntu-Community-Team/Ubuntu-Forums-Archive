---
title: "Can't access windows partition anymore after upgrading to 10.10."
date: 2010-12-08
forum: General Help
---

### Post by gdpt on 2010-12-08
Dear Ubuntu people,

first post here, I searched for similar issues on this forum, but no luck, so here it goes:

I had my Windows partition mount automatically on my 10.04, and I set it up following [this]("http://www.wikihow.com/Access-Windows-Files-in-Ubuntu") great tutorial.

After the update, it didn't work anymore, and when I tried the command to mount, terminal gave me the following message

```
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.
```

Now, it is important to say that there was a message when starting Ubuntu saying there was an unclean shutdown of Windows 7 (not the exact words, but something along those lines. 

Even after doing a complete disk check, that took about an hour, when I tried to mount the drive, I still got the same error message. 

I have no idea what could have the drive mounted, I don't think I have any software using it at the moment. What are your thoughts on this?
Thanks in advance.

---

### Post by argedion on 2010-12-08
Restart the Computer and choose Windows from the grub menu. Allow Windows to boot up and then log on. Choose to shut down the machine and let it shutdown on its own. Push the power and allow it to reboot to the grub menu then select ubuntu and see if you can access the drive after logging in

---

### Post by gdpt on 2010-12-08
I have tried it, but still, no luck :(

---

### Post by argedion on 2010-12-08
Try using the Ubuntu install CD and just boot into live mode and see if you can access the drive. If you can then I would go and delete the script file and then retry to access the Windows drive from your Ubuntu. You may also want to boot into windows and do a chkdsk and make sure there is nothing wrong with the disk. I fear however that your script may be the culprit

---

### Post by gdpt on 2010-12-09
thanks for the reply, but could you give me some more information on how to do that (i'm quite a noob). Does it work if I boot into linux recovery mode? I do have two mountwinfs files in etc/init.d (one is called mountwinfs and the other one mountwinfs.sh, they are identical in content, and I created them, but apparently I don't have the permissions to delete them?)

---


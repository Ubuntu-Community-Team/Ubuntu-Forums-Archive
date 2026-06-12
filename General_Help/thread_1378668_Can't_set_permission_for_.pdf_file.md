---
title: "Can't set permission for .pdf file"
date: 2010-01-11
forum: General Help
---

### Post by Lakeside on 2010-01-11
I am having a LOT of trouble trying to set permissions for a .pdf file I downloaded.  Our teachers are putting a lot of our lessons on .pdf's that they post to our 'mailbox' and I want to embed them into my site, so I can read them when I want to. But first they need to be moved from where they downloaded to, which is usually my desktop to the right folder.  I have tried using the terminal... sudo chown (my user name)  file.pdf   I tried sudo chmod 777 file.pdf  (making sure I am in the directory it's in)  and it will still not let me move it using copy and paste.  I could try the terminal command for move (what is it again? lol)  but if the permissions are not set I can not upload it to my site backend anyway.  thanks for any help

---

### Post by scouser73 on 2010-01-11
> **Lakeside said:**
> I am having a LOT of trouble trying to set permissions for a .pdf file I downloaded.  Our teachers are putting a lot of our lessons on .pdf's that they post to our 'mailbox' and I want to embed them into my site, so I can read them when I want to. But first they need to be moved from where they downloaded to, which is usually my desktop to the right folder.  I have tried using the terminal... sudo chown (my user name)  file.pdf   I tried sudo chmod 777 file.pdf  (making sure I am in the directory it's in)  and it will still not let me move it using copy and paste.  I could try the terminal command for move (what is it again? lol)  but if the permissions are not set I can not upload it to my site backend anyway.  thanks for any help

*This is the long way of doing it*

**1** - Go to **Terminal**, copy & paste this command: **gksudo nautilus** that will open Terminal as root

**2** - Navigate to your  folder/file/drive, **Right Click**, select the **Permissions** tab 

**3** - Change the **Owner** drop-down menu to your name, then change **Folder Access** to **Create & Delete Files**, then **File Access** to **Read & Write**, then **Group** to your name, **Folder Access** to **Create & Delete Files**, **File Access** to **Read & Write** then click **Apply Permissions To Enclosed Files**.


You will now have full access to your folder/file/drive.

This is the short version.

Enter these commands in Terminal

**1** - > sudo -i

**2** - [COLOR="Red"]**Example:**[/COLOR] cd /home
> cd

**3** - > chown -R username filename

[COLOR="Red"]**Username is you and filename for the file**[/COLOR].

---

### Post by Lakeside on 2010-01-11
Thanks for the detailed help :) this is what I got when I did the first thing:  ** (nautilus:10188): WARNING **: Unable to add monitor: Operation not supported
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS

---

### Post by michy99 on 2010-01-11
It is probably not the permissions of the file that is the problem, but the permissions of the folder that you are trying to move it to. If you open nautilus as root```
gksudo nautilus
```you can put it wherever you want. Before you change permissions on any folders, make sure you know what you are doing. They are usually set a certain way for a reason.

---

### Post by gabo.cr on 2010-01-11
Can you go back to the location of those files using Terminal and then post the results of this command?

```
ls -l
```

---

### Post by gabo.cr on 2010-01-11
> It is probably not the permissions of the file that is the problem, but the permissions of the folder that you are trying to move it to.

That too.
:D

---

### Post by Lakeside on 2010-01-11
Thanks everyone :) For now I tried the 'sudo -i' and will see if it worked, but first I would like to set it back to how it was before, where I had to use sudo username to act as root.  thanks.
Never mind, silly me, I discovered that when I closed the terminal and re-opened it,  I was back to the user@ubuntu prompt, so I will have to type user and sudo to be root, just like before ;)  AND  yayyy,  that worked perfectly,  I could move the file no problem, you guys have saved me a lot of headaches, BIG thanks.

---


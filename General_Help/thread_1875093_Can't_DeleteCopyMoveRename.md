---
title: "Can't Delete/Copy/Move/Rename"
date: 2011-11-04
forum: General Help
---

### Post by al prince nofl on 2011-11-04
Hi all,

I can't make any edit/don't have permission to do do anything (edit/copy/rename/past/create folder) on any of the laptop drives.

I think this problem happened after upgrading to Ubuntu 11.10.

Any suggestions ?

Thanks

---

### Post by sunk_u on 2011-11-04
Can you read the files?

Try
```

ls -all

```
and check the permissions if you have write access. If not use

```

chmod +w <files for which you want write access>

```

Add sudo if necessary..

---

### Post by al prince nofl on 2011-11-04
> **sunk_u said:**
> Can you read the files?

Try
```

ls -all

```and check the permissions if you have write access. If not use

```

chmod +w <files for which you want write access>

```Add sudo if necessary..

I can see the only folder which is in the drive but i don't have permissions, the current permissions is root (not owned by my current user), and my current user is Administrator. also the file properties says the contents unreadable.

[IMG]http://oi44.tinypic.com/24zfzb7.jpg[/IMG]
Thanks.

---

### Post by al prince nofl on 2011-11-05
Any new ?
I still don't have permission to make any edit on the HDD :/

---

### Post by critin on 2011-11-05
Try right clicking on the folder and choose 'Open as Administrator'.  It will ask for your password.

---

### Post by al prince nofl on 2011-11-05
> **critin said:**
> Try right clicking on the folder and choose 'Open as Administrator'.  It will ask for your password.

Sorry, there isn't this option in the right click menu. I am using Ubuntu not Windows 7 :/.

Thanks.

---

### Post by critin on 2011-11-06
Now I wonder what I did, I can't do it again.  lol
I swear I opened my 11.10 and went to 'lost and found.  It was locked and looked the same as your pic.  I right clicked, and it had the option to run as admin.  I chose it and was able to get in and go to all drives.  I did it, that's why I posted here.

Now the option isn't there.  I have no Windows on this machine so that isn't relevant.  A mystery that will haunt me until I figure it out.

---

### Post by al prince nofl on 2011-11-06
@critin, it's ok but still can't open any drive till now :D

---

### Post by critin on 2011-11-06
I can get into my 5 drives though, just not 'Lost and Found' and 'Root' folders--the locked ones.   BUT I DID YESTERDAY WHEN I TESTED IT BEFORE I POSTED HERE.  I  promise I did.  :o

   I **can** get into all the rest of the folders and edit.  I didn't set anything especially, just left everything at default.  Sorry I can't help you sort it out.  You 'should' be able to open and edit.

---

### Post by critin on 2011-11-06
> I can see the only folder which is in the drive

The only folder on that drive?  Isn't that odd?  That's probably the problem.  What about the other drives?  Do they have more folders?  There should be many more.  This particular one had 24.

/media/bin
/media/boot
/cdrom
/dev
/etc
/home

---

### Post by al prince nofl on 2011-11-07
I don't mean that i can't access the "Lost and Found" and the other root folders. I mean that i can't access ANY folder !!
I have 4 drives on my laptop's hard and i can't edit any of them ! can't create folder or edit anything in them. and there isn't any folders in them (just "Lost and Found" folder).
I was able to do before upgrading to Ubuntu 11.04. I think my system got some weird problems after the upgrade. I got errors while upgrading but i saw everything working fine so i thought everything is ok. from the things which happened after i upgraded my Ubuntu that there isn't screen saver and there isn't auto lock! also i can't find the folder emblems! and can't play any video on "Movie Player".
Btw: the third-party has been disabled while upgrading Ubuntu, would it be the problem in it ? if so how can i enable it back ?

Thanks.

---

### Post by dino99 on 2011-11-07
is your installation a standard one ?

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

might be better/easier/faster to do a clean install again

---

### Post by critin on 2011-11-07
Yes, I understood you couldn't access any folders, but you said 'lost and found' was the only folder in this specific drive.  There should be more..

I agree with dino99, it may be easier to install a new image.  Upgrading has been difficult for many users.
Since you ran the code suggested in post 2, and nothing helped--reinstalling may be the easiest answer.  It seems something went wrong with the upgrade.

---

### Post by al prince nofl on 2011-11-08
Ummm... Not the solution which i waited. I don't like manual install new version :/
It's ok, I will try install new image version soon.

Thanks all.

---


---
title: "Folder access from one user to another - permissions?"
date: 2010-01-27
forum: General Help
---

### Post by argued.logic on 2010-01-27
*I have searched every forum post relevant to this subject and read every manual I could find about chmod / chown commands and still...*

The problem is that I have a folder containing sub-folders / files under **/home** in **user1**
and I want **user2** to have complete access to that folder. Is it even possible?

What I have done is created a new group called "multimedia" and added both users to the group followed by changing permissions in the folder to 770, removing world access.
As an example the **ls -l** gives me *drwxrwx---  84 user1 multimedia 12288 2009-10-30 13:48*. So far all good I thought but once in **user2** account I cant access the folder at all.

If I am on the wrong track please correct me and show me another way to do this.

Thank you in advance!

---

### Post by warfacegod on 2010-01-27
> **argued.logic said:**
> *I have searched every forum post relevant to this subject and read every manual I could find about chmod / chown commands and still...*

The problem is that I have a folder containing sub-folders / files under **/home** in **user1**
and I want **user2** to have complete access to that folder. Is it even possible?

What I have done is created a new group called "multimedia" and added both users to the group followed by changing permissions in the folder to 770, removing world access.
As an example the **ls -l** gives me *drwxrwx---  84 user1 multimedia 12288 2009-10-30 13:48*. So far all good I thought but once in **user2** account I cant access the folder at all.

If I am on the wrong track please correct me and show me another way to do this.

Thank you in advance!

Shot in the dark here but you may want to try using the chown command to change the folder usergroup to multimedia.

---

### Post by SlugSlug on 2010-01-27
> **argued.logic said:**
> *I have searched every forum post relevant to this subject and read every manual I could find about chmod / chown commands and still...*

The problem is that I have a folder containing sub-folders / files under **/home** in **user1**
and I want **user2** to have complete access to that folder. Is it even possible?

What I have done is created a new group called "multimedia" and added both users to the group followed by changing permissions in the folder to 770, removing world access.
As an example the **ls -l** gives me *drwxrwx---  84 user1 multimedia 12288 2009-10-30 13:48*. So far all good I thought but once in **user2** account I cant access the folder at all.

If I am on the wrong track please correct me and show me another way to do this.

Thank you in advance!

its not ideal to use the users home dir tho your best of having something like

/home/shared/pictures
/home/shared/music

etc


```
sudo setfacl -R -d -m g:multimedia:rwx /home/user1
```also check the users / groups 

```
groups user2
```

---

### Post by warfacegod on 2010-01-27
Not that mine isn't, but you've got a creepy Avatar. In a "that's not right" sort of way.

---

### Post by argued.logic on 2010-01-27
> **SlugSlug said:**
> its not ideal to use the users home dir tho your best of having something like

/home/shared/pictures
/home/shared/music

etc


```
sudo setfacl -R -d -m g:multimedia:rwx /home/user1
```also check the users / groups 

```
groups user2
```

I see it now, I had the choice of creating new partition or store the files in /home
and all advice I got is to store it under /home from everyone I talked to before
this installation. Thank you for your answer, I will try that one as soon as I am 
clear of what that command will do. Would you mind explaining that to me?

"sudo setfacl -R -d -m g:multimedia:rwx /home/user1"

Groups user2: user2 adm cdrom audio plugdev fuse admin sambashare multimedia
Groups user1: user1 adm dialout cdrom plugdev lpadmin admin sambashare multimedia

---

### Post by warfacegod on 2010-01-27
In the Terminal, type man in front of each part of the code. Example:

man -R or man -d

---

### Post by argued.logic on 2010-01-27
Don't take this the wrong way wartacegod but your replies doesn't help me at all.
I know how to search for information and use man pages as well. What I am 
asking for is the "result" of running that command so I can prepare for eventual
problems if something goes wrong. That is how I work. So if you dont have anything
concrete to add to this post or actually an proposition of your own I ll just wait for
someone who does.

SlugSlug: btw - did you point the command to whole /home or only the folder affected
               in this case?

---

### Post by t4thfavor on 2010-01-27
I believe it's going to set the gROUP to mULTIMEDIA for the folder /home/user1 and it's going to do it recursively which means the whole structure.

As for the -d -m im not quite sure, What I am sure of is you can look into man for the details, as you already stated you knew how to do it.


Don't bite the hand that feeds, if nothing more he was keeping your post on the first page. You will get crappy replies now and then, we all do.

Not that WarFace's post was crappy, he simply assumed that you were a nub and didn't know how to use the tools, which is a valid assumption.

---

### Post by warfacegod on 2010-01-27
Thanks t4thfavor for the favor of the vote of confidence.

> ]I believe it's going to set the gROUP to mULTIMEDIA for the folder /home/user1 and it's going to do it recursively which means the whole structure.

Wouldn't using "chown" to change usergroup, as I suggested above, accomplish the same thing?

---

### Post by argued.logic on 2010-01-27
> **t4thfavor said:**
> 
Don't bite the hand that feeds, if nothing more he was keeping your post on the first page. You will get crappy replies now and then, we all do.


 Thank you, honestly I didn't think of that and keeping the post I am trying to solve alive
and in-front is something I am grateful for.

---

### Post by argued.logic on 2010-01-27
> **warfacegod said:**
> Thanks t4thfavor for the favor of the vote of confidence.



Wouldn't using "chown" to change usergroup, as I suggested above, accomplish the same thing?

Correct me if I am wrong but "[I]drwxrwx---  84 user1 multimedia 12288 2009-10-30 13:48"
[/I]shows that the usergroup is in place.Or did I misunderstood something.

---

### Post by warfacegod on 2010-01-27
> **argued.logic said:**
> Correct me if I am wrong but "[I]drwxrwx---  84 user1 multimedia 12288 2009-10-30 13:48"
[/I]shows that the usergroup is in place.Or did I misunderstood something.

Check the Permissions tab in the Properties windows of the appropriate folder. As a matter of fact, if I recall, you can *change* usergroup from there as well.

---

### Post by argued.logic on 2010-01-27
Of course you can but I prefer the command line at all times and once again, the group is correctly in place and the owner is my username. Both owner and group have "Create and Delete Files" rights.

---

### Post by SlugSlug on 2010-01-27
> **argued.logic said:**
> I see it now, I had the choice of creating new partition or store the files in /home
and all advice I got is to store it under /home from everyone I talked to before
this installation. Thank you for your answer, I will try that one as soon as I am 
clear of what that command will do. Would you mind explaining that to me?

"sudo setfacl -R -d -m g:multimedia:rwx /home/user1"

Groups user2: user2 adm cdrom audio plugdev fuse admin sambashare multimedia
Groups user1: user1 adm dialout cdrom plugdev lpadmin admin sambashare multimedia


sorry for delay 

setfacl allows for you to add additional acl's to folders / files

you can see current acl's by using the getfacl command IE

```
getfacl /home/shared/
```

lets break this command down
"sudo setfacl -R -d -m g:multimedia:rwx /home/user1"
setting the acl; -Recursive -default -modify  (modifying the default acl's recursively) group:multimedia:read:write:execute  /path/to/share  that needs editing.

---

### Post by warfacegod on 2010-01-27
> **argued.logic said:**
> Of course you can but I prefer the command line at all times and once again, the group is correctly in place and the owner is my username. Both owner and group have "Create and Delete Files" rights.

You hadn't specifically stated that the folders usergroup was set properly. You were asking if it was. I gave you a point blank way to find out.

---

### Post by SlugSlug on 2010-01-27
> **argued.logic said:**
> Of course you can but I prefer the command line at all times and once again, the group is correctly in place and the owner is my username. Both owner and group have "Create and Delete Files" rights.


my guess is you did not use -R

```
sudo chgrp -R multimedia /home/share
```

but like I mentioned before - I think your better using setacl

---

### Post by argued.logic on 2010-01-30
Thank you for your time and all explanations *SlugSlug*, I got it all working thanks to 
your advice about using /home/shared instead of my personal account.
I did some reading on **setacl** these past few days and I believe it is a powerful command
(needed to install **acl** tho since it wasn't in karmic by default) but even tho I followed
all instructions I couldn't get past the error message "Operation denied" but hey, since
the group attribute worked I now have complete access to all these files from both 
accounts. It is time for marking this thread Solved so once again, Thank you!

---

### Post by warfacegod on 2010-01-30
> **SlugSlug said:**
> my guess is you did not use -R

```
sudo chgrp -R multimedia /home/share
```

but like I mentioned before - I think your better using setacl

Correct me if I'm wrong but isn't this almost exactly what I suggested in the first place?

---

### Post by SlugSlug on 2010-01-31
> **argued.logic said:**
> Thank you for your time and all explanations *SlugSlug*, I got it all working thanks to 
your advice about using /home/shared instead of my personal account.
I did some reading on **setacl** these past few days and I believe it is a powerful command
(needed to install **acl** tho since it wasn't in karmic by default) but even tho I followed
all instructions I couldn't get past the error message "Operation denied" but hey, since
the group attribute worked I now have complete access to all these files from both 
accounts. It is time for marking this thread Solved so once again, Thank you!


ahh I remeber karmic, you also need to edit your /ect/fstab to enable acl on the drive

(Backup)
```
sudo cp /etc/fstab /etc/fstab.bak
```tweak
```
gksudo gedit /etc/fstab
```
UUID=e182f101-b5ed-411b-87c0-3cfd5de6d4b2 /home           ext4    relatime,acl        0       2

see that reatime,acl -- -- you need to add the acl bit to any drive that needs acl settings..

and then either unmount and remount the drives -- or just reboot

---

### Post by hawthornso23 on 2010-01-31
This is all getting too complicated for my taste. 

Surely you shouldn't be having to advise someone to install a powerful admin type tool and edit the fstab just to let another user access a few files. Isn't that what groups and permissions are for.

---

### Post by SlugSlug on 2010-01-31
> **hawthornso23 said:**
> This is all getting too complicated for my taste. 

Surely you shouldn't be having to advise someone to install a powerful admin type tool and edit the fstab just to let another user access a few files. Isn't that what groups and permissions are for.


Well IMO thats the corrrect way to set shares up -- whats wrong with users learning that ?

---

### Post by hawthornso23 on 2010-01-31
> **SlugSlug said:**
> Well IMO thats the corrrect way to set shares up -- whats wrong with users learning that ?

Well ... nothing I guess. It just seems a bit excessive for sharing files between two users.

---


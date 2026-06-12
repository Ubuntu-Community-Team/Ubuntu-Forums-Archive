---
title: "No privileged access to folders"
date: 2010-01-19
forum: General Help
---

### Post by malangbaba on 2010-01-19
Is there a reason I dont have privileged access to any of my folders, in /home, or anywhere else?

Running Ubuntu Karmic and Win 7, with a separate partition to share files between both OS.  It was working fine, until I installed Kubuntu on a separate partition, and now Ubuntu acts funny (i can browse anywhere, but cant create new folders, download files, execute files, etc. The problem exists in any and all folders (/ and /home)

I can do so if I access nautilus as root...

I now reinstalled ubuntu, and still the same problem...

thoughts?

---

### Post by tom4everitt on 2010-01-19
Its perfectly normal that you can't do changes to / for example if you're not root. 

About your home folder I think you can fix this by running:

sudo chown -R youruser /home/<name-of-homefolder>

---

### Post by tom4everitt on 2010-01-19
The long explanation is that your previous user had a different user id (you can see your user id with the command id). When you install ubuntu again it will create a new user (with some id) and a home folder for that user and a home folder with the same name. But it will not touch your previous homefolders (so you should be able to reinstall the system without loosing personal data).

Now if there already exists a folder with the name of the user, belonging to someone with another id (that this user does no longer exists doesn't matter) it will just let that be the your home folder but you will not own it. I guess you could call this a bug :) (I'm not sure this is what happened, but it sounds reasonable.)

---

### Post by malangbaba on 2010-01-19
> **tom4everitt said:**
> Its perfectly normal that you can't do changes to / for example if you're not root. 

About your home folder I think you can fix this by running:

sudo chown -R youruser /home/<name-of-homefolder>

hmm, i could have sworn i could make changes to / without being root, but anyway, that is not so important...

i tried the command you listed it gave me:
chown: cannot/access '/home/myusername/.gvfs': Permission denied

And the problem still continued, but then i went to home/myuseragin and noticed the lock symbol on my folders..highlighted and went to permissions, and set to read/write

now it is working.

thanks!

thoughts on what the above error is for? (which still persists if i try that command again)

---

### Post by tom4everitt on 2010-01-19
Oh, I guess the chown (change owner) command runs into trouble with some special file (perhaps its a link or had no access even for root). 

But it seems like you actually was the owner of your home folder (otherwise you couldn't just have given yourself permissions i think) so either the chown command worked on all normal files, or you were the owner all the time. 

If you want to check this you can run 

ls -al .gvfs

and see whether you are the owner of .gvfs. If you're not i would actually recommend you to:

sudo mv /home/youruser /home/youruser-backup
sudo mkdir /home/youruser
sudo chown youruser:youruser /home/youruser

to make yourself a fresh home folder with the right owner and permissions. Otherwise you run the risk of getting some weird errors later because you're not the owner of .gvfs. 


Glad you got it working though :)

---


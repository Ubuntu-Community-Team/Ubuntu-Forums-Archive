---
title: "Simple backup and SSH"
date: 2009-12-10
forum: General Help
---

### Post by Curbuntu on 2009-12-10
I have a question about how Sbackup (Simple Backup Config) relates to SSH and where files are stored and setting are “remembered.”  Here's my situation:


[LIST=1]
[*]I'm running a Fedora-10-based Amahi server.  (See [www.amahi.org]("http://www.amahi.org") for a project we hope the Ubuntu community will adopt as its own.   The developers are anxious to have an Ubuntu-based version of this feature-rich, FLOSS home server.)  Because it has built-in ssh capability (naturally), I was able to use Sbackup in ssh mode to backup both our Ubuntu laptops (9.04 and 9.10) and store the resulting tarballs on the server.  So far, so good.
[*]For reasons that don't relate to this story, I had to reinstall the Amahi server.  After that, Sbackup was “broken,” which is to say that I could no longer make Sbackup work in the same ssh mode.  (I could use Sbackup locally, and I could also ssh into the server from Terminal from each laptop; the latter proves that the server-username and server-passwords work.)
[*]The error message Sbackup gives each time is: **“The selected destination is not writtable [sic] with current permissions.  The backups can not [sic] be written there.”** (See attached screenshot.)  I have carefully checked the permissions on all the folders involved on both sides of the transaction.  I blamed changes in the server setup, but, as it turned out, the blame was misplaced, because...
[*]For other reasons, I did a fresh install (not an upgrade), changing the 9.04 laptop to 9.10. Sbackup worked again in ssh mode – but only on the “new” 9.10 laptop,  not the “old” one. This leads me to believe that somewhere on the “old” 9.10 laptop there's a config file or setting or key or *something* that “remembers” the connection to the original server installation, keeping it from connecting to the “new” server installation.  I'd guess it's something related to ssh, but I know very little about such matters.
[/LIST]
So the question is: **What and where is this SSH-Sbackup setting and how can I edit or delete it?**

 Any help clearing this up will be appreciated!

---

### Post by Curbuntu on 2009-12-20
Any ideas or suggestions?  It's a bit discouraging to have this unresolved...

---

### Post by Joeb454 on 2009-12-20
It looks like it's a permissions error on the remote computer - having never used Sbackup, I can't really say 100%

I'd check the permissions on the remote computer to see if it's writeable etc by the user you're using with ssh.

---

### Post by blueridgedog on 2009-12-20
What happens if you try it with a new user account (hence one without a prior connection to the server)?  It may be a simple matter of deleting the ~/.ssh directory.

---

### Post by Curbuntu on 2009-12-20
> **Joeb454 said:**
> It looks like it's a permissions error on the remote computer - having never used Sbackup, I can't really say 100%

I'd check the permissions on the remote computer to see if it's writeable etc by the user you're using with ssh.

Thanks for the reply!

To recap: The laptop with the "new" 9.10 installation *can *backup, but the laptop with the "old" 9.10 installation *cannot *backup.

Since I'm backing up as the same user from each laptop to the same folder (except the very last chain, i.e., @home/folder1/folder2/folder3/a and @home/folder1/folder2/folder3/b), I can't see that this might be the issue; but I did check the permissions on "a" and "b," to be sure.  Both "a" and "b" have the permissions drwxrwxr-x, are owned by my username and are part of the "users" group.

That's what makes me think that the problem has to be some file on the "old installation" laptop.

---

### Post by Curbuntu on 2009-12-20
> **blueridgedog said:**
> What happens if you try it with a new user account (hence one without a prior connection to the server)?  It may be a simple matter of deleting the ~/.ssh directory.

Thanks for replying!

Do you mean:

1) Setting up a new user on the problem laptop, and then...
2) Setting up the same user on the Amahi server, with corresponding backup folders...

and trying to backup that way?  If that's what you mean, I'll give it a try and report back.

---

### Post by Curbuntu on 2009-12-20
blueridgedog,

Based on your suggestion, I have tried several things:

1) Created brand new user on both client and server, carefully checking permissions on the server and setting up the client-user as administrator.  Result: no change.
2) Eliminated .ssh folder in client's home folder.  Result: no change.
3) Completely uninstalled sbackup from client.  Rebooted.  Reinstalled sbackup.  Result: no change.
4) Tried a combination of 2) and 3) above.  Result: no change.

One note on sbackup: If not uninstalled, it "remembers" the last ssh// setup that was saved, even if it was set up under another user's account.  (It requires administrator permission to open sbackup.)  This is probably so that every user's home directory can be backed up, which makes sense.

There's got be some other... key?... that's gumming up the works.  Any further input would be appreciated.

---

### Post by blueridgedog on 2009-12-20
One idea: Uninstall sbackup, then delete /etc/sbackup.conf (as root), then reinstall.  That is the only config file I can find that should store settings.

---

### Post by Curbuntu on 2009-12-20
blueridgedog,

After a complete sbackup uninstall, /etc/sbackup.conf doesn't seem to exist.  

After looking at the /etc/sbackup.conf file on the laptop that is sbackup'ing properly, I note that the last line says:

```
lock = /var/lock/sbackup.lock
```but I can't find that "lock" file on either machine.  Any idea what that is?

---

### Post by blueridgedog on 2009-12-21
> **Curbuntu said:**
> 

After looking at the /etc/sbackup.conf file on the laptop that is sbackup'ing properly, I note that the last line says:

```
lock = /var/lock/sbackup.lock
```but I can't find that "lock" file on either machine.  Any idea what that is?

That file will only exist when the program is in use.  

Have you tried to create the file and sftp it manually?  That may reveal more information.

---

### Post by Curbuntu on 2009-12-21
blueridgedog,

"SFTP"?  Secure FTP? (I'm just guessing.)  Theoretically I could do this with any file, assuming I can figure out from man sftp how to create the command.  Would I need to set up anything on the server side as well?

---

### Post by blueridgedog on 2009-12-21
I mentioned that as I assumed that was the backed of sbackup it it may reveal some other aspect of the error.

---

### Post by Curbuntu on 2009-12-21
> **blueridgedog said:**
> I mentioned that as I assumed that was the backed of sbackup it it may reveal some other aspect of the error.

Would you mind running that by me again?  Thanks.

---

### Post by tmkuster on 2010-03-16
Did anything ever come of this? I'm facing exactly the same problem, tried exactly the same steps, got no joy at all. Simple Backup  still says it can't write to my selected directory over ssh.
Any further info would be most appreciated.
By the way, I found this bug, which had been rejected as invalid, but which describes the situation perfectly. I asked them to reopen it. 
[https://bugs.launchpad.net/ubuntu/+source/sbackup/+bug/240988](https://bugs.launchpad.net/ubuntu/+source/sbackup/+bug/240988)
Ted

---

### Post by Curbuntu on 2010-03-16
Unfortunately, no.  But as it so happened, I decided to reinstall Ubuntu on the two laptops in question.  What files I couldn't find to change before the reinstallation apparently were overwritten, because when I tried Sbackup after the reinstalls, everything worked fine.  The two machines back up to the server hourly without issue.  But I'd still like to know how to fix this problem without a reinstall.

---

### Post by tmkuster on 2010-03-28
Hm... That's interesting because for this latest attempt I used a completely fresh install of 9.10, with no previous ssh activity on it.

---

### Post by dibuntux on 2010-06-22
OK guys, thank you all for your efforts, I solved it:

Re-install SimpleBackup will not do it - 

This was the trick:
mymachine:/root$ sudo rm .ssh/known_hosts

Then SimpleBackup, on testing ssh, will ask if you want to login anyway to the unknown key host - you say yes and it goes!

Hope it helps

---

### Post by ulysses768 on 2010-06-27
That worked for me.  I had the same issue.  Why does is this a problem for simple backup and not nautilus?

---


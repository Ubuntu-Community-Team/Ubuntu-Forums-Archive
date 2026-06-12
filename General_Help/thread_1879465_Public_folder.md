---
title: "Public folder"
date: 2011-11-11
forum: General Help
---

### Post by Lolpanda on 2011-11-11
Evening all, Kind of a unique question I'm posing today, hopefully someone can help me out.

So on the family's computer, in order to keep things fairly easy to backup, instead of doing "~/Shared" For every home directory. I was just going to do one folder in a neutral part of the FS, my thought was /media/Public 

And then off of that just do like

/media/Public/Music
/media/Public/Videos
/media/Public/Documents

This way it was just one samba and NFS share, and one local share for all users, that (ideally) anyone could read and write to, no problems. I ran into a few logic problems though, and hopefully you guys can help me work them out.

1) If people are just dragging and dropping files into /Media/Public/... won't they own the individual files? And if so, won't that make it so other users can't access the files that are supposed to be "shared." Or, is there a way that I can make it so when they drop the files into the folder, they become either 777, or whatever would be better to handle it.

2) Who should "own" /media/Public ?  I was thinking make the folder 777, but that still brings up the owner and group when I do ls -l, so should I make an extra account named Public, in the users group and chown -R /media/public? Or could I use the 'nobody' user and group?

3) (Any other problems you guy see with this scenario, or, any better way to do this that I'm just not thinking of?)

---

### Post by galvatron408 on 2011-11-11
This is what I would do.

1) sudo chmod 2775 /Media/Public (yes, whoever creates the file will own it but the permissions will be set to 664 aka rw by owner/group and read by all) make sure everyone is in the same group

2) owner = root and group = whatever group everyone is in (assuming everyone as in everyone who is supposed to have access)

> **Lolpanda said:**
> 
1) If people are just dragging and dropping files into /Media/Public/... won't they own the individual files? And if so, won't that make it so other users can't access the files that are supposed to be "shared." Or, is there a way that I can make it so when they drop the files into the folder, they become either 777, or whatever would be better to handle it.

2) Who should "own" /media/Public ?  I was thinking make the folder 777, but that still brings up the owner and group when I do ls -l, so should I make an extra account named Public, in the users group and chown -R /media/public? Or could I use the 'nobody' user and group?

3) (Any other problems you guy see with this scenario, or, any better way to do this that I'm just not thinking of?)

---

### Post by Lolpanda on 2011-11-12
THanks for the reply Galvatron! The 'sticky' bit Im not worried about, because I would want them to be able to delete their own files and we're mature enough not to screw with eachother's files.

Do you see any easier way of doing this? Because I was kind of hitting a roadblock with this.

---

### Post by galvatron408 on 2011-11-13
What makes you think that they can't delete their own files? Perhaps you didn't set it up correctly.

If you set it up right, it would look like this.

/Media/Public (owner=root, group=mygroup, permission 2775)

user = jsmith and group = mygroup
user = zsmith and group = mygroup

user jsmith executes "touch /Media/Public/testfile.txt"

/Media/Public/testfile.txt (owner=jsmith, group=mygroup, permission 664)

user jsmith can delete his own file

---

### Post by Cyclane on 2011-11-14
What galvatron mentioned isn't called a sticky bit but a SGID.
With a SGID a user executing a file get's the permissions of the group owner but also when creating a file in a folder with a SGID will assign it the same group owner.

With a sticky bit users can't delete each others _directories_.

The octal number for sticky bit is 1 and the octal number or SGID is 2. So what galvatron mentioned will work, he just called it by a wrong name


###EDIT
While on the subject, there is 1 last special permission an that is: SUID.
when a file has SUID assigned to it, a user executing it will get the permissions of the file owner.
the octal number for SUID is, you guessed it: 4

---

### Post by Derek Karpinski on 2011-11-14
There is a package called 'bindfs' that works perfectly for your situation.  Although it's broken now, it did work great.  Wish we could get the dev to fix it.  Google it.

Or mount your drive with the acl flag, and set up acl permissions.  If you used acl, and you have your /home on a separate partition, just mount your /home parttion with the acl flag, and create your shared directory as /home/public or something like that.  Package 'eiciel' provides a GUI for setting permissions.

There are a few threads on how to set up each.

---


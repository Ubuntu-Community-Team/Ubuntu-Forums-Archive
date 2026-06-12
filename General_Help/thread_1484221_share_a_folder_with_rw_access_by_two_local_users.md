---
title: "share a folder with r/w access by two local users"
date: 2010-05-15
forum: General Help
---

### Post by jbm222 on 2010-05-15
This seems like somewhat of a n00b question, but I'm kind of stumped and working on a half a dozen other things at the moment, so I thought I'd go ahead and ask it.

Is there a "correct" way to set up a shared folder between two local users using only EXT4 that will allow both users read & write access to everything in the folder?

Here's my scenario:  My wife and I use the same computer.  I want two separate user accounts (mine and hers), but I want ~/Music to point to the same location for both users so that I don't have to duplicate all of the files.

Too protect the innocent, I'll use Jack and Jill.

So say Jack downloads or rips an album: 
"/home/jack/Music/Radiohead/Ok Computer"

I want Jill to be able to able to create a folder:
"/home/jill/Music/Radiohead/Hail To The Theif"

I know the basics of symlinks so I can get /home/jack/Music and /home/jill/Music to point to the same place.  I also have Jack & Jill in the same group.

The problem I'm having with my test setup is when Jack creates "/home/jack/Radiohead", it is set up to where Jill can read, but not write.  So she can play songs from Ok Computer, but if she wants to download Kid A, she has to go in and manually change the permissions on Radiohead first.

Any suggestions on how to fix this?

Also, while I might set up multiple directories this way, what I DON'T want is for Jack to be able to modify /home/jill/otherdir where otherdir is just a regular directory set up with default permissions.

Oh, and as an added bonus, it would be nice to set up another account (i.e. a "guest") with limited permissions that can read, but not write/modify.

---

### Post by jbm222 on 2010-05-15
Sorry... guess I didn't search hard enough.  I looks like bindfs might do want I want.    please stand by.

---

### Post by nothingspecial on 2010-05-15
Create a new directory somewhere outside of home, perhaps the /media folder and call it Music.
```

sudo chown -R jack:jack_and_Jills_group /media/Music
```
```

chmod -R 774 /media/Music
```

That will let jack and jill do what ever they want in that folder, but let others (your guest account) only read the files.

Then simlink both of your ~/Music folders there.

---

### Post by BoneKracker on 2010-05-15
You don't need bindfs for this.  You just need to understand how to use UNIX file permissions (which are confusing at first).
[http://www.zzee.com/solutions/unix-permissions.shtml#setuid](http://www.zzee.com/solutions/unix-permissions.shtml#setuid)

I'm going to give this to you the way you'd do it in the command line, but you can set the permissions in Nautilus too, if you're more comfortable doing it that way.

1. Make sure the permissions on the music directory are 0770 (rwxrwx---) and not 0750 (rwxr-x---), which is what they probably are by default.```
chmod 0770 ~/music
```(The last digit can be a 4 if you want everybody to have read access -- that goes for what I'll type below as well.)

2. Make sure the music directory has the correct owner and group```
chown jack:users ~/music
```
(where "users" is whatever group you assigned both you and your wife to, and "music" is whatever you named the directory you want to share (I'm assuming it's in your home directory).


Slightly more advanced:```
mv ~/music /home
chown root:music /home/music
chmod 2770 /home/music
```
(or 2774)

**Explanation:**

(This assumes you have or will create a group "music", although you could do the same thing with "users" or whatever.)

This will put the shared directory in /home but outside either user's home directory (where it really should be).  It will be owned by root (which is really should be).  This will set the permissions to rwxrws---

In plain language:

_Owner:_
Can read in the directory
Can write in the directory
Can enter the directory

_Group members:_
Can read in the directory
Can write in the directory
Can enter the directory

_Others:_
Can't do squat (if you want everybody to be able to read, just make the last digit a 4 in all cases).

The 2 at the beginning makes the directory SGID (Set Group ID).  That means any files in the directory automatically will inherit the group of the folder, as opposed to the group of the user putting the file there.

That way, you and your wife can have different primary groups.  You just both need to be MEMBERS of the group you assign the music folder to (group "music" in my example).

For example, you might be user "jack" with primary group "jack" (or primary group "users"), and she might be user "jill" with primary group "jill" (or primary group "users"), but you make /home/music owned by "root" with group "music", and then just add both jack and jill to group "music".

Then you just create a symlink to the music directory in both /home/jack and /home/jill (which you already know how to do).

In this way, only users in group "music" can mess with the music, and every file that gets in there will automatically belong to group music.

If it were useful, you can go a step further and make it so that only jack can delete music that jack has put there, and only jill can delete music she has put there (although both can modify the files to change song name, edit tags, etc.).  This is accomplished by setting the "sticky" bit.  That would be:```

chmod 3770 /home/music
```
(or 3774)

And it is represented as rwxrws--t

:)

Edit: and I would not recommend using the /media folder.  That is for media (CDs, DVDs, USB sticks, etc.) to be automounted in by udev.  Although it may look like it, it's not intended to be a place to store "media" files (i.e. music and video).  User data belong in /home.

---

### Post by jbm222 on 2010-05-16
I already got it working with bindfs, however, I suspect that adds some minimal performance overhead... 

Looks like this is the key to BoneKracker's method:

> The 2 at the beginning makes the directory SGID (Set Group ID). That means any files in the directory automatically will inherit the group of the folder, as opposed to the group of the user putting the file there.


I was missing the magic "2".   

One other observation:  it would appear that setting the "others" permission to 5 (r-x) instead of 4 (r--) opens up a potential security hole allowing anyone to execute files in the directory with the permission of the group.  Which is probably just further reason to create a separate group for doing this.

---

### Post by BoneKracker on 2010-05-16
> **jbm222 said:**
> I was missing the magic "2".   

One other observation:  it would appear that setting the "others" permission to 5 (r-x) instead of 4 (r--) opens up a potential security hole allowing anyone to execute files in the directory with the permission of the group.  Which is probably just further reason to create a separate group for doing this.

On the directory, an x just means that they can enter the directory, not that they can execute what's in the directory.  (I know; it's confusing.  I still have to refresh my understanding of permissions occasionally.)

```
r - Read permission. Whether the file may be read. In the case of a
directory, this would mean the ability to list the contents of the
directory.

w - Write permission. Whether the file may be written to or modified. For
a directory, this defines whether you can make any changes to the contents
of the directory. If write permission is not set then you will not be able
to delete, rename or create a file.

x - Execute permission. Whether the file may be executed. In the case of a
directory, this attribute decides whether you have permission to enter,
run a search through that directory or execute some program from that
directory.
```

Here is a good plain-language explanation of permissions (although this one doesn't seem to cover the sticky bit):
[http://www.freeos.com/articles/3127/](http://www.freeos.com/articles/3127/)

It's harder to find a useful explanation of the intial three bits (suid, sgid, sticky):
Most people can grasp "rwx,rwx,rwx = 777".  But that's actually "0777". There are three possible bits of information that can precede those:
3 = suid (set user identification attribute)
2 = sgid (set group identification attribute)
1 = sticky

For a file:
3 (suid) -> when anybody executes this file, it will be executed as though the owner were executing it
2 (sgid) -> when anybody executes this file, it will be executed as though a member of the group were executing it
1 (sticky) -> obsolete (used to mean "after file is executed, cache in ram", but this is automatic now)

For a directory:
3 (suid) -> n/a
2 (sgid) -> files in this directory automatically inherit the group assigned to the directory
1 (sticky) -> files in this directory may only be deleted by their owner (even if other have write access)

Another useful thing to know is that mount commands provide some ability to restrict what goes on.  Let's say you and your wife want to be able to execute programs in your home directories, but you intend to share this music directory with others, and you don't ever want anybody to be able to execute something in the music directory.

You could create a separate partition on your disk for your music files and mount that partition to /home/music. In your fstab file, on the line that controls how the system mounts that partition, you could include the option "noexec".  For example:```
/dev/sda8  /home/music  ext4  noexec  1  2
```

From 'man mount' we see that the "noexec" mount option means: "Do not allow direct execution of any binaries on the mounted filesystem."  (You can search man pages by pressing the "/" key.)

That way, users could execute programs in their home directories, but nothing could ever be executed in the /home/music directory (and you could more safely share it over cifs, nfs, ftp, webdav, or whatever).

---

### Post by kdford on 2012-07-15
> **BoneKracker said:**
> You don't need bindfs for this.  You just need to understand how to use UNIX file permissions (which are confusing at first).
[http://www.zzee.com/solutions/unix-permissions.shtml#setuid](http://www.zzee.com/solutions/unix-permissions.shtml#setuid)

I'm going to give this to you the way you'd do it in the command line, but you can set the permissions in Nautilus too, if you're more comfortable doing it that way.

1. Make sure the permissions on the music directory are 0770 (rwxrwx---) and not 0750 (rwxr-x---), which is what they probably are by default.```
chmod 0770 ~/music
```(The last digit can be a 4 if you want everybody to have read access -- that goes for what I'll type below as well.)

2. Make sure the music directory has the correct owner and group```
chown jack:users ~/music
```(where "users" is whatever group you assigned both you and your wife to, and "music" is whatever you named the directory you want to share (I'm assuming it's in your home directory).


Since my two local users are "equal", MUST a single user be identified as the owner?  Can I make the custom group (let's call it thesmiths) the owner as well as the group? like this...
chown thesmiths:thesmiths /home/shared

---

### Post by Vaphell on 2012-07-15
> MUST a single user be identified as the owner? Can I make the custom group (let's call it thesmiths) the owner as well as the group?
yes, but what difference does it make in this scenario? Group permissions are pretty much all that matters.

---

### Post by bodhi.zazen on 2012-07-15
This is an old thread and some of the advice is accurate, but dated.

IMO a better option is bindfs

[https://help.ubuntu.com/community/Bindfs-SharedDirectoryLocalUsers](https://help.ubuntu.com/community/Bindfs-SharedDirectoryLocalUsers)

Or, as an alternate, for finer grained control, perhaps ACL.

[https://help.ubuntu.com/community/UbuntuLTSP/ACLSupport](https://help.ubuntu.com/community/UbuntuLTSP/ACLSupport)

---

### Post by Morbius1 on 2012-07-16
> **kdford said:**
> Since my two local users are "equal", MUST a single user be identified as the owner?  Can I make the custom group (let's call it thesmiths) the owner as well as the group? like this...
chown thesmiths:thesmiths /home/shared
First, what Vaphell said.

Second, the syntax of the chown command is:
```
chown user-name:group-name /path
```"thesmiths" is a group name not a user name so you can't make the owner thesmiths unless you actually make a new user called thesmiths.

---

### Post by BoneKracker on 2012-07-16
> **bodhi.zazen said:**
> This is an old thread and some of the advice is accurate, but dated.

IMO a better option is bindfs

[https://help.ubuntu.com/community/Bindfs-SharedDirectoryLocalUsers](https://help.ubuntu.com/community/Bindfs-SharedDirectoryLocalUsers)

Or, as an alternate, for finer grained control, perhaps ACL.

[https://help.ubuntu.com/community/UbuntuLTSP/ACLSupport](https://help.ubuntu.com/community/UbuntuLTSP/ACLSupport)
I disagree, unless you already happen to be using bindfs or some kind of access control lists.  If not, then they are unnecessary complexity.  The use case he is describing is exactly what group permissions are for.

---

### Post by chocklet on 2012-07-16
This thread contains valuable information that I needed to know.  Yep, the magic "2" is the key for me too, along with the way that the explanation was segregated in its own paragraph (that even I could not miss) which stated...

"...any files in the directory automatically will inherit the group of the folder, as opposed to the group of the user putting the file there." 

It all started with a descriptive title that told me that I needed to take a look at the thread, and with a clearly defined question.  Thanks to everybody, and especially to BoneKracker for clear detailed explanations.    I hope that those who take the time to simplify complicated stuff understand the impact that they make.

---


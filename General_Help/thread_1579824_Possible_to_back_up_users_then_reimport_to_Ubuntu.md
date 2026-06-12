---
title: "Possible to back up users then reimport to Ubuntu?"
date: 2010-09-22
forum: General Help
---

### Post by Roasted on 2010-09-22
Is it possible to back up users on a system and later import them? Reason I ask is I got a new hard drive so I'm doing a fresh install of Ubuntu, but I do not want the permissions to get out of whack since the user account is tagged to a user ID, so unless I get them perfect there will be some sudo chown-ing to do...

Is it possible?

---

### Post by bodhi.zazen on 2010-09-22
Just back up /home/user_name for most things.

You will need to know the uid as linux actually uses a number and not a name to identify users.

See /etc/passwd , /etc/shadow, and /etc/groups

So as long as you know the uid, you would restore a deleted user by first restoring the /home directory and then pass uid options and /home options to adduser

[http://manpages.ubuntu.com/manpages/lucid/en/man8/adduser.8.html](http://manpages.ubuntu.com/manpages/lucid/en/man8/adduser.8.html)

```
adduser --uid xxx --gid yyy --home /home/user_name
```

Then, last, make sure ownership and permissions are correct in the home directory.

---

### Post by luvshines on 2010-09-22
You want to copy content to new HD ??

Try the cp -p option and backup /etc/passwd, /etc/shadow, /etc/group file to be replaced later

---

### Post by CharlesA on 2010-09-22
> **luvshines said:**
> You want to copy content to new HD ??

Try the cp -p option and backup /etc/passwd, /etc/shadow, /etc/group file to be replaced later

You'll probably have to run that command with sudo to keep the permissions.

rsync -a works too. :)

---

### Post by Roasted on 2010-09-22
Yeah - I know Linux looks at UID and not the actual usernames. I've done this same thing before and had to reset permissions since now "Fred" was not user 1001, he was user 1003, etc.

So if I back up /etc shadow+group+passwd and dump them on the new install I should be good to go?

---

### Post by bodhi.zazen on 2010-09-22
> **Roasted said:**
> Yeah - I know Linux looks at UID and not the actual usernames. I've done this same thing before and had to reset permissions since now "Fred" was not user 1001, he was user 1003, etc.

So if I back up /etc shadow+group+passwd and dump them on the new install I should be good to go?

and back up /home as well.

Otherwise it should work, in theory.

---

### Post by Roasted on 2010-09-22
> **bodhi.zazen said:**
> and back up /home as well.

Otherwise it should work, in theory.

Well my situation doesn't need /home, since these users never use my actual computer. I have a drive in my system entirely used and accessed via Samba, so their data gets backed up there. I just hate having to reinstall and even though it's only a few users, it's still a pain to remap who is who, and each time I kept thinking there's got to be a better way than this. I should be good to go though with the info above. Thanks guys!

---

### Post by CharlesA on 2010-09-22
> **Roasted said:**
> Well my situation doesn't need /home, since these users never use my actual computer. I have a drive in my system entirely used and accessed via Samba, so their data gets backed up there. I just hate having to reinstall and even though it's only a few users, it's still a pain to remap who is who, and each time I kept thinking there's got to be a better way than this. I should be good to go though with the info above. Thanks guys!

That'll help for sure. :)

I have a shell script that I run on new install that creates users with a specific uid:

```
#!/bin/bash

# Normal Variables
BIN=/bin/
USBIN=/usr/sbin/
NULL=/dev/null
# Start of shell script
# Create user htpc and add to group raid
${USBIN}useradd htpc -u 1001 -M -d $NULL -s $NULL
# Create user clone and add to group raid
${USBIN}useradd clone -u 1002 -M -d $NULL -s $NULL
#eof

```

Since those users only access the machine via Samba, I didn't have to set a UNIX passwd for them.

---

### Post by SaintDanBert on 2010-09-22
I've done ops similar to  your OP several times and several ways.
I've used **cp -av**:
The "-v" option to cp results in a list of actions to STDOUT.
The "-a" option to cp (archive) is short hand for "-dpR".
The "-R" option to cp recurses folder trees.
The "-dp" options are "--preserve=links,mode,ownership,timestamp"
(I've also used **tar** and  and **rsync -a** less often.)
```

$#--- save the files
$ cp -av  myOriginal  myCopy

$#--- restore the files
$ cp -av  myCopy  myOriginal

```

It helps to play a bit so you are comfortable with folder creation
based on what you put on the command line. Trailing slashes make sense
some times and not at others. Your mileage may vary.

After the new install, I'll have [color=orange]/home/user1[/color].
I'll have files for user1 on external storage.

I login as user1 and create a folder [color=orange] $HOME/oldeHome [/color]. I will then restore from backup into oldeHome. I can then
set ownership and permissions to match the new user1 with a recursive
command.

[highlight]CAUTION[/highlight] If a user has **symlinks** in their $HOME tree, (a) it can be rough getting a good backup, (b) it can be rough to get a good restore, (c) it is likely that you may have duplicate files when your finished.

Good luck,
~~~ 0;-Dan

---

### Post by SeijiSensei on 2010-09-22
It's a heck of a lot easier to just create a tarball of /home with tar.  If I have a lot of system administration tasks to do, I usually become the root user by starting with "sudo su" and going from there.  Otherwise expect to prepend "sudo" to the following:

cd /
tar cjvpf home.tar.bz2 home

Copy home.tar.bz2 to the new system, then run

cd /
tar xjvf /path/to/home.tar.bz2

All done; all permissions, symlinks, etc., preserved.  If you prefer you can use rsync with the '-av' switch if you have both the old and new drives installed on the same machine, or the old drive is on a machine visible over the network and accessible with ssh.

One warning about moving /etc/passwd and /etc/group.  If both the new and the old distros are identical and at the same release level, you should be fine.  Sometimes, though, there will be special accounts created when new services are added by later releases.  As a result I'd make sure you append just the old user information to the new passwd and group files.  All the users you create will have UIDs > 1000; those are the only ones you need to copy.  In /etc/shadow, the passwords are keyed by usernames, not UIDs, so just copy the lines from /etc/shadow that begin with the names of the users you have created.

I'm not sure from your comments exactly how Samba relates to this, but if people log into shares on your box, you may need to copy /etc/samba/smbpasswd as well.

---


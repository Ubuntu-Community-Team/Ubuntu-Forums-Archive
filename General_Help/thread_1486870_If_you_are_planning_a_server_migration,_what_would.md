---
title: "If you are planning a server migration, what would you do?"
date: 2010-05-18
forum: General Help
---

### Post by Roasted on 2010-05-18
Say I have a file server, with 300 users loaded on it with specific shares, permissions, ownership, etc.

What would I have to do in order to make the new server work JUST like the old one without any issue? 

I'm talking strictly from the standpoint of getting the users + shares + samba users + permissions migrated accordingly. Everything else I'm not worried about.

---

### Post by CharlesA on 2010-05-18
Personally I'd image the old machine and restore the image to the new machine.

That seems the best solution for migrating. You can just copy the shares and whatnot to another drive use rsync -a (as root) to keep the permissions and whatnot. Exporting the user list is possible, but I am not sure if you can keep the users passwords if you export, then import them again.

I did a "migration" from 9.10 to 10.04 on my small home server, and just ran a script to create the users in Linux, then they were automatically imported when I installed samba, however I had to set their passwords for them. I think you can force them to change the password on next logon, but that would be a pain in the backside.

---

### Post by jbrown96 on 2010-05-18
If you are using standard Linux permissions and not something exotic like ACLs, then it's easy to move your settings.

1) Copy /etc/passwd, /etc/group, /etc/user, and /etc/shadow to get your user info. 
2) Copy everything in /etc/samba/ for your samba settings.
3) Image the machine.
4) Boot into single user mode or from the LiveCD and copy all those files over to their proper locations.

---

### Post by Roasted on 2010-05-18
> **jbrown96 said:**
> If you are using standard Linux permissions and not something exotic like ACLs, then it's easy to move your settings.

1) Copy /etc/passwd, /etc/group, /etc/user, and /etc/shadow to get your user info. 
2) Copy everything in /etc/samba/ for your samba settings.
3) Image the machine.
4) Boot into single user mode or from the LiveCD and copy all those files over to their proper locations.

If I do this, would the restored users have home directories? What would happen if these users log in? Would they be able to save anything? Would their home folder just simply not exist?

---

### Post by jbrown96 on 2010-05-18
> **Roasted said:**
> If I do this, would the restored users have home directories? What would happen if these users log in? Would they be able to save anything? Would their home folder just simply not exist?

They wouldn't have home folders and would probably get an error because the directory doesn't exist. You would at least need to create a home directory for them, but you probably want to copy over their data anyway.

If you just need the empty home directories and have a lot of users, it would be simple to parse /etc/passwd to get each user's home directory and create it.

---

### Post by Roasted on 2010-05-18
> **jbrown96 said:**
> They wouldn't have home folders and would probably get an error because the directory doesn't exist. You would at least need to create a home directory for them, but you probably want to copy over their data anyway.

If you just need the empty home directories and have a lot of users, it would be simple to parse /etc/passwd to get each user's home directory and create it.

How exactly would I automate it so the home directories are created with the appropriate ownership/permission for each individual user?

---

### Post by CharlesA on 2010-05-18
> **Roasted said:**
> How exactly would I automate it so the home directories are created with the appropriate ownership/permission for each individual user?

Could probably rsync to an external drive and then rsync them to the new server when it is up and running.

---

### Post by Roasted on 2010-05-18
> **CharlesA said:**
> Could probably rsync to an external drive and then rsync them to the new server when it is up and running.

Ehh, little backwards from what I want to do.

Say I have an old server + new server. In the servers (both of them) I have the OS drive, then I have the data drives where the shares are. The home directories are not where data is stored - data is only stored in /media/storage, etc on those drives mounted there.

What I want to do is have the data in /media/storage like it's always been, BUT I don't want users to error out if they log into the server itself. I want those home directories to exist.

OR...

If I sudo rsync all home directories + /media/storage, then save the /etc/passwd + users + groups + samba, put it on the new server, would the home directories when I rsync them to the new server match up accordingly to each of the users since I have their /etc/passwd + group + whatever else imported back to the new server?

---

### Post by CharlesA on 2010-05-18
Yeah, the point of doing the rsync to keep the permissions/owner/group from the old server.

That should work, I'd suggest trying it with a small amount of data and then seeing if it will work.

If it does, then do it with all the data.

Talking about solution #2.

---

### Post by Roasted on 2010-05-18
> **CharlesA said:**
> Yeah, the point of doing the rsync to keep the permissions/owner/group from the old server.

That should work, I'd suggest trying it with a small amount of data and then seeing if it will work.

If it does, then do it with all the data.

Talking about solution #2.

Right - but the only question I have is (and this may be me backtracking a bit to earlier posts) but if I rsync a folder as root, I take permissions, ownership, everything. This is also the same as gksudo nautilus and just copy/paste, isn't it? Anyway, if I do this with /media/storage, and I save the etc user/passwd/etc folder, I therefore retain all "mappings" to each user to each drive and there would be no crossing of permissions.

However, at the same token, the same would be true for /home directories too. All I would have to make sure I do is rsync as root /home + /media/storage. Then import it back over, merge the passwd and group files and everything else, and blam - home directories are back in business. Storage is back in business. Users are back in business. All permissions retained, etc.

---

### Post by CharlesA on 2010-05-18
Yes, that should be what occurs.

I'd still test it on a small amount of data first to make sure.

---

### Post by HermanAB on 2010-05-18
If it has to be exactly the same and there are hundreds of accounts, then I'd virtualize it.  Once you have it working as a virtual machine you can move it to anything at all.

I never install a server on the bare metal anymore.

---

### Post by jbrown96 on 2010-05-18
> **Roasted said:**
> Right - but the only question I have is (and this may be me backtracking a bit to earlier posts) but if I rsync a folder as root, I take permissions, ownership, everything. This is also the same as gksudo nautilus and just copy/paste, isn't it? Anyway, if I do this with /media/storage, and I save the etc user/passwd/etc folder, I therefore retain all "mappings" to each user to each drive and there would be no crossing of permissions.

However, at the same token, the same would be true for /home directories too. All I would have to make sure I do is rsync as root /home + /media/storage. Then import it back over, merge the passwd and group files and everything else, and blam - home directories are back in business. Storage is back in business. Users are back in business. All permissions retained, etc.

rsync will copy permissions correctly as long as you use the -a flag (recommended) or -p flag.

---

### Post by CharlesA on 2010-05-18
Oops, forgot to mention that.

You'd use this command:

```
sudo rsync -a /source/ /destiniation/
```

---

### Post by Roasted on 2010-05-18
> **HermanAB said:**
> If it has to be exactly the same and there are hundreds of accounts, then I'd virtualize it.  Once you have it working as a virtual machine you can move it to anything at all.

I never install a server on the bare metal anymore.

While I can understand your opinion, there will be instances where virtualizing is not the answer, which is where my question came in with this thread in regard to how do you handle that task accordingly.

I know when I reinstall Ubuntu on my little file server at home the wrong users get assigned to the wrong shares, but a minute or two in terminal chmod and chown-ing everything fixes that. But like I said, what if I was on a HUGE server. One with 800 people connected to it with their own samba network shares, etc. That's where I started to wonder how you could migrate from server to server, since I know Microsoft has some sort of migration assistant - made me wonder how Linux could handle the same task.

---

### Post by CharlesA on 2010-05-18
> **Roasted said:**
> I know when I reinstall Ubuntu on my little file server at home the wrong users get assigned to the wrong shares, but a minute or two in terminal chmod and chown-ing everything fixes that. But like I said, what if I was on a HUGE server.

I know what you mean there. I ended up setting up a script of sorts when I do reinstalls on my server at home.

It created the users and groups with specific IDs so that I wouldn't have to screw around with chown.

```
#Create group raid
addgroup -gid 1004 raid
#Create user htpc and add to group raid
useradd htpc -u 1002 -M -d /dev/null -s /dev/null -U -G raid
#Create user clone and add to group raid
useradd clone -u 1003 -M -d /dev/null -s /dev/null -U -G raid
#Add charles to clone and raid groups
usermod -a -G karen,clone,raid charles


```

Unfortunately that isn't really feasible with on a server with 800+ users.

---

### Post by Roasted on 2010-05-18
> **CharlesA said:**
> I know what you mean there. I ended up setting up a script of sorts when I do reinstalls on my server at home.

It created the users and groups with specific IDs so that I wouldn't have to screw around with chown.

```
#Create group raid
addgroup -gid 1004 raid
#Create user htpc and add to group raid
useradd htpc -u 1002 -M -d /dev/null -s /dev/null -U -G raid
#Create user clone and add to group raid
useradd clone -u 1003 -M -d /dev/null -s /dev/null -U -G raid
#Add charles to clone and raid groups
usermod -a -G karen,clone,raid charles


```

Unfortunately that isn't really feasible with on a server with 800+ users.

Right. However, the solution you gave me earlier (copying /etc/passwd + groups + samba + whatever else was mentioned) would still work for me at home with my little file server scenario - wouldn't it? I'm not moving data, but I swear by fresh installs from release to release, forcing me to redo users, and whatnot.

---

### Post by CharlesA on 2010-05-18
> **Roasted said:**
> Right. However, the solution you gave me earlier (copying /etc/passwd + groups + samba + whatever else was mentioned) would still work for me at home with my little file server scenario - wouldn't it?

Probably. I've never done it before, but since that is where Linux stores the passwords and groups and whatnot, it should work fine.

---

### Post by jbrown96 on 2010-05-18
Here's a script that will go through your /etc/passwd file and create home folders for users that can login (i.e. not system users). It will also change ownership to the correct user, but you may also want to alter the permissions if you want them to be shared/not shared.

```
#!/bin/bash

grepped=`cat /etc/passwd | egrep -o '/home/[_a-zA-Z0-9]+\:/bin/bash'`
dir=`echo $grepped | egrep -o '/home/[_a-zA-Z0-9]+'`
user=`echo $dir | egrep -o [_a-zA-Z0-9]+$`

mkdir $dir && chown -R $user:$user $dir
done
```

---

### Post by CharlesA on 2010-05-18
Nice script. Thanks!

---

### Post by louieb on 2010-05-18
> **Roasted said:**
> ...) but if I rsync a folder as root, I take permissions, ownership, everything. This is also the same as gksudo nautilus and just copy/paste, isn't it? 

Not the same. Ownership is not preserved when you copy and paste. The user doing the copy becomes the owner of the copy. Not what you want. 

rsync with the -a option is one way to preserve ownership and permissions.

---

### Post by CharlesA on 2010-05-18
I think you can also use cp -a, but I prefer rsync.

---


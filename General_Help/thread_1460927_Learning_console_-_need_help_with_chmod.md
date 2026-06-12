---
title: "Learning console - need help with chmod"
date: 2010-04-23
forum: General Help
---

### Post by nolsen01 on 2010-04-23
So I created a group called devel and then I created an account called hack. The only member of devel is hack, and the only group that hack belongs to is devel.

I would like to grant write access to /usr/src to devel. How do I do this?

I've found a couple tutorials online, but they are not being clear. If I use "chmod g+w /usr/src" and I'm logged in as root, what group is it assigning write privileges to? These tutorials only say "the group."

---

### Post by patchwork on 2010-04-23
Edit:  Sorry misread question

---

### Post by nothingspecial on 2010-04-23
Why not just add hack to admin?

I wouldn`t go about chmodding /usr/src

Well actually, I probably would, but then I like to break things on purpose :-$

---

### Post by SaintDanBert on 2010-04-23
Your file and folder are owned user=root, group=root.
Your user is not a "root" user of any sort.

Use [highlight]chown[/highlight] to alter file or folder user and group "ownership."
User [highlight]chmod[/highlight] to alter a file or folder permissions.
You are on the right track but did not appear to go quite far enough.

Open a console or terminal window.
Type the command **id**. You get something that looks like this:
```

user@host:path/ $ id
uid=1000(someUser) gid=1000(someUser) groups=4(adm), 20(dialout), 21(fax), 24(cdrom), 29(audio), 30(dip), 46(plugdev), 104(fuse), 106(lpadmin), 112(netdev), 121(admin), 122(sambashare), 1000(someUser), 1001(video), 1002(someGroup), 1003(otherGroup)

```

Now look at the folder in question:
```

user@host:path/$ ls -lhd /usr/local/src
drwxr-xr-x 2 root root 4.0K 2009-04-21 12:28 /usr/local/src

```

If the left-most name, the userIdent, on the folder matches the UID from the user, then you own the folder.

If the right-most name, the groupIdent, on the folder matches the GID from the user, then you are the group owner.

If any of the other groups on the user match the right-most name from the folder, you also get group access.

If neither UID nor GID match, then you get "other" access.

Files and folder get exactly one user-ident and group-ident.
Users may be members of several groups.

There is also a utility suite call "access control lists" that offers much finer control but adds some complexity.


Good luck,
~~~ 0;-Dan

---

### Post by nikhilbhardwaj on 2010-04-23
this should do the trick for you
```

sudo chown -R hack:devel /usr/src

```

---

### Post by nothingspecial on 2010-04-23
> **nikhilbhardwaj said:**
> this should do the trick for you
```

sudo chown -R hack:devel /usr/src

```

Not a good idea.

By all means, chown and chmod whatever you like.

But this way leads to breakage.

sudo exists for a reason.

---

### Post by nikhilbhardwaj on 2010-04-24
> **nothingspecial said:**
> Not a good idea.

By all means, chown and chmod whatever you like.

But this way leads to breakage.

sudo exists for a reason.

how else do you propose to answer the OP's question
/usr/src is owned by root
to change the ownership to the user/group that he/she wants to you have to use sudo
i'm sure its much better than chmod 777

if you know a better way 
then by all means let us all know.

---

### Post by nothingspecial on 2010-04-25
I am assuming that the OP would like to modify the kernel source(s) contained within /usr/src

I am suggesting using sudo to either edit the code in /usr/src or copy it to his/her home directory, change the ownership of the copied directories and edit them there.

Rather than changing the ownership of /usr/src

---

### Post by QLee on 2010-04-25
> **nothingspecial said:**
> I am assuming that the OP would like to modify the kernel source(s) contained within /usr/src

I am suggesting using sudo to either edit the code in /usr/src or copy it to his/her home directory, change the ownership of the copied directories and edit them there.

Rather than changing the ownership of /usr/src

+1 I agree that this would be preferred to changing permissions of system files

---

### Post by SaintDanBert on 2010-04-25
I routinely do the following

1.  create a $HOME/Prj folder for myself
2.  create folders in /usr/local/src for source packages
3.  I set ownership and permissions along the lines the OP suggests
4.  I return to my $HOME/Prj folder and create links to the folders in /usr/local/src

Now when I use ** cd ~/Prj/something ** I wind up in **/usr/local/src/something ** with a secondary group that is the same as the project file owner.

Wnen I deploy the project to /usr/bin or /usr/sbin or other system space, I rely on links instead of copies of the files ... unless the files will continue to evolve.

Cheers,
~~~ 0;-Dan

---


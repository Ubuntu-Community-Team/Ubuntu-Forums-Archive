---
title: "Auto Map Windows Server Folder For All Users On Ubuntu Systems"
date: 2011-02-25
forum: General Help
---

### Post by Roasted on 2011-02-25
I work for a school district. We are running in a Windows environment with a Windows domain. It was asked of me if I could get an Ubuntu system on our domain and running without issue, as we would like to tinker with the idea of slowly introducing Ubuntu systems to the network.

I have a test system here. I added it to the domain using Likewise-Open. I have Samba installed, etc. Here's the next curve ball that I need answered.

All user documents are stored in their individual shares on the same Windows server. In Windows, we use re-directed My Documents, so their My Documents actually points to \\server\users\bob_dole instead of C:/Documents and Settings/Bob Dole/My Documents.

How can we do this in Ubuntu? I don't care if it re-maps the home directory or creates a folder on the desktop that is linked. Either way, I want to log in to ANY Ubuntu system and blam - I have a link to \\windowsserver\users\my_share. I want any user on the domain to be able to do that to any Ubuntu system and have a link to THEIR folder on the Windows server.

How can I do this?

---

### Post by amsterdamharu on 2011-02-27
You can mount /home/myuser/Documents to a samba share. To mount it using fstab would assume only one user logs on to the computer so you need some script to take care of it if there are possible more than one user logging in to the computer. As is usually the case with Windows domains, the user can choose whatever computer it wishes to log on.

As explained here
[http://ubuntuforums.org/showthread.php?t=1695254](http://ubuntuforums.org/showthread.php?t=1695254)
You can add an upstart job that in turn will start a script in /usr/bin when the user has logged in.

You can run a script when the user loges in (as strartup application preferences in gnome-control-center) but mounting is only allowed by root so you have to sudo it and then give the user sudo rights as well.

Since mounting has to be done by root anyway I would go for the first option.

The mount command would look a bit like this:
```
mount -t smbfs -o username=<username>,password=<passwd> //sambashare/<username> /home/<username>/Documents

```
The problem here is that password might change when the user changes it so if this happens you need to change the script (maybe there is an upstart event for that so you can script it to change the automount). 
The password is stored in a text file so there is a security issue even if you have the script only readable by root.
The third problem is that mount will run as root so "whoami" will return root and not the user logged on. So we need to figure out what user is logged in.

---

### Post by amsterdamharu on 2011-02-27
Ooops, see that with likewise it is not needed to identify with user and password when accessing a share:

[https://help.ubuntu.com/10.04/serverguide/C/samba-ad-integration.html](https://help.ubuntu.com/10.04/serverguide/C/samba-ad-integration.html)

```
mount.cifs //MS_Server/share /home/<username>/Documents
```

It looks like this can run as normal user so you can put it somewhere in the users .bash_login (under home/<username>)

You could try putting the entire home/<username> on a Windows share.

---

### Post by Roasted on 2011-02-28
All right, this gives me some info to review when I get home and back to work later this week. Ultimately, I really don't care where the documents mount to.

They could mount to the entire /home/user directory, or /home/user/Documents. Along with that, I wouldn't mind it just auto-generating a folder on the desktop with the folder path leading to \\WindowsServer\Users\Bob_Dole or whoever the user may be.

Point is, I just need to make sure whatever user that logs in to whatever Ubuntu system on the Windows domain, in some way shape or form, has a direct link to their Windows folder on the server.

---

### Post by btindie on 2011-02-28
There's a package called pam-mount (libpam-mount) that allows you to automatically mount user shares when the session starts which may suit your needs.

Additionally there's autofs which is traditionally used in UNIX environments to mount a users home directory but it can also be used to mount cifs shares. Because of the way it works you may want to create a /documents mount point on the Ubuntu workstations and for each user automatically create a sym-link from /home/joe_blogs/Documents to /documents/joe_blogs.

In /etc/auto.master you'd have something like
```
/documents      auto.docs  --timeout=60 --ghost
```

and in /etc/auto.docs
```

joe_blogs     -fstype=cifs       ://WindowsServer/Users/&

```

You can even configure autofs to retrieve the maps from LDAP so you only need to maintain the one copy which could be stored in [AD]("http://ondarnfs.blogspot.com/2009/08/automounter-integration.html") if you don't have any Linux servers.

---

### Post by Roasted on 2011-03-05
> **btindie said:**
> There's a package called pam-mount (libpam-mount) that allows you to automatically mount user shares when the session starts which may suit your needs.

Additionally there's autofs which is traditionally used in UNIX environments to mount a users home directory but it can also be used to mount cifs shares. Because of the way it works you may want to create a /documents mount point on the Ubuntu workstations and for each user automatically create a sym-link from /home/joe_blogs/Documents to /documents/joe_blogs.

In /etc/auto.master you'd have something like
```
/documents      auto.docs  --timeout=60 --ghost
```

and in /etc/auto.docs
```

joe_blogs     -fstype=cifs       ://WindowsServer/Users/&

```

You can even configure autofs to retrieve the maps from LDAP so you only need to maintain the one copy which could be stored in [AD]("http://ondarnfs.blogspot.com/2009/08/automounter-integration.html") if you don't have any Linux servers.

Would this work regardless of what user logs in? I want Bob Dole to log in and get Bob Dole's link, nobody elses. Then I want Steve Jobs to log in and get a link to his files, nobody elses. etc...

Likewise, this is a school district, and we have our students broken up into 4 categories based on years.

So you have:

\\WindowsServer\ClassOf2014\*student name*
\\WindowsServer\ClassOf2015\*student name*

etc...

So even though I need it to hit the proper student, I also need it to hit the proper year that the student graduates in...

make sense?

Is this even possible?

---

### Post by btindie on 2011-03-06
> **Roasted said:**
> Would this work regardless of what user logs in? I want Bob Dole to log in and get Bob Dole's link, nobody elses. Then I want Steve Jobs to log in and get a link to his files, nobody elses. etc...

Likewise, this is a school district, and we have our students broken up into 4 categories based on years.

So you have:

\\WindowsServer\ClassOf2014\*student name*
\\WindowsServer\ClassOf2015\*student name*

etc...

So even though I need it to hit the proper student, I also need it to hit the proper year that the student graduates in...

make sense?

Is this even possible?

The example I gave just simplifies writing of the autofs maps and was just for one user. The '&' gets replaced with the keyvalue - i.e. username.

To further extend this example you'd need something like:
```

bob_dole            -fstype=cifs             ://WindowsServer/ClassOf2014/&
steve_jobs          -fstype=cifs             ://WindowsServer/ClassOf2015/&

```That would need to be repeated for each user. Replace '&' with the users home directory name if it differs to their Linux login name.

However, for this to work the usernames need to be unique as they're keys in what is effectively a database. So you couldn't have user bob_dole in both ClassOf2014 and ClassOf2015. You could do

```

bob_dole            -fstype=cifs             ://WindowsServer/ClassOf2014/&
bob_dole15          -fstype=cifs             ://WindowsServer/ClassOf2015/bob_dole

```I think you'd also want to use KERBEROS authentication for the users when they log into the Linux clients to setup the authentication tokens to be able to mount their home directories on /documents automatically when they access it. Just create a sym-link in the users Linux home directory pointing to their mounted Windows home directory so they can access it easily.

---

### Post by Roasted on 2011-03-07
Now what do you mean I would need an entry per user? I have several HUNDRED users, so doing that individually wouldn't be an option, to be pretty blunt about it.

I'm all right setting up 1 entry with wildcards to hit all users. I'm also okay with setting up 4 entries with wildcards if I need to with setting up ClassOf2014/15/16/17, but I won't waste time setting up hundreds of links for our users.

Likewise, I also began to wonder. How CAN this work through fstab? I'm thinking I'd have to set something in the .profile level, because fstab handles tasks at bootup. Well these systems will be turned on once and logged into 8 or 9 times before they reboot, so I'm failing to see how fstab would help...

Appreciate the help so far!

---

### Post by btindie on 2011-03-08
You can use wildcard matching on the key as in
```
*                    -fstype=cifs          ://WindowsServer/Users/&
```but it wouldn't suit your needs as not all users home directories are in the same directory.

If you were to separate the years on the Linux computers as you have done under Windows then it would be more straight forward. You need something like

/etc/auto.master:
```
/documents        auto.docs
```/etc/auto.docs:
```
*                 -fstype=autofs,-Dclass=&        auto.docs_sub
```/etc/auto.docs_sub:
```
*                 -fstype=cifs                  ://WindowsServer/${class}/&
```Which will give you
/documents/ClassOf2014/bob_dole
/documents/ClassOf2015/steve_jobs
*if* the directory exists on the windows server.

Alternatively, if you've got the users homdirectory location stored in your AD, or in a form that's usable, then you can write your own automount program that's called when the directory is accessed. Take a look at /etc/auto.net and /etc/auto.smb for examples. It can query LDAP (AD) for the given username and return the directory on the Windows server it needs to mount.

Another alternative, if you don't want to write each individual entry yourself then you can write a script to generate it for you. All it'd need to do is query LDAP to get the users name and work out where their home directory is stored then generate the auto.doc file. Or if you were storing your MAPS in LDAP, then write it back to the LDAP server.

It has nothing to do with fstab, it uses a program called automount from the autofs package that monitors specific directories for access. When access is required it mounts the folder.

Read up on the [Autofs]("http://linux.die.net/man/5/autofs") docs and look at the examples that are available online such as [here]("http://www.greenfly.org/tips/autofs.html").

---

### Post by Roasted on 2011-03-30
> **amsterdamharu said:**
> Ooops, see that with likewise it is not needed to identify with user and password when accessing a share:

[https://help.ubuntu.com/10.04/serverguide/C/samba-ad-integration.html](https://help.ubuntu.com/10.04/serverguide/C/samba-ad-integration.html)

```
mount.cifs //MS_Server/share /home/<username>/Documents
```

It looks like this can run as normal user so you can put it somewhere in the users .bash_login (under home/<username>)

You could try putting the entire home/<username> on a Windows share.

I tried the above with no success.

mount.cifs: permission denied: no match for /home/jason/Documents found in /etc/fstab

I cannot use root for these students. I just... can't. Is there no way I can automatically link them to their shares? In fact, this is our structure.

Windows Server - Named "Storage" - File Server For All Data
Within that, you have "Students" and then Class of folders.

//Storage/Students/Class of 2011
//Storage/Students/Class of 2012
//Storage/Students/Class of 2013
//Storage/Students/Class of 2014

Is there any way I can just automatically mount the generic path of//Storage/Students to /home/ANYUSERTHATLOGSINWITHOUTROOT/Documents

That way if the student logs in and sees the classes folders, they'll know to just follow the path from there.

---


---
title: "apache &amp; group permissions"
date: 2010-11-12
forum: General Help
---

### Post by Matpen on 2010-11-12
Ok, this costed me a whole day of trying and retrying.

I set up a small home server with apache, php, and mysql.
System infos:
Linux 2.6.31-22-generic-pae
Ubuntu 9.10 Karmic Server edition
Apache/2.2.12 (Ubuntu)

Until now, it served happily a couple of sites, with no problems. But now, I wanted to set up my ftp server to point to the same directory as one of the sites, for me to be able to upload and manage files via ftp. As a server I normally use proftpd.

With my usual config, proftpd runs with its own user and simulates the user ftpuser:ftpgroup when creating files. So I just changed all the files to be owned by this user and group. Permissions set to 770.

Everything works fine, and I'm able to access the data via ftp. BUT, when I try to browse my site the usual way (i.e. point firefox to its address) a 403 forbidden error is issued.

Of course, you will say: you didn't allow access to apache. Well, I remembered that right away, and added the user www-data to the ftpgroup user. Now I espect apache to be able to read and serve the files.

Still same problem. 403. The apache error log is full with "permission denied" errors.

After many attempts, I logged in as the user www-data, and tested access to the files. This way I'm able to cd into the directory, and read-write the files with nano.

As a test, I tryed the other way around. Setting www-data:www-data as the owner of the files, and adding the ftpuser to the www-data group. This way apache works, but proftpd does not.

I hope that someone will be able to shed some light on this. Most probably it has something to do with a misunderstanding of groups permissions or the way this two deamons access the files.

Thank you in advance!

---

### Post by skillet-thief on 2010-11-12
I'm not sure what the problem is, but have you tried starting and stopping apache. At the command line, new group permissions don't become active until you start a new shell, ie. log in again. I wouldn't be surprised if something similar wasn't happening with apache.

Also, are you sure you want to give apache write access to all of your files? I've always considered that a necessary evil.

---

### Post by Matpen on 2010-11-14
Thank you very much for your reply, skillet-thief!

Indeed, it seems to be necessary to restart the daemon for the changes to /etc/group to take effect. This helped me a lot.

Unfortunately, I'm unable to get this work if one group has more than one member. For example, it doesnt work if the owner:group is set to matteo:matteo, and both ftpuser and www-data are members of the group "matteo".

The workaround for now is to set the owner:group to matteo:ftpgroup and add www-data to the group ftpgroup.

Anyway, I would really appreciate some help in finding out whats going on, as I will probably need the solution soon or later in the future.

Thanks again!

---

### Post by Matpen on 2010-11-14
> **skillet-thief said:**
> Also, are you sure you want to give apache write access to all of your files? I've always considered that a necessary evil.

Oh, btw! Apache actually needs write access to a subdirectory (where some files are stored by the web app). However, the ftpuser needs write access to all of them, so I had to grant write permissions to the whole group (and thus to apache).

Permissions 770 was actually used for testing purposes only, I now managed to switch to the safer 660.

Thank you for pointing out that, anyway. People often forget, how important it is, to correctly set file access permissions!

---

### Post by Matpen on 2010-11-18
bump

---

### Post by skillet-thief on 2010-11-21
I'm really not sure why that isn't working for you, but have you considered an ownership schema like mateo:ftpuser, where www-data is a member of mateo, and then assigning privileges like 760?

---

### Post by Matpen on 2010-11-22
Thank you for your post, skillet-thief!

Yes, that works (sort of). But as I pointed out before, it only does, when there is only one member of the group, which is enough for this case.

I was just wondering what I could do, if I needed to add more users...

---

### Post by skillet-thief on 2010-11-22
I'm sorry, maybe I got things backwards. What I meant was making ftpuser the owner of all of your files, and mateo the group. This way the 760 permissions would make sense.

The problem of why you can't add more users to the group seems very strange. I wonder if you are doing something slightly wrong when assigning group membership. (This kind of thing happens to me all of the time.) I would double check the output of ls -l to make sure that you are not, for example, reversing user and group somehow.

---

### Post by Matpen on 2010-11-23
Thanks again for your reply!

The way you describe would of course work too. It is a variation of the solution I ended up with, i.e. setting user:group = matteo:ftpgroup and add www-data to the group ftpgroup.

I too thought I could have done something wrong with the permissions or the memberships. I did double check with ls -l and everything looks fine to me. And most importantly, I found out that, by switching to user www-data (su www-data) everything works as it should, even with multiple users per group.

That is why I thought, that the catch lies not actually in the membership, but in the way apache/proftpd simulate the user for accessing the files (recall that apache is actually run by root on startup).

Again, thanks in advance for any input!

---

### Post by skillet-thief on 2010-11-24
> The way you describe would of course work too. It is a variation of the  solution I ended up with, i.e. setting user:group = matteo:ftpgroup and  add www-data to the group ftpgroup.


The advantage with what I was proposing is that you can give different rights to ftpuser (7) and www-data (6).

> That is why I thought, that the catch lies not actually in the  membership, but in the way apache/proftpd simulate the user for  accessing the files (recall that apache is actually run by root on  startup).


I doubt that this has anything to do with it. apache and proftpd don't pretend to be unprivileged users, they *actually become*, respectively, www-data and ftpuser. I still suspect some kind of mixup with the way that your groups are organized. Have you looked in /etc/passwd and /etc/groups to make sure you are doing what you think you are doing? But otherwise, at this point, if your system is working I wouldn't worry about the group problem that much.

---

### Post by Matpen on 2010-11-25
> 
The advantage with what I was proposing is that you can give different rights to ftpuser (7) and www-data (6).


Yes, you are right. This way it is even better, I have a finer degree of control over user permissions.

> 
apache and proftpd don't pretend to be unprivileged users, they *actually become*, respectively, www-data and ftpuser


Now, this is a very important information to me. This means that, if I can access the file when I become the www-user, apache must be able to access them, as well.
The direct consequence is that the problem must lie somewhere else.

> 
I still suspect some kind of mixup with the way that your groups are organized. Have you looked in /etc/passwd and /etc/groups to make sure you are doing what you think you are doing? But otherwise, at this point, if your system is working I wouldn't worry about the group problem that much.


Unfortunately I did double and triple-check those files already... they seem to be correct to me.
At this point, my guess is that the problem is somehow special to my system. Maybe some kind of interaction which is difficult to trace and reproduce. And as you state, the workaround you propose is more than sufficient for now.

Anyway, I learned some crucial points from this problem:
- it IS possible to add more user to a group (I was starting doubting it!)
- daemons BECOME the unprivileged user after startup, and do not just simulate it
- there is something else wrong in my system :)

Now that I'm sure about this points, I will elaborate a couple of experiments. If by chance I find out what's going on, I will definitely post here for the sake of completeness.

For the moment, I really thank you many times for you help, skillet-thief. Keep up the good community!

---

### Post by skillet-thief on 2010-11-25
Happy to help!

---


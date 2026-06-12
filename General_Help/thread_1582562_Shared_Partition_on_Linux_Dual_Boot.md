---
title: "Shared Partition on Linux Dual Boot"
date: 2010-09-26
forum: General Help
---

### Post by neu5eeCh on 2010-09-26
**Another question:** I have a dual boot system: Fedora & Ubuntu. 

The shared partition is EXT4. I recently had to reinstall Ubuntu and now Fedora claims that it lacks the permissions needed to access anything in the shared partition. If I grant myself the rights in Fedora, will those rights muck up Ubuntu?

---

### Post by perspectoff on 2010-09-26
In a way, this situation is desirable.

You can view the owner/group for the folders on the shared partition using a File Manager like Nautilus as root (from either OS):

 sudo nautilus

For routine use, you must have a similarly named user on both OS to access the shared partition (or at least a similarly named group to which a user on each OS belongs), if you don't want to access the partition as root all the time. The shared partition must have permissions for the user or group in common (are alternatively be made read/write/execute for everyone).

Fine-graining your access controls is a desirable feature of Linux.

---

### Post by yetiman64 on 2010-09-26
> **perspectoff said:**
> ...sudo nautilus.... 

@ perspectoff, To use sudo and nautilus, "gksudo" should be used instead, as nautilus is a graphical app. Or alternately you could use "gksu nautilus"

Link #4 in my sig has an explantion under the heading "Graphical Sudo" down the page a bit, you may wish to alter the command, yetiman64.

---

### Post by azc on 2010-09-26
Also, make sure the user and group IDs are the same for Fedora and Ubuntu.

The **id** command: **$ id username** should return the "uid" and "gid".

Not sure about Fedora, but CentOS starts regular users with a uid and gid of 500.

Whereas Ubuntu begins the initial account uid and gid of 1000.

---

### Post by neu5eeCh on 2010-09-26
Thanks for all your comments. This is just the kind of help I needed. I'll try making sure my user and group ID matches in both.

---

### Post by srs5694 on 2010-09-27
> **perspectoff said:**
> You can view the owner/group for the folders on the shared partition using a File Manager like Nautilus as root (from either OS):

 sudo nautilus

That's overkill, and potentially dangerous. You should *not* run programs as root unless it's necessary, and it certainly is not necessary for this job. (It's necessary to *change* the ownership of files, but not to find out what the ownership is.)

I'm not very familiar with Nautilus (I don't use it much myself), but most file managers let you see who owns files and directories by right-clicking and selecting an option called Properties. Click the Permissions tab in the resulting dialog box. This works in both KDE's and Xfce's file managers, and I'd be shocked if there weren't something similar in Nautilus. Alternatively, it's easily accomplished (and more efficiently if you need to check many files) using the text-mode ls command; just type "ls -l /path/to/file" to see full information, including the owner, group, and permissions on /path/to/file. If that file is a directory, you'll see the information on all the files and directories it contains; or change "-l" to "-ld" to see the information on just that one directory.

> For routine use, you must have a similarly named user on both OS to access the shared partition (or at least a similarly named group to which a user on each OS belongs), if you don't want to access the partition as root all the time. The shared partition must have permissions for the user or group in common (are alternatively be made read/write/execute for everyone).

That's not quite correct. Linux uses user ID (UID) and group ID (GID) *numbers* to control access to files. The names we humans use are assigned to the numbers in the /etc/passwd and /etc/group files (or in other ways in advanced configurations), but these names are irrelevant as far as Linux is concerned. Suppose you've got a file with a UID of 1001 and a GID of 523. On one installation, those might correspond to the user fred and the group devel; but on another installation on the same system, they might correspond to the user sally and the group sally. On this second system, fred might have a UID of 1003, and sally might have a UID of 1002 on the first system. Such differences can get very confusing very fast.

azc's suggestion of synchronizing the UID and GID values on the two installations is the sensible way to go, at least in this specific case. This can be done with the text-mode usermod command, or probably with a GUI front-end, as in "sudo usermod -u 1000 -g 100 fred" to change fred's UID to 1000 and GID to 100. This command will *not,* however, change the ownership of files; for that, chown will be required after making the UID change, as in "sudo chown -R fred /home/fred". Log out immediately after doing this. In fact, it's really best to do this from a direct root login, but Ubuntu doesn't permit such logins by default. Fedora does, though, so it's probably best to change the Fedora UID to match the UID in Ubuntu.

> Fine-graining your access controls is a desirable feature of Linux.

On that much we do agree!

---

### Post by neu5eeCh on 2010-09-27
Thanks SRS, I was fast asleep when you posted this.

In fact, I discovered a 2007 post on the Fedora Forum with information similar to what you provided - but the author concluded there wasn't a way to change the UID or GID in Fedora (at that time). The route suggested (which I followed) was to create a user (B), then delete ones original account (including home directory). I copied the files I needed, created user (B), deleted my original account, then recreated my original account (same username and password), but specified a new UID * GID. This works because in Fedora (may also be true in  Ubuntu) the supervisor can specify a user's UID and GID when a new account is created (post OS-install).

The only issue I face now is Fedora's complaint, in terminal, that it "cannot find name for group ID". So far, this "problem" seems cosmetic. Do you know a fix?

In my case, I assigned my user 1000 & 1000, which is the UID & GID of my Ubuntu account.

---

### Post by srs5694 on 2010-09-27
I can't comment on the specific Fedora forum post you reference; however, I can guarantee you that it *is* possible in Fedora, since I've done it. My suspicion is that the poster simply didn't know how to do it. The workaround you outline should also work.

Chances are you're missing a relevant entry in the /etc/group file. You should be able to add one either by manually editing the file or by using the groupadd command as root:

```

groupadd -g 1000 somename

```

Change "somename" to the name you want to use.

---

### Post by neu5eeCh on 2010-09-28
Thanks for that last suggestion SRS, I'm marking this case SOLVED.

---


---
title: "windows ftp to linux box"
date: 2006-04-15
forum: General Help
---

### Post by lezz on 2006-04-15
i have a windows computer from which i want to run ftp client and connect it to the ubuntu vsftpd for downloading files. i use local user logon to the server but windows cant see my symbolic link in /home/ftpuser.

#cd /home/ftpuser
#ls -la

lrwxrwxrwx  1 root root   14 2006-04-16 01:00 share -> /mnt/share

when i log into it with my linux box i will see it the link as a directory. but not from windows. is this a compatibility problem between ntfs and ext3? how do i then make windows seeing this directory/symlink?

---

### Post by Ensnared on 2006-04-15
FTP doesn't care about filesystems - all that is required is that the server understands the filesystem it's running on and the client understanding the filesystem it's running on, and that they both support the FTP protocol for transferring files between eachother. If you connect with an ftp-client from the same computer as the server is running on, you'll see the exact same as you see with the Windows ftp-client.

It's more of an issue of the vsftp-daemon not supporting symlinks that are linked to items located outside of the ftp-server root directory, which I'm pretty sure is the case with vsftpd as well as most other ftp-daemons.

I don't think there is any way to make vsftpd support these kinds of symlinks, but I could be wrong. Couldn't find anything about it in the documentation atleast.

---

### Post by lezz on 2006-04-15
[QUOTE=Ensnared]
It's more of an issue of the vsftp-daemon not supporting symlinks that are linked to items located outside of the ftp-server root directory, which I'm pretty sure is the case with vsftpd as well as most other ftp-daemons.

I don't think there is any way to make vsftpd support these kinds of symlinks, but I could be wrong. Couldn't find anything about it in the documentation atleast.[/QUOTE]

No. I see the symlink and I can also jump to it with the 'cd' command when im using a linux box. But not with Windows. So according to this, the symlink is actually working, but not from a Windows computer. WEIRD!

How do you usually share files and directories that are located outside the ftp-root-directory for instance /home/ftpuser? I doubt that you would copy all music and pictures to /home/X for each user.

---

### Post by Ensnared on 2006-04-15
[QUOTE=lezz]No. I see the symlink and I can also jump to it with the 'cd' command when im using a linux box.[/QUOTE]
Is this when you're logged in on the linux box with an FTP-client, or when you're logged in on the box with a regular shell? Because there's a huge difference, and from what you wrote it seemed like the symlink is working when logged on to the server with a regular shell, which is quite normal.

Do you log on with the same username and password on FTP both with the client from the computer the server runs on and the Windows computer?

Anyway, if you allow local users to log on to the server they will have access to everything they have access to if they were logged in on the server with a regular shell, cause in those cases the ftp root directory is the same as the system root directory. If it's a separate FTP user with a chroot to his or her home directory however, then it's a different matter entirely. In the first case, the server will normally follow symlinks. In the second, it won't. This is due to security issues more than anything else - if you chroot the user to a dir, it's because you don't want the user to have access to items outside his virtual root, and the server will therefore disallow access to these items also if they are symlinked.

It may be a different matter with hard links, but I've never used those myself so couldn't quite tell you how to try it. You might want to check out [this explanation](http://linuxgazette.net/105/pitcher.html) in any case.

---

### Post by souki on 2006-04-15
the dos/windows client does not understand symlink, it sees symlinks as 0 length files
you can try use an other ftp client or login with your local user account
if you login with a local user account, you will have the same rights, and you will access the /mnt/share directory if your local account has the right to

---

### Post by lezz on 2006-04-15
[QUOTE=Ensnared]Is this when you're logged in on the linux box with an FTP-client, or when you're logged in on the box with a regular shell? Because there's a huge difference, and from what you wrote it seemed like the symlink is working when logged on to the server with a regular shell, which is quite normal.
[/QUOTE]

I logged in on the box with an ftp-client (ftp command), but I did try the latter too tough.

It was like the last poster predicted, it doesnt work with Windows-in-built but FlashFXP could read the symlinks. Great. But the problem is, like you mentioned, that if I dont chroot the user he can jump around between directories in my filesystem. And that isnt really what I had in mind. So the dilemma is, if I dont chroot the user I wont be forced to copy music files i want to share to every users home directory, but if I chroot him, he can't use the symlinks.

Let me ask you again, which method do YOU use to share same files (music, document and so on) in the computer to multiple ftp users?

---

### Post by souki on 2006-04-15
[QUOTE=lezz]Let me ask you again, which method do YOU use to share same files (music, document and so on) in the computer to multiple ftp users?[/QUOTE]
zope : ftp + http + webdav + html management
I'm a lazy guy

---

### Post by lezz on 2006-04-15
[QUOTE=souki]zope : ftp + http + webdav + html management
I'm a lazy guy[/QUOTE]

I meant what ftp structure you used in sharing the files.

---

### Post by dcstar on 2006-04-15
[QUOTE=Ensnared]
.......
It may be a different matter with hard links, but I've never used those myself so couldn't quite tell you how to try it. You might want to check out [this explanation](http://linuxgazette.net/105/pitcher.html) in any case.[/QUOTE]
Best to think of a hard link as another (real) directory entry pointing to the same physical file data (on the same file system), and a soft link as a logical pointer to the original directory entry (which requires special interpretation compared to the hard link) on any accessible file system.

---

### Post by souki on 2006-04-15
[QUOTE=lezz]I meant what ftp structure you used in sharing the files.[/QUOTE]
yes, I understand, but zope is different for this aspect
because it is role oriented and it uses its own meta file system, so I don't need to care mutch about structure, all the work is done when defining roles and users define their own structure

---

### Post by Ensnared on 2006-04-15
I don't run an ftp-server like that and haven't done so in years, but I can tell you how I would do it if I was going to set one up.

I'd make a directory, like /home/ftproot, and make this the chroot dir for all users. I'd then put all the shared stuff in there in appropriate folders, and restrict availability as necessary for the various users if need be. For uploads, I'd make a separate directory where users could only upload stuff, not read, delete or even view the contents. If I'd need separate home-dirs for the users, I'd just make these as subdirectories of the ftproot jail, and again restrict access so only the users were allowed to use their own "home" directories.

I believe I set something like this up using proftpd a very long time ago, but I can't say how to do it - or if it's even possible - with vsftpd. I can't even remember how I did it with proftpd anymore.

If you need each user to have their own separate chroot jail, then I really don't know how to set up files to be available to all users, but if I were going to do it I'd probably first see if it is possible with hard links.

---

### Post by lezz on 2006-04-16
[QUOTE=Ensnared]I don't run an ftp-server like that and haven't done so in years, but I can tell you how I would do it if I was going to set one up.

I'd make a directory, like /home/ftproot, and make this the chroot dir for all users. I'd then put all the shared stuff in there in appropriate folders, and restrict availability as necessary for the various users if need be. For uploads, I'd make a separate directory where users could only upload stuff, not read, delete or even view the contents. If I'd need separate home-dirs for the users, I'd just make these as subdirectories of the ftproot jail, and again restrict access so only the users were allowed to use their own "home" directories.

I believe I set something like this up using proftpd a very long time ago, but I can't say how to do it - or if it's even possible - with vsftpd. I can't even remember how I did it with proftpd anymore.

If you need each user to have their own separate chroot jail, then I really don't know how to set up files to be available to all users, but if I were going to do it I'd probably first see if it is possible with hard links.[/QUOTE]


Ok, I get what you mean. But let's say you wanna share /mnt/music (aka d:), which contains over 50 gb of music, to all your users in the chroot:ed directory /home/ftproot. How do you do then? That's the problem I can't solve.

---

### Post by souki on 2006-04-16
[QUOTE=lezz]Ok, I get what you mean. But let's say you wanna share /mnt/music (aka d:), which contains over 50 gb of music, to all your users in the chroot:ed directory /home/ftproot. How do you do then? That's the problem I can't solve.[/QUOTE]
Why don't you simply mount your partition inside the chroot jail ?
or change your ftproot to the mounted partition ?

---


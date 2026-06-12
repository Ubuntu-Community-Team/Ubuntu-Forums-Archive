---
title: "Users on multiple computers"
date: 2010-07-29
forum: General Help
---

### Post by wolfgangmcq on 2010-07-29
I am trying to convince my school to switch from Windows to Ubuntu. However, I'm not sure how to solve this problem:
 
When you login to a computer, Windows consults a server on the school's network to find out whether username & password are correct. If they are, it logs you in. It also creates two drives which appear in My Computer and refer to folders on a server on the network: the Y:\ drive and the M:\ drive. The Y:\ drive is the same for all students, and contains folders where teachers can put files, etc. for their students. The M:\ drive is the equivalent of the home folder in Unix- you save your files there and they follow you around wherever you login.
 
My question is:
First of all, how would you set up Ubuntu so that it checks the user's login against the logins stored on another server? What software you would need to install, and so on. Second, how would you make the user's home folder follow them around? Also, I believe that Ubuntu has something akin to the Windows Registry. How would you make that follow the users around, too? (That is, if it exists.) Third, how would you make something like the Y:\ drive? I think this is a relatively simple problem, but I know nothing about networking, so I'm not sure.

---

### Post by JustinR on 2010-07-29
> **wolfgangmcq said:**
> I am trying to convince my school to switch from Windows to Ubuntu. However, I'm not sure how to solve this problem:
 
When you login to a computer, Windows consults a server on the school's network to find out whether username & password are correct. If they are, it logs you in. It also creates two drives which appear in My Computer and refer to folders on a server on the network: the Y:\ drive and the M:\ drive. The Y:\ drive is the same for all students, and contains folders where teachers can put files, etc. for their students. The M:\ drive is the equivalent of the home folder in Unix- you save your files there and they follow you around wherever you login.
 
My question is:
First of all, how would you set up Ubuntu so that it checks the user's login against the logins stored on another server? What software you would need to install, and so on. Second, how would you make the user's home folder follow them around? Also, I believe that Ubuntu has something akin to the Windows Registry. How would you make that follow the users around, too? (That is, if it exists.) Third, how would you make something like the Y:\ drive? I think this is a relatively simple problem, but I know nothing about networking, so I'm not sure.

One solution for the login problem is to have user accounts (eg. /home) on a networked drive and use /etc/fstab to to make Ubuntu use that instead.

And again, use /etc/fstab to mount the network drive on boot.

And I'm not sure what you mean my follow the user around.

---

### Post by drdos2006 on 2010-07-29
For mapping network drives on a Ubuntu server, have a look at this HOWTO.
[http://ubuntuforums.org/showthread.php?t=249889&highlight=howto+nfs](http://ubuntuforums.org/showthread.php?t=249889&highlight=howto+nfs)

For setting up a Ubuntu server, have a look at this HOWTO.
> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
Setting up a Linux Server, Start to Finish, using Webmin. By Kevin Elwood

regards

---

### Post by wolfgangmcq on 2010-08-04
By "follow the user around" I mean when they log into one computer, make a change to something, & then log into another computer, the change appears on that one too.
 
Thank you for the suggestions!

---

### Post by JustinR on 2010-08-04
> **wolfgangmcq said:**
> By "follow the user around" I mean when they log into one computer, make a change to something, & then log into another computer, the change appears on that one too.
 
Thank you for the suggestions!

Hi,

So continuing on my first idea, if you put the /home directory on a networked drive and edit /etc/fstab to show this, then I believe this is possible. Also, if you use this method - it will 'follow the user around'.

---

### Post by Zorgoth on 2010-08-04
As far as I am aware of Ubuntu has no registry; amiright?

---

### Post by Zorgoth on 2010-08-04
I have some recommendations.

Do NOT mount the networked drive as /home.

Rather:

in /etc/fstab, mount the networked drive as /media/homedrive

in /etc/gdm/PostLogin/Default:

mount the home directory of the particular user using
```

mount -B /media/homedrive/$LOGIN /home/$LOGIN

```
ONLY if that directory is not mounted by another computer.

Then there is much less danger of different computers interfering with each other and killing a home directory.  Also, the networked hard drive should be hooked up to a server in such a way that 

a) each home directory may only be accessed by one computer at a time - so the server should have a single-threaded process that handles login requests (managed on the client side in /etc/gdm/PostLogin/Default) and ensures (using an if statement in /etc/gdm/PostLogin/Default) that if a user is already logged in, another computer can't log in as that user; this system will have to take crashes into account.  My guess is that networked filesystems can handle a lot of that pretty automatically.

b) if the server goes down, access to all home directories is automatically terminated; that is pretty easy of course

Note that if the mount fails, the user will load into a default session without their home directory.  I think this is a good situation.  It is also a reason not to mount the networked drive as /home directly because otherwise the system would still try to automatically write to /home/user_name, which depending on the setup would, if the networked drive was mounted as /home, either fail to allow any login at all or else result in two copmuters simultaneously using the same ~.

Also, you need to make sure all the computers with th esame hardware have the exact same packages.  You would probably want updates/new packages to be installed only during specified prescheduled times when no one is using the computer, and you would, to make the administrator's life easier, want to have a script or something that automatically installs the same updates for each computer.

One BIG problem with this whole concept is that all the computers using a /home would ideally be using the same hardware I think (someone correct me if I'm wrong)...  Perhaps you would only want to mount certain subdirectories of /home remotely (or perhaps hardlink rather than mount, in the case of files directly in ~)?

---


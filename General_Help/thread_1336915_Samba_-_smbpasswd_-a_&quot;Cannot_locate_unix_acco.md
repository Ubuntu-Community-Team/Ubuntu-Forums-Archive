---
title: "Samba - smbpasswd -a &quot;Cannot locate unix account!&quot;"
date: 2009-11-25
forum: General Help
---

### Post by Roasted on 2009-11-25
I'm dual booting Ubuntu and Kubuntu on the same system to try out KDE land more and more. As a result, I want to mimic my file server services on Ubuntu as best as I can on Kubuntu so there's no major downtime if I choose to reboot. 

All of the users ARE on the system. I'm aware that Samba requires the user to exist on the local system as well as added to the Samba user list in order to function properly. But they are on the system - yet when I run:

jason@Skynet:~$ sudo smbpasswd -a user
Cannot locate Unix account for 'user'!
jason@Skynet:~$

---

### Post by bab1 on 2009-11-25
> **Roasted said:**
> I'm dual booting Ubuntu and Kubuntu on the same system...

Dual booting connotes the use of two (2) separate systems.> 

All of the users ARE on the system. I'm aware that Samba requires the user to exist on the local system as well as added to the Samba user list in order to function properly. But they are on the system - yet when I run:

jason@Skynet:~$ sudo smbpasswd -a user
Cannot locate Unix account for 'user'!
jason@Skynet:~$

If you are dual booting I'll bet you'll find that you have 2 passwd and 2 shadow files.  They user may even have the same UID/GID and /home directory.

The local machine is not just a physical thing.  A ***host ***is the running OS and the hardware.

---

### Post by Roasted on 2009-11-25
Hm, I'm not entirely sure I follow, but I'll just expand here on what I know and how my system is set up:

20gb Ubuntu
360gb /home/jason
20gb Kubuntu

All users that were added to Kubuntu also have the same UID as they did in Ubuntu. Everything in Kubuntu matches up. Permissions look fine, group assignment looks fine, etc.

I'm not sure why anything in Ubuntu would effect or prevent me from doing this same setup in Kubuntu, because the only thing shared by the two operating systems is /home/jason. They each have their own independent root directory.

---

### Post by bab1 on 2009-11-25
> **Roasted said:**
> Hm, I'm not entirely sure I follow, but I'll just expand here on what I know and how my system is set up:

20gb Ubuntu
360gb /home/jason
20gb Kubuntu

All users that were added to Kubuntu also have the same UID as they did in Ubuntu. Everything in Kubuntu matches up. Permissions look fine, group assignment looks fine, etc.

I'm not sure why anything in Ubuntu would effect or prevent me from doing this same setup in Kubuntu, because the only thing shared by the two operating systems is /home/jason. They each have their own independent root directory.

Well...

Lets use your terms.  A system consists of the hardware and the OS; right?  I this case you have 2 systems (these are known as hosts it the IT world).

That you use the same file system for the /home directory and the same permissions on both hosts is irrelevant to your problem.  You have 2 kernels, and therefore 2 authentication systems.  Thus, you have 2 sets of users.

The host Skynet (I hope you used 2 different hostnames) can't find the user your defined with your command ```
sudo smbpasswd -a user
```

How did you confirm that this user existed on this host?

I would use this```
getent passwd|grep user
```This returns the following for the user skeezix```
skeezix:x:1010:1002:Skeezix The Kid,,,,:/home/skeezix:/bin/bash
```

To see the information on the GID and what groups the user skeezix is in you can use ```
getent group|grep skeezix
```

Try this when booting each instance of the OS (Kubuntu and Ubuntu) and see if there is a difference.

---

### Post by Roasted on 2009-11-25
Or - can I just delete the users off of Ubuntu/Samba and add them to Kubuntu/Samba? I believe I'll begin to use Kubuntu full time so I really don't need both instances of the service running.

---

### Post by bab1 on 2009-11-25
> **Roasted said:**
> Or - can I just delete the users off of Ubuntu/Samba and add them to Kubuntu/Samba? I believe I'll begin to use Kubuntu full time so I really don't need both instances of the service running.

What do you mean by that?  Why do you have to delete users from one OS to add to the other?  Only one OS is running at any one time.  

What makes you think there are 2 **_unrelated_**, separate instances of smbd are running?  Samba normally has 2 copies of smbd daemon running while listening on an idle host.

---

### Post by Roasted on 2009-11-26
I don't know. I didn't think they were related at all, unless some trace of the samba path was left in my home directory which gets mounted on Kubuntu as well.

---

### Post by bab1 on 2009-11-26
> **Roasted said:**
> I don't know. I didn't think they were related at all, unless some trace of the samba path was left in my home directory which gets mounted on Kubuntu as well.

You don't know?  Are you just speculating or guessing at possible notions?  What better inducement could there be for someone to respond with RTFM?

A better grounding in how and why Samba works as it does is needed on your part.  May I direct you to [_http://samba.org/samba/docs/_]("http://samba.org/samba/docs/").  All will be revealed.

---

### Post by Roasted on 2009-11-26
I've used Samba for several years. I've read many manuals and used it with flying success. You were confusing me because I was getting the vibe there WAS some sort of connection between the two operating systems existing on the same system.

Every "manual" you speak to RTF about says the same thing.

Add user to Linux.
sudo smbpasswd -a user
Type PW, done, good to go.

So when I follow "TFM" and it barfs out that error, I have no idea where to go from there considering THAT is the process that always worked.

---

### Post by bab1 on 2009-11-26
> **Roasted said:**
> I've used Samba for several years. I've read many manuals and used it with flying success. 

I understand that.  One can be user of a tool such as Samba successfully without understanding the underlying processes.  As an example, most people successfully use a car every day, but have not a clue of what to do if it malfunctions.
> 

You were confusing me because I was getting the vibe there WAS some sort of connection between the two operating systems existing on the same system.
Just the opposite  There is no connection between the 2 OS's.  The file systems where the user stores their data can be the same. > 

Every "manual" you speak to RTF about says the same thing.

Add user to Linux.
sudo smbpasswd -a user
Type PW, done, good to go.

Unless there is a problem.> 

So when I follow "TFM" and it barfs out that error, I have no idea where to go from there considering THAT is the process that always worked.

An now we are down to the core of the issue.  Do you just want the answer to your problem, or the knowledge of what to do when something on the system breaks?

The howto's will give you the procedures on how to setup Samba, but little knowledge of how Samba really works.

If *just fix it *is what you want, then you need to answer questions asked (i.e. How did you confirm that this user existed on this host?).  To understand the underlying processes you need to read as much as you can on Samba itself.  Most of which, is pretty dry reading.  The writer most of the time assumes you have a CS background.

---

### Post by Roasted on 2009-11-27
No idea what the problem was, but I redid Kubuntu because it looked like I had a broken install since I would right click on certain items and KDE would just flat out crash. I redid Kubuntu, added local users, then added them to Samba - all worked fine.

So, everything is good to go now. Thanks!

---


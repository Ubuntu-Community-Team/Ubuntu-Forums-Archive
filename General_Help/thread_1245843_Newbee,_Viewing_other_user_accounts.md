---
title: "Newbee, Viewing other user accounts?"
date: 2009-08-21
forum: General Help
---

### Post by dodobird on 2009-08-21
I have done a lot of Google, but don't seem to find the answer to this question. I bought a storage units contents a week ago that had a lot of computers and parts and music equipment. One of the computers is a Acer Aspire 4720z that has Ubuntu on it, but was user:password protected.

From reading on the web I was able to create my own account from, Root I think? 

I have never used Linux so I'm unknown to it's use, but I did create the account from a command line and am able to get into it.

It seems to have a 120GB drive and I can see that it has 98.8 GB free space, so I'm thinking there must be data on it under 1 or more user accounts.

Now with Windows you can "see" other user accounts on a system, but I don't know how to do that with Linux, and as a windows Admin you can change passwords. 

Can you "see" other accounts in Linux and change the passwords? 

Not knowing what is on the system, it would be nice to know what kind of files are stored and be able to delete if there not of any use.

There was a lot of music stuff, mixer boards, mikes, amps, that kind of stuff in the storage container so I'm thinking there mite be some good mix creations or usable software on the system, so I'd like to look before just reformatting.

I also don't know what I'd have to do to reformat the drive for windows if it comes to that, I don't have a copy of Ubuntu or know how to use it, but I'm willing to give it a try.

Could any of you help me with finding out whats on this system or would it just be best to reformat and install something new.

FYI: it is Ubuntu 8.04 the Hardy Heron April 2008 release

Thanks for any help you can offer.

---

### Post by zvacet on 2009-08-21
To see if there are other accounts go to places>computer>filesystem>home.If you find other users and want to change password boot in recovery mode ( you will see it when comp start to boot) and type 

```
password username
```

enter new password and hit enter.After that type 

```
shutdown -r now
```

That will reboot comp.

---

### Post by bchurchill on 2009-08-21
In general you can.  The owner of files has the ability to set permissions for each file or folder that may allow other people to read or write.  If you're browsing and you get 'permission denied' then you'll need to use sudo to run a process as root.  A good way to do this is

```
gksudo nautilus &
```

if you're in GNOME... or something similar with konqueror in KDE.

---


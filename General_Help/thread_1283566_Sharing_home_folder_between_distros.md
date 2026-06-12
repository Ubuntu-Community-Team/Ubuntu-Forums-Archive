---
title: "Sharing /home folder between distros"
date: 2009-10-05
forum: General Help
---

### Post by Soapy.Illusions on 2009-10-05
If I will be installing multiple distros (arch and ubuntu in this case) is it possible for them to each have their own separate / directory but share /home so my music is accessible on both without having to mount it?

---

### Post by Giblet5 on 2009-10-05
I use a common /home filesystem for Ubuntu, Suse, CentOS, and RedHat.

All of them have Gnome and KDE support.

I use a 1.5TB drive for /home.

The look/feel is the same for all OS releases, which can be confusing, so I have gimp'ed background images that identify what I'm running.

---

### Post by SuperSonic4 on 2009-10-05
Yeah, it's fine although it could get confusing

---

### Post by Soapy.Illusions on 2009-10-05
> **SuperSonic4 said:**
> Yeah, it's fine although it could get confusing

How could it be confusing, if I will have arch running Kde and ubuntu running gnome?

---

### Post by CatKiller on 2009-10-05
The one potential downside that I can see is using the same application in each distro with different versions which aren't configuration-compatible. It does happen (although I have no idea how often) so it might be something to look out for.

---

### Post by louieb on 2009-10-05
Problem 1
In Linux a user has 2 ids one is the User name the other is his User id a number 
to see what i mean 
```
ls -la
ls -ln
```see how the user name has been replace by a number. If they don't match then there can be permission problems.  

Problem 2
Same program different version.+ Configuration file format changed. Can and probably will give unpredictable results.  

No problem.
Create a separate data partition for your music and videos.  Lot easier to mount it than fighting problems that could rise from problems 1 & 2.

---

### Post by dcstar on 2009-10-06
> **Soapy.Illusions said:**
> If I will be installing multiple distros (arch and ubuntu in this case) is it possible for them to each have their own separate / directory but share /home so my music is accessible on both without having to mount it?

This can cause issues if you are using different versions of Gnome (or whatever) in the different distros.

Newer versions of Gnome (and other apps) can change config settings/data structures that then do not work correctly when an older version is used again.

---

### Post by frazerr on 2009-10-06
how do you do it?

i tried making symboIic Iinks from my current distos home foIder to my oId drives /home/me foIder

some things worked  - but others did not

any hints of a better way to do it?

---


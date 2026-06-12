---
title: "nfs access denied message in Maverick"
date: 2010-11-07
forum: General Help
---

### Post by xeddog on 2010-11-07
I have been reading a lot of posts here today trying to resolve an issue I was having with nfs.  Almost all of the posts I read just seemed to stop with no resolution shown, or the resolution shown did not work for me so I never could get an answer.  But I finally found it and maybe someone else can find this useful.

I recently installed 64-bit Ubuntu Maverick.  This was a clean install as opposed to an upgrade.  Since the install I have been having a heck of a time getting a remote filesystem mounted via nfs.  The file system I have been trying to mount is located on my HDX-1000 media server.  This machine is running a  flavor a linux as it's operating system, and I have been using it for about 2 years now.  I have been able to mount it's filesystem on all other machine in my house which include Windows 7, and a couple of earlier versions of Ubuntu linux.  But I just could not get it to mount using Maverick.  I kept getting the "mount.nfs access denied by server while mounting ..." message.

Finally, I found a list of all the different parameters that can be specified on an entry in the fstab.  The one that worked for me was simply to change the fstab entry from this:

```
HDX-Server1:/share	/media/HDX-Server1 nfs rw,rsize=8192,wsize=8192,intr
```

to this:
```
HDX-Server1:/share	/media/HDX-Server1 nfs rw,rsize=8192,wsize=8192,intr[COLOR="Red"],nfsvers=3[/COLOR] 
```

That is one more little gremlin down.  Just 34,689 to go.  :lolflag:

Wayne

---

### Post by mastapat11 on 2010-11-19
Yay!! This is just what i needed. thanks guy :D

Now, with props out the way, let's get to the whining -->

WHY DOES THIS WORK??? 
in */etc/exports* it expressly states:

> # Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
 Which doesn't exactly make sense.  what is [COLOR="Red"]gss[/COLOR]? what is [COLOR="red"]krb5i[/COLOR]?

What's written in my ***/etc/exports*** is:

> /home/xxx		10.1.0.0/24(rw,no_root_squash,sync,subtree_check)
/media/BACKUP		10.1.0.0/24(rw,no_root_squash,sync,subtree_check)

I'm guessing/assuming this must be [SIZE="3"]v3[/SIZE] format??
Except, ***/home/xxx*** works for me w/o "nfsvers=3" parameter, but ***/media/BACKUP*** doesn't.  
Matter of fact, everything i export from ***/media*** requires this extra parameter.  WTF!!!???
I didn't need this for Hardy or Lucid.  Is Maverick retarded or just me (or both)? 

4+ yrs of using NFS and i still don't understand it and just fumble around w/ it till something works.

Sincerely, 
Tired, irritated, & frustrated!

---

### Post by fragos on 2010-11-19
I've just been using the (rw) parameter in /etc/exportfs for a number of Ubuntu releases and it's always worked for me.

---


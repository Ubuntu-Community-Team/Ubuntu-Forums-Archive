---
title: "davfs2 Mounting Error"
date: 2010-11-30
forum: General Help
---

### Post by JaredNJames on 2010-11-30
Hi,

I use Humyo for online storage and mount it through davfs2.

Up until a few weeks ago it was working perfectly.  I could mount a folder, upload/download files and had no errors.

Recently, everytime I try to mount with davfs2 to Humyo, I get the following error:

```
/sbin/mount.davfs: Mounting failed.
SSL handshake failed: SSL alert received: Error in protocol version
```

I have no idea why it would suddenly stop working.

I would appreciate any help you could provide.

Jared James

---

### Post by Tyl29 on 2010-12-01
Hy,


I'm a new user of Humyo premium. I'm using Fedora 14 and I'm trying to mount the folder with davfs or cadaver but I got the same error message.
I used this [How to]("http://patrik.cqure.net/wordpress/2009/09/27/backing-your-nas-to-humyo/") to configure the connexion.



With davfs:
```
mount -t davfs [https://dav.humyo.com]("https://dav.humyo.com/") /media/humyo/
/sbin/mount.davfs: Mounting failed.
SSL handshake failed: SSL alert received: Error in protocol version
```With cadaver:
```
Could not open collection:
SSL handshake failed: SSL alert received: Error in protocol version
```Strangely, if I use nautilus using "connect to a server", it works, I can use drag and drop to copy files but I can't use it with command line.


I would be greatly interested in any help about this subject.

Sorry for my bad english...

Yann

---

### Post by JaredNJames on 2010-12-04
Bump

---

### Post by Tyl29 on 2010-12-04
I found [this ]("https://projects.forum.nokia.com/home/wiki/KnownIssues")in a Nokia forum.

It seems to me it describe a similar problem.
There are some explanation on how to correct the gnutls' bug for svn and git but nothing about davfs.

Maybe we should just uninstall davfs and recompil it with some parameters like --with-openssl --with-expat and --with-curl ?

This is just an idea but it's far too complicated for me.
Anybody cool help?

Thanks by advance.

---

### Post by JaredNJames on 2010-12-04
I actually found the same thing.

It's too complicated for me too.

I ran it and got pretty far, but then it started throwing errors and I was lost.

Perhaps someone else who understands it can assist us.

---

### Post by Tyl29 on 2010-12-04
I believe I got the same result...

Hope someone could help too.

---

### Post by Tyl29 on 2010-12-08
Up please.

---

### Post by JaredNJames on 2010-12-08
I'm curious if the problem is with Humyo or all webdav mounting on ubuntu.

Humyo was recently taken over and there have been quite a few changes to the site design.  I'm wondering if they've changed something on their end.

I'm going to send them an email tomorrow about it.

---

### Post by JaredNJames on 2010-12-08
I've just had a bunch of SSL updates on Ubuntu 10.10, I'm installing them now and will try humyo again and report back in about ten minutes.

---

### Post by JaredNJames on 2010-12-08
Nope. didn't work.

---

### Post by JaredNJames on 2010-12-08
Fantastic news, I've fixed it myself.

> **Tyl29 said:**
> ```
mount -t davfs [https://dav.humyo.com]("https://dav.humyo.com/") /media/humyo/
```

I decided to try without SSL encryption.

So your new mount script looks like this:

```
mount -t davfs [http://dav.humyo.com]("https://dav.humyo.com/") /media/humyo/
```(Just removed the s from https.)

If you've saved the credentials in the secrets file you'll need to do the same there.

Once done, the folder will mount and you will be able to use it again.

---

### Post by Tyl29 on 2010-12-09
Congratulations!!!!

It confirms there is a problem with SSL encryption.
I assume the exchange with Humyo won't be as secure as with SSL but I am not the CIA and I believe my files don't worth to be spyed.

Maybe an update in Ubuntu (or Fedora for me) will correct this issue

Thanks very much.

Yann

---

### Post by JaredNJames on 2010-12-09
Well I don't really care too much about the encryption either.  Not like I have anything worthwhile.

I had the problem with 10.04 as well just before I updated to 10.10, so I think it is with the SSL itself.

Problem is, I don't know if it is with Humyo or my own SSL.  Like I said, Humyo as recently been taken over that is when the problems occurred.

I don't have another service to test the SSL with, but may have a look if I get time.  That will tell me if it is Humyo or not.

---

### Post by Tyl29 on 2011-01-08
Hy!

I reported the [bug ]("https://bugzilla.redhat.com/show_bug.cgi?id=663660")to the RedHat community (I'm a Fedora user) and I had an answer.

It seems, it's possible to configure fusedav to use an other version of ssl.
Now I am trying to figure out how to apply this solution.

If someone could help, I would greately appreciate.

Thanks by advance.

Yann

---

### Post by Tyl29 on 2011-01-11
Hi,

I asked for more information on how to apply the changes and here is the answer:
> Sorry, I haven't worked out how to do it on Fedora 14 and can't give
specific instructions.

On Debian or Ubuntu you can use my fusedav binaries (32- and 64-bit
versions).

Download:
$ wget -O fusedav '[https://safesync.com/LMFdGRJZ/fusedav-32?a=uAm4eOKwL-g](https://safesync.com/LMFdGRJZ/fusedav-32?a=uAm4eOKwL-g)'
$ # or 64-bit: [https://safesync.com/LMFdGRJZ/fusedav-64?a=zR5FgA8mmKo](https://safesync.com/LMFdGRJZ/fusedav-64?a=zR5FgA8mmKo)
$ chmod 755 fusedav
$ sudo aptitude install fuse-utils libfuse2 libneon27

Run:
$ ./fusedav [https://dav.trendmicro.safesync.com/](https://dav.trendmicro.safesync.com/) /media/safesync

I can access my files in /media/safesync.It should work out of the box for Ubuntu users.
Hope this can help.

Thanks again to [EMAIL="stefanha@linux.vnet.ibm.com"] [/EMAIL]Stefan Hajnoczi who provides those information.[EMAIL="stefanha@linux.vnet.ibm.com"]
[/EMAIL]

---


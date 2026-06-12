---
title: "Proxy problems in Kubuntu 12.04"
date: 2012-08-06
forum: General Help
---

### Post by pwabrahams on 2012-08-06
I have Kubuntu 12.04 recently installed and I've encountered two quite different problems that may have the same cause: difficulty with proxy connections.

1. I was trying to use the line

```
gpg --keyserver pgpkeys.mit.edu --recv-key  A8AA1FAA3F055C03
```

But when I tried it, I got this:

```
gpg: requesting key 3F055C03 from hkp server pgpkeys.mit.edu
gpgkeys: HTTP fetch error 6: Couldn't resolve host 'pgpkeys.mit.edu'
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

```

From what I read on the Net, this is caused by a problem with a proxy server.

2. When I try to start up the Dropbox daemon, I get this:

```
Error: Trouble connecting to Dropbox servers. Maybe your internet connection is down, or you need to set your http_proxy environment variable
The installation of Dropbox failed.

```

I'm not using a proxy server.  Since other folks have reported both of these problems, I think there's a system problem.  Is there at least a workaround?

---

### Post by cortman on 2012-08-06
> **pwabrahams said:**
> I have Kubuntu 12.04 recently installed and I've encountered two quite different problems that may have the same cause: difficulty with proxy connections.

1. I was trying to use the line

```
gpg --keyserver pgpkeys.mit.edu --recv-key  A8AA1FAA3F055C03
```But when I tried it, I got this:

```
gpg: requesting key 3F055C03 from hkp server pgpkeys.mit.edu
gpgkeys: HTTP fetch error 6: Couldn't resolve host 'pgpkeys.mit.edu'
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

```From what I read on the Net, this is caused by a problem with a proxy server.

2. When I try to start up the Dropbox daemon, I get this:

```
Error: Trouble connecting to Dropbox servers. Maybe your internet connection is down, or you need to set your http_proxy environment variable
The installation of Dropbox failed.

```I'm not using a proxy server.  Since other folks have reported both of these problems, I think there's a system problem.  Is there at least a workaround?

Odd. Check the specified places [here]("http://forum.kde.org/viewtopic.php?f=18&t=80506") to make sure a proxy wasn't accidentally set.
Are you using a firewall also? Similar situation.

---

### Post by pwabrahams on 2012-08-07
Very odd indeed.  System Settings indicates No Proxy.  I'm not using a firewall as far as I know.  Moreover, these problems appeared only after the upgrade from 11.10 to 12.04.

The Dropbox problem is the subject of an older thread on the Dropbox forum,[http://forums.dropbox.com/topic.php?id=59808]("http://forums.dropbox.com/topic.php?id=59808") but no resolution is indicated.

---

### Post by cortman on 2012-08-07
If this is the case, I'd say check with your ISP and make sure they aren't the cause of the issue.

---

### Post by pwabrahams on 2012-08-07
The problem with Dropbox only started with the 11.10-12.04 upgrade.  Furthermore, a number of other people have had the Dropbox problem.  So it seems unlikely that the ISP is the source of the problem, since I've had no other problems with them.  And I wouldn't know what to ask them, anyway.

I've also asked about this on the Dropbox forum, but so far have not had any responses.

---

### Post by cortman on 2012-08-07
Hm.
With that many people having problems with Dropbox, it looks like a bug to me, in which case the proper procedure is to report it.

Honestly not sure about the other; I'll have to research it a bit.

---

### Post by pwabrahams on 2012-09-02
I discovered that if I replace **pgpkeys.mit.edu** by its actual IP address, the key retrieval works correctly.  So I'm pretty sure that proxy problems have nothing to do with the difficulty.  But I still don't know why the IP address retrieval fails.

---


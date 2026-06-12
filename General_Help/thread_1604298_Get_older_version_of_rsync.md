---
title: "Get older version of rsync"
date: 2010-10-23
forum: General Help
---

### Post by skinns on 2010-10-23
Hey,

I'm trying to sync a folder from a remote server to my computer, when I try to connect with rsync I'm prompted for a password, then get the following error,

protocol version mismatch -- is your shell clean?
(see the rsync man page for an explanation)
rsync error: protocol incompatibility (code 2) at compat.c(173) [Receiver=3.0.7]

I'm thinking (and please correct me if I'm wrong here) this is because I'm have rsync version 3.0.7 on my computer and the server has version 2.6.8.

I can't do anything about the server's version, so how do I downgrade rsync on my computer to version 2.6.8? Also, is doing this a really bad idea?

Thanks

---

### Post by marshmallow1304 on 2010-10-23
No, that's not the problem.

[QUOTE="man rsync"]rsync occasionally produces error messages that may seem a little cryptic. The one that seems to cause the most confusion is "protocol version mismatch — is your shell clean?".

This message is usually caused by your startup scripts or remote shell facility producing unwanted garbage on the stream that rsync is using for its transport. The way to diagnose this problem is to run your remote shell like this:

```
ssh remotehost /bin/true > out.dat
```

then  look at out.dat. If everything is working correctly then out.dat should be a zero length file. If you are getting the above error from rsync then you will probably find that out.dat contains some text or data. Look at the contents and try to work out what is producing it. The most common cause is incorrectly configured shell startup scripts  (such  as .cshrc or .profile) that contain output statements for non-interactive logins.[/QUOTE]

---

### Post by skinns on 2010-10-23
Turns out I don't have shell access on the server, so ends that dream. Thank for the help!

---


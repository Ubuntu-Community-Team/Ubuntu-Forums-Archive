---
title: "libnss_winbind: 32-bit / 64 bit"
date: 2010-06-23
forum: General Help
---

### Post by gmoore777 on 2010-06-23
we are using LucidLynx Linux, 64-bit,
with ActiveDirectory accounts via samba/winbind 64-bit.

I have 2 separate 32-bit applications:
   IBM MQ Toolkit (32-bit java-based) and 
   Acrobat Reader (32-bit)
that fail to run.

They throw different errors: 
   JVMSHRC155E Error copying username into cache name
and
    getpwuid_r(): failed due to unknown user id (6090)

I can solve both issues by adding an entry in the /etc/passwd
file for that ActiveDirectory user running the application.
(of course that is a hack, that I'd rather not do)

So I am surmising that the real problem/solution is that 
these 32-bit applications would work if I installed 32-bit 
samba and winbind so that a 32-bit libnss_winbind.so would 
be around to assist in the NSS (Name Service Switch)
request for a username if given a userid.
But I don't want to have 32-bit and 64-bit samba/winbind
installed on one machine as I can imagine that would stir
up more issues.

Another solution would be to pray that both applications
have a 64-bit version to install. (that's not going to happen)

I've Googled one solution that installing and running NSCD
would help, but it is known that one is to NOT run nscd
on a system with winbind is running.

So is there a more slicker solution to what I think is
a missing 32-bit NSS situation?

---

### Post by gmoore777 on 2011-04-05
So it seems that Oracle 32-bit client 11.2.0.2 has changed
such that this error occurs for us:

    C  [libclntsh.so.11.1+0x77a849]  skgpgetinfo+0x9d

(works fine for 10.2.0 and 11.2.0.1 client)

So there is a slicker fix for this rather than adding an entry
in the /etc/passwd file as I mentioned above.

Just get your hands on a 32-bit version of libnss_winbind.so.2
and shove it in /usr/lib32.

I got the package from here:
   [http://packages.ubuntu.com/lucid/i386/winbind/download](http://packages.ubuntu.com/lucid/i386/winbind/download)

extracted the package:
   dpkg -x winbind_3.4.7~dfsg-1ubuntu3.4_i386.deb

and copied just the libnss_winbind.so.2 to /usr/lib32.

All done.(no reboot or linking is needed)
This fix solves the same problem: an application, is 
holding a Unix id and wants to get the user's name, or
vice-versa and
needs to get this information from either /etc/passwd or from 
winbind. It doesn't care which.

This fix works for acroread.
(haven't tested it for IBM MQ software, yet. My peers will do
that tomorrow-ish)

This bug 
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/694953](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/694953)
may address this issue in the future for some Ubuntu versions.

---

### Post by gmoore777 on 2011-04-07
Note to self: the above didn't help with my MQ issue. We have an entry in the /etc/passwd, for another reason.

---


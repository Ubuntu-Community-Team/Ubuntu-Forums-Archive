---
title: "Ubuntu, AWS Ubuntu and FileZilla"
date: 2011-12-25
forum: General Help
---

### Post by OldManRiver on 2011-12-25
All,

Having some interesting issues.  A client selected AWS (Amazon Web Services) as host for a project.  We installed the Ubuntu 10.04 i386 server instance there.  We have to upload and work the files but keep running into some problems.

1. AWS does not have a direct set up for FTP, so have to SSH to it and set up everything.
2. FileZilla works only under the following circumstances, due to the way it handles ssh authentication files:
   a. Computer must be Winduhs,
   b. Putty must be open and logged into AWS site first,
then and only then will FZ work as it uses the Putty .ppk file and it's back-end link to putty to authenticate the connection.

I've read everything I can get my hands on and since we are Linux house, not having FileZilla to have it's own authentication handling and then having Putty and PuttyGen to not set up right on Ubuntu, which they do not work as advertised at all, really makes for a difficult time trying to do a very simple job.

If you know some tricks on how to get the Putty to install and work from withing FileZilla, as it has to for AWS, then please chime in and let me know, so I can fix this crazy mess.

Thanks!

OMR

---

### Post by Habitual on 2011-12-26
OMR:

have you tried using FZ's key-management to 'import' the key.ppk?

Filzilla > Edit > Settings > SFTP > Add Keyfile.

---

### Post by OldManRiver on 2012-04-02
All,

Marked this solved as we got off that horrible AWS platform and will never go back for any reason.

Cheers!

OMR

---


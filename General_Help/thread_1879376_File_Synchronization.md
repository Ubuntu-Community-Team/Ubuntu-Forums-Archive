---
title: "File Synchronization"
date: 2011-11-11
forum: General Help
---

### Post by SyntheticShield on 2011-11-11
I love Ubuntu One primarily because of the space they give you which is significantly more than anything else out there.  However, after reading some information on options such as ownCloud, Tonido and the like it got me to thinking.

I have a website with tons and tons of space.  More than I could use anytime soon in the foreseeable future anyway.  I know, obviously, that I could use Filezilla to move files to and from there but can I do more?  Is there a way to actually synchronize the files between my web server (I would create a separate folder area to store my personal files) and the laptops I have?

Ive looked at Unison, SparkleShare and have not been able to get anything to work.  I know I could use something like FreeNAS to set up a file share at home but Id rather just upload file to my own web server and then have some kind of installation that would check at start up and then check at a certain (preferably defined) interval for any changes in the files and synchronize them.

So can this be done?  Has anyone done it and if so can you help get me started?

Thanks in advance.

---

### Post by blueridgedog on 2011-11-11
Can you access your web server with ssh?  If so, then you can use rsync over ssh.

---

### Post by SyntheticShield on 2011-11-11
If I can, I have not figured out how.  I know that does not speak very well of my skills, but as best I can tell I cannot.

---

### Post by blueridgedog on 2011-11-11
I assume you are paying a commercial hosting firm then?  

This page (if you read all of the posts) lists a variety of ways to synchronize to an HTTP server.

[http://serverfault.com/questions/24622/how-to-use-rsync-over-ftp](http://serverfault.com/questions/24622/how-to-use-rsync-over-ftp)

---

### Post by bootedguy on 2011-11-11
If you are using a shared hosting plan (the kind that cost $5 to $10 per mo), you might want to check their "terms of service."  Most do not allow using these for backup.

---


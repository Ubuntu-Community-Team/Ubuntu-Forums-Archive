---
title: "sshfs mount problem"
date: 2012-08-23
forum: General Help
---

### Post by SemperVI on 2012-08-23
Hello,
I am an application developer who is fairly new to Linux. In any case - I am trying to mount an sftp location. After reviewing many of the outstanding articles posted here I feel like I am close but perhaps I am missing the obvious.

After running the following command, the cursor drops to the next line w/o a prompt and simply blinks. Ultimately I would like to establish this mount in fstab but I can't even get my system to mount my network directory.

```
me@work:~$ sshfs username@hostname:/the/path/to/folder /mnt/hostname/outbound
{cursor blinks here forever}
```

If I go to the share I created in /mnt/hostname/ - I can't even traverse into outbound - which does exist. The window just works as if it can't resolve any further sub-directories. e.g. outbound 

I should probably mention the server cert is not trusted. (dev environment). Would this cause the problem? 

It should be noted I have connected to this remote host with a sftp client and accepted the untrusted cert.

Am I missing something? I would be grateful for any suggestions you might have.

---

### Post by surajkumarr on 2012-11-25
This could happen due to a few reasons.
1. ping the host and verify the connectivity
2. make sure both the paths are correct and the folders mentioned exists.
3. make sure the username exists in the host and have proper privilages on the host folder

If all the above mentioned criteria meets. Check whether ssh works. type ssh username@hostname.
if you are getting a "connection reset by peer" error. check your ~/.ssh/knownhosts.  after taking a backup of 'knownhosts' file rename or delete it. Now try again

---


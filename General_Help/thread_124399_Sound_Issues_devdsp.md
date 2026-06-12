---
title: "Sound Issues: /dev/dsp"
date: 2006-02-01
forum: General Help
---

### Post by jordanm on 2006-02-01
In the past chmodding /dev/dsp to 666 always fixed my sound issues on ubuntu 5.10. After reinstalling, today I cant seem to get it to stick though. I try chmod 666 /dev/dsp as root. After, when I ls -l /dev/dsp it shows the correct permissions of crw-rw-rw-. When I reboot however, the permissions get reset to the original and sound continues not to work. Ive tried this multiple times yet every time I reboot the permissions get reset.

Any suggestions?

Thanks, jordan

---

### Post by ebash on 2006-02-05
It seems like if your user doesn't belong to the 'audio' group.
To find out to which groups you belong use the command:
groups

See if 'audio' is listed there.

Now, perform the command: 
ls -al /dev/dsp

I get the following results (I am runnning Dapper):
crw-rw---- 1 root audio 14, 3 2006-02-05 10:41 /dev/dsp

See the 4th column ('audio')? It's the group that is allowed to use the device.
Add your self into the same group and everything should work.
Note, in order to apply the changes you must logout and login again.

To add your self to the group audio you can use the 'System' -> 'Administration' -> 'Users and Groups' dialog.
Another way is to edit the file /etc/group

---


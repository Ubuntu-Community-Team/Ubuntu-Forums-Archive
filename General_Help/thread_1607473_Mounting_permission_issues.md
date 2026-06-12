---
title: "Mounting permission issues"
date: 2010-10-27
forum: General Help
---

### Post by saitoh on 2010-10-27
Hey guys,

Thanks in advance for any help.

So I have want to have a shared folder mounted on startup and I put the following in my fstab:
```

VMShare /media/VMShare vboxsf defaults,gid=1001,dmask=002 0 0

```

where gid 1001 corresponds to the virtualshare group.

When I boot up the permissions are as follows(from ls -l):
```

drwxr-xr-x  1 root virtualshare   68 2010-10-27 15:45 VMShare/

```

So I'm curious why it's group permissions aren't the same as owner?
In the fstab I put dmask=002 which should lead to rwxrwxr-x so basically full permissions for owner and group and read/execute for public. However thats not what I'm getting. Also once I get this working correctly am I going to have an issue if the virtualshare group isn't a users primary group? On some older unix servers I ran into this issue, hopefully it won't matter as long as the user in in the group.

Thanks

---

### Post by saitoh on 2010-10-29
bump

---

### Post by saitoh on 2010-11-02
Ubuntu Forums fail, again.

---

### Post by saitoh on 2010-11-04
So I finally found some time to go back and take a look at this issue and it turns out it results from file permissions on the host os. If you do this on windows (I know nothing about windows file permissions that supposedly exist on server editions, I tested this out on xp and seven professional editions) it isn't an issue. On a Windows Host whatever you set the shared folder to in your fstab is what the shared folders permissions are. However, on unix based hosts the permissions that you assign the shared folder in the host override the mounting permissions the guest assigns the shared folder. Simply doing chmod -R 775 which on the shared folder via the host OS gave the correct permissions in the guest.

I would also like to say that setting the permissions with fstab in the guest is not completely pointless. You can control the permissions and set them to an equal or lesser value than what the host gives. For example if the host permission for a shared folder is 770. You can have fstab mount it and give the guest any permission you like for owner and group, but nothing will change for public because it was given no permissions what so ever in the host.

---


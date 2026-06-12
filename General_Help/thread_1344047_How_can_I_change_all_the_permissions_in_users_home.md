---
title: "How can I change all the permissions in users home directory"
date: 2009-12-02
forum: General Help
---

### Post by utherpendragonfly on 2009-12-02
I have added another user account for my wife after installing 9.04. Then I copied her files from backup to new home folder. Most of the permissions are now root. Is there a terminal command to change all permissions on the home folder back to her account?

---

### Post by endBc on 2009-12-02
```
sudo chown -R user:group /home/user

```Change the username and group according to whom you want to give the permissions and it should solve your problem.

---

### Post by utherpendragonfly on 2009-12-02
> **endBc said:**
> ```
sudo chown -R user:group /home/user

```Change the username and group according to whom you want to give the permissions and it should solve your problem.

Thanks for the reply. The user name is steph and the group is also steph Here is what I did:

davey@davey-desktop ~ $ sudo chown -R steph:steph /home/steph
[sudo] password for davey: 
chown: cannot access `/home/steph/.gvfs': Permission denied

I don't know what .gvfs is or why is permission denied?

---

### Post by endBc on 2009-12-02
```
umount /home/steph/.gvfs && rm -r /home/steph/.gvfs

```

Let us know if there's anything else you need help with.

---

### Post by utherpendragonfly on 2009-12-02
Thank you very much! That did it!

---


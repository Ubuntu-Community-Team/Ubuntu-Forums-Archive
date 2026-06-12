---
title: "Fresh Install / Home Folder Copy / Can not login"
date: 2012-08-10
forum: General Help
---

### Post by krustenBrot on 2012-08-10
Hey everyone,
I just did a fresh install of 12.04, after that still being on the USB live system i copied over my previously backed up home folder. I did that before (*using the same username during installation!*) and i did not have any problems. However, now when i try to log into my user account, lightdm fades to black, and then just comes up again.

My guess is there is either something wrong with a config file i copied, or with the user id, which prevents access to the config files in home and therefore causes a crash. 

Any idea how to fix that?

---

### Post by krustenBrot on 2012-08-10
Quick update: I just switched to console logged in as my main user and tried to **cd **into a *home directory* and it says: **Permission Denied**. Soo something definitely went wrong during my backup attempt.

**edit:  ***ls -l  *shows that my whole home folder was copied as root. ... someone was not paying attention here. -.- Is there a simple way of giving back the permission of **non executive** files to my user?
I will probably go for a new install and just copy over Pictures,Music etc.. and leave the config files as they are.

---

### Post by steeldriver on 2012-08-10
you want to give back *ownership *- if you do that, there will likely be no need to mess with permissions

```
sudo chown -R *yourusername*:*yourusername */home/*yourusername*
```

---

### Post by krustenBrot on 2012-08-10
will this work on all files?
Or do i have to worry about executables?

---

### Post by steeldriver on 2012-08-10
it will change all the ownerships from root back to user (all files - executable or otherwise - and directories) but leave the permissions (file mode bits) as they are - this is usually what you want 

it's unlikely that the actual modes (aka 'permissions') have changed - *you *don't have permission simply because *root *is the owner

---

### Post by krustenBrot on 2012-08-10
**Thanks** for your help and the clarification!
Works like a charm :)

---


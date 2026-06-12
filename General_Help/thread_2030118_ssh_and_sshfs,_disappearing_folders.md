---
title: "ssh and sshfs, disappearing folders"
date: 2012-07-20
forum: General Help
---

### Post by vbonafe on 2012-07-20
I'm having exactly the same problem using Ubuntu 12.04 both on server and desktops.

If a user log in from one computer and copy something to a shared folder (via sshfs) and then other user mounts the same folder, the contents simply disapear!!!

Here's the command I'm using (it's in .profile):

```
sshfs $USER@192.168.1.100:/home/pub $HOME/pub
```

I'm sorry if it's an old thread, but it's the only one a found and I'm starting to panic in here...

Please, any help is very very wellcome...

---

### Post by matt_symes on 2012-07-20
Hi 

You posted in a very old thread (from 2009). 

The information may not be valid in old threads as thing change code software get updated.

You are far better of creating a new thread and link to the old thread if you think the information may be valid.

I have split your post off from  the old thread for you and linked to the old thread.

Old thread.

[http://ubuntuforums.org/showthread.php?t=1044481](http://ubuntuforums.org/showthread.php?t=1044481)

Kind regards

---

### Post by vbonafe on 2012-07-20
I'm giving up of sshfs for nfs, following this article:

[https://help.ubuntu.com/community/AutofsLDAP]("https://help.ubuntu.com/community/AutofsLDAP")

Hope to have more lucky with that, by now I got a bunch of angry users... :(

---


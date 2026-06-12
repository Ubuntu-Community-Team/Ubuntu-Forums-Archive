---
title: "Keyring lost - can I reset it ?"
date: 2006-03-10
forum: General Help
---

### Post by Metz on 2006-03-10
I appear to be missing my default keyring, and can't find a way to reset it.

Any ideas ?

---

### Post by ronmarley1 on 2006-03-10
Hi Metz,
I'm not exactly sure what you're asking, but I thinks this'll solve your problem.  Sorry if I'm off base.  Go to your Home folder.  Hit <Ctrl-H> to show hidden files.  Find .gnome2 and open it.  Find keyrings and open it.  Delete default.keyring.  When you are prompted for a password again, it will ask if you want to save it in Keyring.  If you click Yes, it will ask you to create a new keyring.

---

### Post by Metz on 2006-03-11
Thanks Ron !!

That's what I figured....but it wasn't working. However, turns out the issue was with Samba not connecting, therefore not trying to store passwords....therefore not creating a new keyring ! Doh !!

Thanks for your help :)

---

### Post by falkenberg_cph on 2006-06-14
I have got this problem too. So im just gonna hijack the thread :)

I have deleted the default.keyring., but my wireless dosnt ask for the keyring anymore. 

This topic is an offspring of my main problem:
[http://www.ubuntuforums.org/showthread.php?t=194932](http://www.ubuntuforums.org/showthread.php?t=194932)

It appears that after i installed keyring manager, where i tried deleting the default keyring wlan dosnt ask for it anymore, and it does not connect to my router.

I wish there was some way to completely remove keyring, and start over.
Please help me :( 

Carsten

---


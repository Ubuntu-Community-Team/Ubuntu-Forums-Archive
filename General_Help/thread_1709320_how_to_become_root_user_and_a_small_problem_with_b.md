---
title: "how to become root user and a small problem with banshee"
date: 2011-03-18
forum: General Help
---

### Post by padfootpak on 2011-03-18
I am trying to mount an ISO image. but for that i have to use root user. for that I do
>   su - it prompts me for password and i give the the password i use for "sudo" commands. It denies authentication. so i was wondering how I can find out my root password or maybe it's still default.

second problem, I tweaked with Banshee a little and now it won't show on the upper panel and when I press the close button it Quits instead of running in background and keep playing my songs. Any idea how to correct it. I re-installed it but that did not work.

---

### Post by fcomstoc on 2011-03-18
> **padfootpak said:**
> I am trying to mount an ISO image. but for that i have to use root user. for that I do
it prompts me for password and i give the the password i use for "sudo" commands. It denies authentication. so i was wondering how I can find out my root password or maybe it's still default.



for some reason ubuntu does not use root accounts it just has you sudo everything - i find this to be a pain so I created a root account with
fcomstoc@frank-laptop~$sudo passwd root 
it will ask for your sudo password and then for a root password twice
after that you can log in as root with  su

---

### Post by Joe of loath on 2011-03-18
Keep the root password as the default (it will be randomly generated to stop crackers). If you need a terminal session as root, use sudo -i, or sudo su, and use your sudo password.

---

### Post by padfootpak on 2011-03-18
I solved the first part. Any idea about the Banshee problem?

---

### Post by Joe of loath on 2011-03-18
Yes, go Edit > Preferences > Extensions > scroll to the bottom > select 'Notification Area Icon'

And it'll be back as it was.

---


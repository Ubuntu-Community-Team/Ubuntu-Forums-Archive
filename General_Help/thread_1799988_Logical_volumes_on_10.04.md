---
title: "Logical volumes on 10.04"
date: 2011-07-08
forum: General Help
---

### Post by NoFriends on 2011-07-08
Hi,

Posted on behalf of a friend.

Running 10.04 lucid 

set up 5 logical volumes on ubuntu installation which are in use.

The issue we are getting is trying to unmount these (as they are constantly in use)
and use the entire disk without any logical volumes, I have done some research and 
some people suggest not doing this because it can cause some serious damage.

Thanks in advance.

---

### Post by dino99 on 2011-07-08
sudo dpkg-reconfigure mountall

otherwise mountmanager can help you setting your prefs

---

### Post by NoFriends on 2011-07-08
I just attempted to run.

[COLOR=Red]df -h[/COLOR]

which gives me the tmp logical volume which i am trying to remove.

running

[COLOR=Red]sudo umount /directory/directory/tmp[/COLOR]

i get the message.

[COLOR=Red]umount: /tmp: device is busy.[/COLOR]

any ideas ?

---

### Post by dino99 on 2011-07-08
of course the Os use it continously, so cant be removed, it is highly needed :)

---

### Post by NoFriends on 2011-07-08
But the dev/mapper//tmp logical volume which i set up was not set up automatically during installation ?
i created the logical volume, the same with dev/mapper/opt and dev/mapper/var.

These are other logical volumes which were created by myself on installation.

---

### Post by SeijiSensei on 2011-07-08
Boot from a LiveCD and then work on the drive.

---

### Post by NoFriends on 2011-07-11
Thanks SeijiSensei

---


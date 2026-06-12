---
title: "How to run bash file without admin password."
date: 2010-11-01
forum: General Help
---

### Post by bearly230 on 2010-11-01
I have a bash file for turning off my touchpad. And it works perfect.

What I would like to be able to do is run it and not have to supply the root password.

Is there any way of doing this in Ubuntu 10.10?

Thanks.

---

### Post by luvshines on 2010-11-01
Does your file does 'su' to root, somewhere between the lines ? (I am guessing this since you say that it requires root password)

If it does, then you may want to add that file to allow password less run in /etc/sudoers and replace su with sudo

---

### Post by bearly230 on 2010-11-01
The command in the bash file is 

sudo modprobe -r psmouse

When I run it, it prompts for the password. Since it's such a simple file I would like to have it run without the user having to supply the password.

---

### Post by luvshines on 2010-11-01
Oh Ok, so it is asking for your password and not the 'root' password :)

Try adding this line to /etc/sudoers files:
```

## Open the /etc/sudoers editor
sudo visudo

## Add this line to the end of file. Replace <user-name> for your user
<user-name> ALL=NOPASSWD: /sbin/modprobe

```

It should luk something like(assuming bearly as username)
bearly ALL=NOPASSWD: /sbin/modprobe

Then save and close the file. I think this will work for password less thing
**But you may want to check what security implications it may have**

---

### Post by bearly230 on 2010-11-01
Thanks that took care of it. I do appreciate it.

---

### Post by luvshines on 2010-11-02
Nice to see it was resolved. :D

PS: Don't forget to mark this one **SOLVED**

---


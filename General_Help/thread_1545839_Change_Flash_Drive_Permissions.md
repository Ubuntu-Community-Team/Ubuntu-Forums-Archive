---
title: "Change Flash Drive Permissions"
date: 2010-08-04
forum: General Help
---

### Post by NM5TF on 2010-08-04
I just installed a usb card reader for my digi camera...how can I change the permissions from "root" to "user" so I can write to this flash drive?

It reads my pix just fine, but it won't let me write....

it is installed at /media/usb0

any help here??

Tom

---

### Post by rawlins02 on 2010-08-04
I believe this is done with:

> sudo chown -R username /media/usb0

where username is replaced with the desired user name.  But perhaps someone else here can confirm.

---

### Post by drewsus on 2010-08-04
thats right
but I would do:
```
sudo chown -R 1000 /media/usb0
sudo chgrp -R 1000 /media/usb0
```

1000 being the user id of the main user

---

### Post by NM5TF on 2010-08-04
):P

thanx guys...that fixed it...

change this to SOLVED

---

### Post by drewsus on 2010-08-04
> **NM5TF said:**
> ):P

thanx guys...that fixed it...

change this to SOLVED

YOU need to change this to Solved ;) 
Go to Thread Tools at the top and then...

---

### Post by joereith on 2010-08-04
you could have used the sudo chown -R username:username /dev/usb0 command to accomplish the same task. But good job anyways

---

### Post by mcduck on 2010-08-04
> **joereith said:**
> you could have used the sudo chown -R username:username /dev/usb0 command to accomplish the same task. But good job anyways

You really shouldn't change the ownership of device nodes.

---

### Post by Smart Viking on 2010-08-04
> **mcduck said:**
> You really shouldn't change the ownership of device nodes.

Can you explain this? I don't understand. :)

---


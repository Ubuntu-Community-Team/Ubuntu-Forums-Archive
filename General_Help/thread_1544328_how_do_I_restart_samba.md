---
title: "how do I restart samba/"
date: 2010-08-02
forum: General Help
---

### Post by kaykav on 2010-08-02
good morning,
                   So how do I start or restart samba? I tried
/etc/init.d/samba restart to no avail.  Im confused..thanks

---

### Post by Smart Viking on 2010-08-02
if "samba" is the command to launch samba, i guess you could just "pkill samba && samba", you might need to use sudo though, i dont know. :)

---

### Post by cob on 2010-08-02
The "new" method is "service smbd restart".  If you try to restart it with the scripts in /etc/init.d, it tells you as much, I believe.

---

### Post by Telengard C64 on 2010-08-02
> **kaykav said:**
> I tried
/etc/init.d/samba restart to no avail.

Try one of these:

```
sudo /etc/init.d/samba restart
```

or

```
sudo /etc/init.d/samba reload
```

or

```
sudo smbd reload
```

[_SettingUpSamba_](https://help.ubuntu.com/community/SettingUpSamba)

[_related thread_](http://ubuntuforums.org/showthread.php?t=258320)

---

### Post by Telengard C64 on 2010-08-02
> **cob said:**
> The "new" method is "service smbd restart".  If you try to restart it with the scripts in /etc/init.d, it tells you as much, I believe.

That will restart *smbd*. Now what about *nmbd*?

---

### Post by Morbius1 on 2010-08-02
Just exchange the "s" with an "n":
```
sudo service nmbd restart
```

---

### Post by kaykav on 2010-08-02
Thank you very much.It worked. but where can I find that info?
Ona ubuntu documentation? or?

---

### Post by CharlesA on 2010-08-02
I don't know if it's actually documented anywhere except on the forums.

I usually use this script to start/stop samba:

```
#!/bin/bash
service smbd stop && service nmbd stop
service smbd start && service nmbd start
```

Run it with **sudo**.

---

### Post by sdaau on 2010-12-09
> **CharlesA said:**
> I don't know if it's actually documented anywhere except on the forums.

I think you're right - I just spent HOURS trying to find the "restart samba" syntax, and this is the first one that seemingly works!!

EDIT: 
goddamn, no it doesn't on Lucid:
```

sudo service smbd restart
smbd: unrecognized service

sudo service nmbd restart
nmbd: unrecognized service

sudo /etc/init.d/samba restart
sudo: /etc/init.d/samba: command not found

sudo smbd reload
sudo: smbd: command not found

```

WHAT THE ****!!!!!!???

WHY IS THIS SO STUPID ????!!!


WHAT THE **** IS THE PROPER COMAMND TO RESTART SAMBE IN LUCID FOR ****S SAKE!!!!?????

---

### Post by Morbius1 on 2010-12-09
You're using the right commands to restart smbd and nmbd if they are already started. You would get another type of error if they are stopped when you issue a restart. In that case you would have to issue a "sudo service smbd start".

But in your case you're getting an "unrecognized service"

Almost sounds like you don't have samba installed or maybe that you inadvertently installed Samba4.

Make sure you have the following packages installed:
samba
samba-common
samba-common-bin

And make sure you don't have any samba4 stuff installed.

---


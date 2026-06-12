---
title: "recover login"
date: 2011-12-24
forum: General Help
---

### Post by booch1131 on 2011-12-24
hi folks,
a friend set up ubuntu for me. he said he did not create a password but when i want to do updates, i am prompted for a password for authentication.
i tried leaving the space blank but that does not work.
so, i googled how to reset the password and did the following:
boot to recovery
drop to root shell
ls /home
passwd username
created new password (and created a new password)

THEN to exit, i'm asked for a LOGIN name and a password,
lo and behold, i have no idea what the login name is.
(i do not need a login or a password to get into ubuntu.)
so i looked around some more and discovered a login admin screen and need a password to get into that. (greyed out, i can see the login name -- it is: Tom (tom)  -- i tried that while in the root -- no go.
the password i created does not work.

so... i tried to install an update using the password i created and that does not authenticate either.

at this point, i'm at a loss.
although i've been using ubuntu (10.04 i think) for about two years, i mainly use it for recovery purposes -- and try to keep it updated in the event i need to use it.
this is a new computer -- and as i mentioned the person who installed it has no recollection of using a password.

i'm at a standstill and in over my head.
any help would be greatly appreciated.
thanks and happy holidays.

---

### Post by WorMzy on 2011-12-24
Do you mean that you're stuck at the recovery shell? Just press Ctrl+Alt+Del to restart.

Or you can log in using the username you provided when you ran "passwd username", and the password you set. Then reboot with

```
sudo shutdown -r now
```

---

### Post by booch1131 on 2011-12-24
when i type in exit from the prompt, i'm asked for a login and a password.
i don't know what the login is supposed to be.
i know the password -- but not the login.
so i hard reboot -- no biggie.
but when i try to install an update or anything else, the password i created at root does not work.

does that make sense?
tks

---

### Post by WorMzy on 2011-12-24
> **booch1131 said:**
> i know the password -- but not the login.

Well, what did you use when you ran the "passwd username" command?

I have a feeling that you didn't set the password for the right user if it's not being accepted now.

What does the terminal prompt say? It should look something like
```
username@hostname:~$
```

The username will be the username that you need to set the password for. It is also the "login".

---

### Post by fdrake on 2011-12-24
> 
boot to recovery
drop to root shell
ls /home
passwd username

i think you changed the password of the "username" user(do you have a user called username?)
do the process again but this time use your username:
```

passwd your_username

```

---


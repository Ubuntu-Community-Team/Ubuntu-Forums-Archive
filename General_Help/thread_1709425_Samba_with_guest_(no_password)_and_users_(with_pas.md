---
title: "Samba with guest (no password) and users (with password)"
date: 2011-03-18
forum: General Help
---

### Post by aktiwers on 2011-03-18
Im creating a Samba share with public folders which should be accessible from any guests without the password/login promt. The share is on Debian and the clients are Windows XP. 

This is easily solved by setting:
```
security = share
...
...
guest account = nobody
...
...
[Guest Share]
        comment = Guest access share
        path = /path/to/dir/to/share
        browseable = yes
        read only = yes
        guest ok = yes

```in smb.conf.

Now I also want to create folders which need username and password before access, on this same samba server.

Any idea how to achieve this?

---

### Post by pricetech on 2011-03-18
To be honest, I haven't edit an smb.conf in a long time.  I guess I'm just too old and lazy.

Anyway;  Install system-config-samba and you'll have a dandy configuration tool that will allow you to set up your Samba server with ease.

Have fun.

---

### Post by Morbius1 on 2011-03-18
```
[Non Guest Share]
        comment = Non Guest access share
        path = /path/to/dir/to/share
        browseable = yes
        read only = yes
        valid users = user1, user2
```You will have to create user1 and user2 on the server. Then add them to the samba password database with this command:
```
sudo smbpasswd -a user1
```[I]Side Note: Don't know if you are having some kind of networking problem that you are using share level security but if it were my system I would replace:
```
security = share
```with the following:
```
security = user
map to guest = Bad User
```[/I]

---

### Post by aktiwers on 2011-03-18
Thanks for both your replies. I will try this next week.
I don't have any GUI installed on the server, so system-config-samba is sadly not an option for me.

One question Morbius1..

What does "map to guest = bad user" do?

The reason I used "security = share" was to get rid of the login prompt for guest access.
All other things I tried kept prompting guests users for login info..  but I haven't tried this :)

---

### Post by Morbius1 on 2011-03-18
> What does "map to guest = bad user" do?

The reason I used "security = share" was to get rid of the login prompt for guest access.
All other things I tried kept prompting guests users for login info..  but I haven't tried thisIt's a poorly labeled option that has a rather convoluted logic. If the remote user passes an invalid password it will be rejected unless the username doesn't exist in the samba database or wasn't asked for in the share definition ( guest ok = yes ) in which case it gets mapped to the "guest account".

The reason you got a password prompt before was because you had "security = user" ( which is the modern default ) and "guest account = nobody" but you had no way to connect the remote guest to the guest account because you didn't have "map to guest = Bad User".

---

### Post by aktiwers on 2011-03-22
Tried it today and it worked perfectly!

Thanks a lot Morbius1 :)

---


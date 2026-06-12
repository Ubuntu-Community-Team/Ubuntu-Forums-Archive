---
title: "I'm getting asked for (non-existing) root password for administrative tasks!"
date: 2010-01-13
forum: General Help
---

### Post by auh2o on 2010-01-13
Ubuntu 9.10 has started asking me for the root password for doing administrative tasks. How did that happen? I haven't even set a root password! I am logged in as a regular /home/ user with sudo rights, but now I can't even authenticate to look at my user rights settings! I recently changed my user privileges to include wireless & network connections, but that's the extent of what I have done.

---

### Post by Mickser_52 on 2010-01-13
Have you tried the password you use at log-in?

---

### Post by sisco311 on 2010-01-13
Is your user in the admin group?

Open a terminal (Applications -> Accessories -> Terminal)
and post the output of:
```
id
```
and
```
grep $USER /etc/group
```

**DON'T** try to log out!!!

---

### Post by auh2o on 2010-01-13
My user password is not accepted.

However, contrary to the advice above, I already restarted and logged into my user account again, and that worked. I am however still asked to supply a root password when trying anything.

As per your request:

```
uid=1000(michael) gid=1000(michael) groups=4(adm),20(dialout),21(fax),24(cdrom),29(audio),30(dip),44(video),46(plugdev),104(lpadmin),112(netdev),1000(michael)
``````
adm:x:4:michael
dialout:x:20:michael
fax:x:21:michael
cdrom:x:24:michael
audio:x:29:pulse,michael
dip:x:30:michael
video:x:44:michael
plugdev:x:46:michael
lpadmin:x:104:michael
netdev:x:112:michael
michael:x:1000:michael
```(Yes, my name is Michael.) ;)

---

### Post by sisco311 on 2010-01-13
You removed your user from the admin group. Boot in *Recovery Mode* and add it back to the group:
[http://psychocats.net/ubuntu/fixsudo](http://psychocats.net/ubuntu/fixsudo)

---

### Post by auh2o on 2010-01-13
Alright. Figures I ****** up something! Thank you kindly.

I second the opinion at your link!

> If you think it's silly that the last *admin* user can be so easily removed graphically from the *admin* group, vote for [Idea #11107: Users and Groups should always make sure at least one user is in the admin group]("http://brainstorm.ubuntu.com/idea/11107/") on Ubuntu Brainstorm. 

---

### Post by sisco311 on 2010-01-13
> **auh2o said:**
> Alright. Figures I ****** up something! Thank you kindly.

I second the opinion at your link!

You are welcome!

Please mark your thread as [SOLVED] by selecting **Mark this thread as solved** from the [color="Red"]Thread tools[/color].

---

### Post by auh2o on 2010-01-13
...and I am back in action!

I feel really silly. I must've accidentally unticked that box while ticking the other. Coming from a Windows environment (and not missing it!), I think I might've appreciated an extra prompt there, along the lines of "are you sure you want to remove..." etc.

---


---
title: "usermod"
date: 2010-07-02
forum: General Help
---

### Post by johnmay on 2010-07-02
:D So, I was planning on getting the USB to work in my 3.2.4 Oracle virtual box, and I found a post that says you have to be a part of vboxusers. I ran > sudo usermod *-G *vboxusers* alias *and then id to see that I was a part of the vboxusers group. After I installed an update which required restart. 

Can you guess what happened? 

That is right! I am no longer in the /etc/sudoers file!!!

Am I toast or what? 

Suggestions? :redface:


Thanks!

---

### Post by marshmallow1304 on 2010-07-03
That command will have removed you from all groups except vboxusers.  To append a group to your current groups, also use -a:

```
sudo usermod -aG <group> <user>
```


In this case, you can follow the section "Booting into recovery mode" on [this page]("http://www.psychocats.net/ubuntu/fixsudo#recoverymode").  Then run

```
usermod -aG admin <user>
```

Now you can at least use sudo so you can use the Users and Groups utility to re-add yourself to necessary groups.

---

### Post by bodhi.zazen on 2010-07-03
> **johnmay said:**
> :D So, I was planning on getting the USB to work in my 3.2.4 Oracle virtual box, and I found a post that says you have to be a part of vboxusers. I ran > sudo usermod *-G *vboxusers* alias *and then id to see that I was a part of the vboxusers group. After I installed an update which required restart. 

Can you guess what happened? 

That is right! I am no longer in the /etc/sudoers file!!!

Am I toast or what? 

Suggestions? :redface:


Thanks!

Boot to recovery mode, drop to a shell.

You will have a command line (bash shell) and you can add your user back to the admin group as well as any additional groups you may need.

Do you know how to do that ? Use the -a option (with uermod).

-g sets your default group. It should be the same as your login name.

---


---
title: "Need help, I accidentally removed myself from all the groups, can't sudo"
date: 2010-12-21
forum: General Help
---

### Post by lobo_tuerto on 2010-12-21
Hi guys,


I was trying to add myself to an existing group but instead ended only on two groups: the new group and myself. Right now **I can't do sudo** and who knows what other things.

If I try to sudo I get this:

```
my-username is not in the sudoers file.  This incident will be reported.
```

What is the list of groups I should belong to?

Can anyone publish what do you see after typing this in the terminal:

```
groups your-username
```

Do I need to boot into recovery mode?

Help! :(

---

### Post by coffeecat on 2010-12-21
I think this will help you:

[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by karthick87 on 2010-12-21
Boot using a live cd and edit the sudoers file..And this is the output which you asked,

```
karthick@Ubuntu-desktop:~$ groups karthick
karthick : karthick adm dialout cdrom dip plugdev lpadmin admin sambashare
```

---

### Post by TNT1 on 2010-12-21
If you still have your root password, why not just go System>Adminstration>Users&Groups and add your user back into the required groups?

---

### Post by efflandt on 2010-12-21
> **lobo_tuerto said:**
> Do I need to boot into recovery mode?Yes, that will work.  No password is needed for netroot or root shell from there to edit /etc/group

I had to do that when natty temporarily removed admin from sudoers and I had to add myself to sudo group.

---

### Post by lobo_tuerto on 2010-12-21
Great success!

I booted into recovery mode as root, then simply did:

```
adduser my-username admin
adduser my-username adm
```

(**Thank you coffeecat!**)


Then rebooted, and sudo is working!

And then added the missing groups (**thank you karthick87!**)

---

### Post by karthick87 on 2010-12-21
You are welcome :)

---


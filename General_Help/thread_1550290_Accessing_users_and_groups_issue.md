---
title: "Accessing users and groups issue"
date: 2010-08-10
forum: General Help
---

### Post by ajgajg1134 on 2010-08-10
I'm trying to access my users and group tool and when I run the command:
```
users-admin
```
I get this back and it shows the window, but the groups section is broken.
```

(users-admin:4342): Liboobs-WARNING **: There was an unknown error communicating asynchronously with the backends: Message did not receive a reply (timeout by message bus)

(users-admin:4342): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

```

Thanks for any help any one can provide. :)

(EDIT)I have already tried reinstalling the addusers package, and this did not fix my problem. (/edit)

---

### Post by oleink on 2010-08-10
> **ajgajg1134 said:**
> I'm trying to access my users and group tool and when I run the command:
```
users-admin
```
I get this back and it shows the window, but the groups section is broken.
```

(users-admin:4342): Liboobs-WARNING **: There was an unknown error communicating asynchronously with the backends: Message did not receive a reply (timeout by message bus)

(users-admin:4342): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

```

Thanks for any help any one can provide. :)

(EDIT)I have already tried reinstalling the addusers package, and this did not fix my problem. (/edit)

can you open it manually??

---

### Post by ajgajg1134 on 2010-08-10
Yes, but it opens the same way, where the groups window is broken.

(Edit)
When I log in to root I'm able to make changes to the groups, or if I run sudo users-admin.
But none of the group changes I make work. I also am unable to change any user privileges.
(/Edit)

---

### Post by oleink on 2010-08-10
> **ajgajg1134 said:**
> Yes, but it opens the same way, where the groups window is broken.

(Edit)
When I log in to root I'm able to make changes to the groups, or if I run sudo users-admin.
But none of the group changes I make work. I also am unable to change any user privileges.
(/Edit)

strange sorry i couldn't fin anything online

---

### Post by ajgajg1134 on 2010-08-11
> **oleink said:**
> strange sorry i couldn't fin anything online

Dang. hmm. Is anyone else having this problem out there? Or know of a fix? It appears as though all my groups have been reset, but I can't fix them. :P

---

### Post by oleink on 2010-08-11
> **ajgajg1134 said:**
> Dang. hmm. Is anyone else having this problem out there? Or know of a fix? It appears as though all my groups have been reset, but I can't fix them. :P

[http://www.linuxquestions.org/questions/linux-software-2/users-and-groups-root-access-ubuntu-714305/]("http://www.linuxquestions.org/questions/linux-software-2/users-and-groups-root-access-ubuntu-714305/")


[http://ubuntuforums.org/showthread.php?t=478005]("http://ubuntuforums.org/showthread.php?t=478005")


[http://ubuntuforums.org/showthread.php?t=473630]("http://ubuntuforums.org/showthread.php?t=473630")


Not all of these are directly related but it's a start...

---

### Post by oleink on 2010-08-11
[http://ubuntuforums.org/showthread.php?t=473630]("http://ubuntuforums.org/showthread.php?t=473630")


This appears to be similar or based on a similar problem...  If this is the problem you're having I'm sorry because there was no fix to the bug report that there is a link to at the end of the page

---

### Post by ajgajg1134 on 2010-08-11
> **oleink said:**
> [http://ubuntuforums.org/showthread.php?t=473630]("http://ubuntuforums.org/showthread.php?t=473630")


This appears to be similar or based on a similar problem...  If this is the problem you're having I'm sorry because there was no fix to the bug report that there is a link to at the end of the page

Ya, It looks as though this might be my problem in another form. I was able to add myself to important groups manually in the terminal, but it hasn't fixed my problem. ```
adduser <user> <group>
```

---

### Post by oleink on 2010-08-11
> **ajgajg1134 said:**
> Ya, It looks as though this might be my problem in another form. I was able to add myself to important groups manually in the terminal, but it hasn't fixed my problem. ```
adduser <user> <group>
```

Yeah according to that it was a bug but I wouldn't be suprised if it was a bug on the install.  Maybe a fresh install?  I know it isn't fun (i did it like a week ago) but it may fix some of those problems with a fresh iso, fresh cd, and fresh install.  (make sure you put all the data you still need on a drive to go back on after the install (just a reminder if you go this route)

---

### Post by ajgajg1134 on 2010-08-11
Yea, I think I'll just work around it for the mean time, but if it becomes a real issue I'll do a fresh install. Thanks for the help!

---

### Post by oleink on 2010-08-11
> **ajgajg1134 said:**
> Yea, I think I'll just work around it for the mean time, but if it becomes a real issue I'll do a fresh install. Thanks for the help!

Yep.  That's what I'd do too.  If it's not a big deal to you why bother with fresh install :)

---


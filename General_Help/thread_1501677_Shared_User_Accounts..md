---
title: "Shared User Accounts."
date: 2010-06-04
forum: General Help
---

### Post by leona on 2010-06-04
I have 3 shared user accounts, basically these are basic user accounts that I use for different things, web development for example.

Before I created these account and gave myself (my user) access to them.

In 10.04 however this doesn't seem possible, I've put them all in the 'users' group and given myself access to that group and to the user, but do you think I can read and write files, nope.

Has something changed in 10.04 and if so how do I achieve what I need?

Arr fixed it, just chmod'd it all to 775 I'd forgotten that!

---

### Post by WorMzy on 2010-06-04
That'll work, but any of the users on the machine will be able to do anything they want with those files. A better solution would be to add the main user to the other user's groups. For example, say you have three users: Ted, Bob, and Jen, and you want Ted to be able to access Bob and Jen's files; you just need to add Ted to group Bob and group Jen.

---

### Post by leona on 2010-06-04
> **WorMzy said:**
> That'll work, but any of the users on the machine will be able to do anything they want with those files. A better solution would be to add the main user to the other user's groups. For example, say you have three users: Ted, Bob, and Jen, and you want Ted to be able to access Bob and Jen's files; you just need to add Ted to group Bob and group Jen.
Thing is WorMzy, I had actually done that, so I thought I'd have access, but it didn't seem to work ??
Hum, actually I have just reset that and your right, it worked, how strange, thank you.

---

### Post by leona on 2010-06-06
Still linux isn't doing what i want, or I don't understand it.
I have this 'shared' account, but when I, or my partner, place files in this account, neither of us can access the other persions files, because they are in our own group, why are the files not in the 'shared' group, and how can I make it save files to a shared group, so we can both access them, we don't want access to each others user accounts but we want to share files, how the hell do we do this!!!! ?

---

### Post by drdos2006 on 2010-06-06
Have a look here, it may help.

[http://ubuntuforums.org/showthread.php?t=1484221](http://ubuntuforums.org/showthread.php?t=1484221)

regards

---

### Post by leona on 2010-06-07
Oh right, so I need to set a 'sgid' like 
```

chmod 2770 /home/shared

```
Hum, will try that, never seen this before... :)

---

### Post by sisco311 on 2010-06-07
Even if you set the setgid bit new file will not inherit the permissions just the group. Try [ACLs]("http://https://help.ubuntu.com/community/UbuntuLTSP/ACLSupport") or [thread=1460472]bindfs[/thread].

---

### Post by leona on 2010-06-07
I see, thank you, read the thread, and will give Bindfs a try, thank you.

---


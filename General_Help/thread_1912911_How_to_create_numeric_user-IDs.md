---
title: "How to create numeric user-IDs"
date: 2012-01-21
forum: General Help
---

### Post by Rebelli0us on 2012-01-21
I’m setting up a system for a company that uses numeric user-IDs... 001, 002, etc. The company also uses Windows and in switching to Linux the owner wants to maintain the employees’ existing IDs. Currently they are experimenting with Ubuntu and employees are using random strings because **Linux disallows user IDs that start with numbers**.

How to convert string IDs to numeric? Would this be correct for employee 007 currently using ID “JamesBond”?

[B]adduser --force-badname 007 admin

usermod -l 007 -m -d /home/007 JamesBond
[/B]

---

### Post by Lars Noodén on 2012-01-21
You'll also probably want the UID to match the name so you should set --uid at the same time.

---

### Post by Rebelli0us on 2012-01-21
Thank you, I'm trying to keep this simple. The usermod command alone should work but I fear it may fail due to the numeric ID.

**usermod -l 007 JamesBond**

---

### Post by Lars Noodén on 2012-01-21
The only difficulty that I can forsee is that the user IDs below and around 100 are often taken for various services.  If you precede the number with a letter, then that problem goes away.

"*Typically, UIDs below 500 are reserved for system accounts ...*"
[http://books.google.com/books?id=IZqg3kQzpEMC&pg=PA119&lpg=PA119&dq=reserved+uids+ubuntu&source=bl&ots=_0ogfNb8HT&sig=_CvGDLNVqPe_6zx44hFfqkZXS_0&hl=en](http://books.google.com/books?id=IZqg3kQzpEMC&pg=PA119&lpg=PA119&dq=reserved+uids+ubuntu&source=bl&ots=_0ogfNb8HT&sig=_CvGDLNVqPe_6zx44hFfqkZXS_0&hl=en)

---

### Post by Rebelli0us on 2012-01-21
> **Lars Noodén said:**
> The only difficulty that I can forsee is that the user IDs below and around 100 are often taken for various services.  If you precede the number with a letter, then that problem goes away.

"*Typically, UIDs below 500 are reserved for system accounts ...*"
[http://books.google.com/books?id=IZqg3kQzpEMC&pg=PA119&lpg=PA119&dq=reserved+uids+ubuntu&source=bl&ots=_0ogfNb8HT&sig=_CvGDLNVqPe_6zx44hFfqkZXS_0&hl=en](http://books.google.com/books?id=IZqg3kQzpEMC&pg=PA119&lpg=PA119&dq=reserved+uids+ubuntu&source=bl&ots=_0ogfNb8HT&sig=_CvGDLNVqPe_6zx44hFfqkZXS_0&hl=en)

007 is just for example, user IDs will be 6 digits long.

---

### Post by Rebelli0us on 2012-01-21
I tried this and it fails:

```


sudo adduser --force-badname 007 admin
adduser: The user `007' does not exist.


```

---

### Post by Lars Noodén on 2012-01-21
Right. That will fail.  What you need is something more like this:

```

adduser --force-badname --uid 007 007

```

That will give you a use with the name 007 as well as a UID of 7.

---

### Post by SeijiSensei on 2012-01-21
> **Lars Noodén said:**
> That will give you a user with the name 007 as well as a UID of 7.

As you mentioned earlier, Lars, he shouldn't do that.  UIDs below 100 are largely reserved for system processes and daemons.  UID 7 is assigned to the "lp" user in my 10.10 copy of /etc/passwd.  OP, I suggest you look carefully at that file before you go much further.

RedHat and CentOS start assigning regular users' UIDs at 500; Debian and Ubuntu start at 1000.

What's wrong with u007?  Or, in your case, I guess it would be something like u123456.

I didn't know Windows allowed numeric usernames.  Is that still true with Win7+?  With an AD server?

One other thing to consider if you're planning to set up a mail server to work with these IDs.  People would need to know that Joe Smith has email address [email]u135325@example.com[/email].  The alternative is lots of entries in /etc/aliases.  Wouldn't you really rather have meaningful usernames like jsmith?

---


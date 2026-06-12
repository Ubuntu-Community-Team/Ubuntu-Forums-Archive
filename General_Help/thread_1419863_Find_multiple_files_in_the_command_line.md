---
title: "Find multiple files in the command line"
date: 2010-03-02
forum: General Help
---

### Post by lazo99 on 2010-03-02
Hi All,

I needs some help in the command line, I have a server for work that I ssh into and I need to be able to find multiple files (they have the leading text just the date identifier changes) and then zip the files (with bzip) them and then finally scp(Secure copy) them to another server.

These files are always in the same directory and this is a daily task and just want to make into a script that I run once I am logged into the remote server. 

Please let me know if there is any more info I can provide to help with this question.

Thanks to all in advance!

---

### Post by iponeverything on 2010-03-02
this is pretty painless. Do you need something for just files for the current day or previous day.

The ssh can be made to work without password by using keys.

give an example of a file name.

---

### Post by lazo99 on 2010-03-02
Here are the beginning names of the files

CD-029
DD-010
MD-022
MD-032
MD-033

---

### Post by iponeverything on 2010-03-02
> **lazo99 said:**
> Here are the beginning names of the files

CD-029
DD-010
MD-022
MD-032
MD-033

You are being very vague.

how does the name relate to date?

If you just want something like the 10 recent files:
```

ls -ltr | tail -10 | awk '{print "scp "$1" user@ip_address:/location/"}' 

```
adding a |sh to end of the line will make happen:

```
ls -ltr | tail -10 | awk '{print "scp "$1" user@ip_address:/location/"}' |sh

```

You will need to add the ssh keys to the remove machine so that it does not prompt for a password.

---

### Post by lazo99 on 2010-03-03
Sorry, don't mean to be vague

The date would be trailing like so:

CD-029_2010-02-26
DD-010_2010-02-26
MD-022_2010-02-26
MD-032_2010-02-26
MD-033_2010-02-26

---


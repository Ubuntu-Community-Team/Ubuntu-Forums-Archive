---
title: "Create a Service User"
date: 2010-03-03
forum: General Help
---

### Post by ofrxnz on 2010-03-03
So, I know this probably isn't the first time this has been asked but...I have a script I would like to run as a service or cron job, but don't want it to run as me or root.

Whats the best way to create a service account and how would i kick something off under that user?

Thanks

Ubuntu server 8.04 64-bit

---

### Post by warp99 on 2010-03-03
> **ofrxnz said:**
> So, I know this probably isn't the first time this has been asked but...I have a script I would like to run as a service or cron job, but don't want it to run as me or root.

Whats the best way to create a service account and how would i kick something off under that user?

Thanks

Ubuntu server 8.04 64-bit

Just create a new user account with the group access you want. Then in your script add the following:

```
su $user -c "$command_string"
```

The script itself has to run as root, but the command runs under a different user id. You could also just run the script as a cron job under that user. 

Why do you need to run this under a different user? The reason I ask is there may be a much easier way.

---

### Post by ofrxnz on 2010-03-04
Thanks for the response.  I inherited our *nix boxes and the last guy ran everything as root and was generally sloppy.  So as I'm slowly going through them I'm trying to tighten it up. In this case, I am trying to update our backup scripts (rsnapshot).

what is the best way to create a service account.  Is it just useradd <name> <homespace> and never set a password so it cant log in? 

Thanks Again,

Adam

---

### Post by warp99 on 2010-03-04
> **ofrxnz said:**
> what is the best way to create a service account.  Is it just useradd <name> <homespace> and never set a password so it cant log in? 

Thanks Again,

Adam

I believe a system account, -r parameter with useradd, is what you're looking for. Take a look at the useradd man pages for more info.

---

### Post by Agent ME on 2010-03-04
> **ofrxnz said:**
> what is the best way to create a service account.  Is it just useradd <name> <homespace> and never set a password so it cant log in?
System accounts also generally have much lower uids. If it's below 1000, it will not show up in the main login screen. (As said above, just use the -r parameter to make the account.)

---


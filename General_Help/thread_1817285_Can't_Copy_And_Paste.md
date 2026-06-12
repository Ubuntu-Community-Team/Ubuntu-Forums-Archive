---
title: "Can't Copy And Paste"
date: 2011-08-03
forum: General Help
---

### Post by Brooksy_FC on 2011-08-03
Hey All,

I'm trying to copy and paste/drag and drop files into /var/www folder, but I keep getting "Error While Copying" do not have permissions.

I know you can run "sudo nautilus" and that gives you permission, but is there a way to have it on permanently rather than running the command all the time?

Cheers Guys!

---

### Post by UnnamedUzer on 2011-08-03
> **Brooksy_FC said:**
> Hey All,

I'm trying to copy and paste/drag and drop files into /var/www folder, but I keep getting "Error While Copying" do not have permissions.

I know you can run "sudo nautilus" and that gives you permission, but is there a way to have it on permanently rather than running the command all the time?

Cheers Guys!

You can give enough permition to you user for this folder
just 
```
chmod 777 /var/www
```

Try to read man of CHMOD ... tune permition

---

### Post by Matt__ on 2011-08-03
The whole point of sudo is so that for a process to run, it has to be authorised.

This achieves two things, it stops illegal processes (ie: ones not initiated by you the user or root) and makes you think about what you are doing so you don't accidentally mess up your system.

Without this built in security you have a system that can be easily modified by malicious 3rd parties via hacks, cracks, spyware, trojans or just plain screwed up by bad and unconsidered user decisions.

Is this all starting to sound familiar? DONT enable sudo permanently in anything!

So anyway, either live with gksudo nautilus or use [ubuntu-tweak]("http://ubuntu-tweak.com/") to allow right click/open as admin.


//edit: a bit of a rant I know lol...but you get the idea :)

---

### Post by Brooksy_FC on 2011-08-03
Ah, I see now. I was wondering what Sudo was haha.

Thanks for your help! :)

---


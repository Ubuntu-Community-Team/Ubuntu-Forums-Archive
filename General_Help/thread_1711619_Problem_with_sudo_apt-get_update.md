---
title: "Problem with sudo apt-get update"
date: 2011-03-21
forum: General Help
---

### Post by Mr. ViC on 2011-03-21
Well, I'll be straight with you guys here.

Here's the output:

```
http://pastebin.com/9EaBYWBB
```It's on the link because it was too big to post here.

Like, why is it asking for the CD?

I've tried to insert the CD, but seems it's not mounted on the right location and I think it won't solve anything either, problem should be one of the repositories I guess.

Any help here would be very appreciated.

Thank you guys very much in advance.

---

### Post by Script Warlock on 2011-03-21
type in the terminal 

gksudo software-properties-gtk

untick the "cdrom with ubuntu 10.10..."

---

### Post by Mr. ViC on 2011-03-21
Thank you for your reply.

Done, and it does not ask for the CD anymore. I'll keep the command in case I need it in the future.

Now it's just another problem with a public key.

```
http://pastebin.com/TPyPHL08
```

Thanks again for helping me out. :)

---

### Post by Script Warlock on 2011-03-21
try

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 7274A4DAE80D6BF5

---

### Post by Mr. ViC on 2011-03-21
That removes the key, right?

Well, thank you very much!

Sudo apt-get update is running with no problems. :)

---

### Post by Script Warlock on 2011-03-21
cheers :)

---

### Post by lazyr on 2011-11-01
> **Mr. ViC said:**
> That removes the key, right?

No, it doesn't remove the key. It actually does the opposite: it imports the public key from the Ubuntu key server so all packages from the respective repository can be checked as trusted.

---


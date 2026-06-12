---
title: "Will I need to upgrade"
date: 2006-04-07
forum: General Help
---

### Post by beforewisdom on 2006-04-07
I just installed 5.10.

I understand a new release is just around the corner.  If I keep installing all of the updates will I get all of the cool new stuff?

Do I need to...and should I,  run apt-get update on a regular basis?

Thanks in advance for the info

Steve

---

### Post by dcstar on 2006-04-07
[QUOTE=beforewisdom]I just installed 5.10.

I understand a new release is just around the corner.  If I keep installing all of the updates will I get all of the cool new stuff?

Do I need to...and should I,  run apt-get update on a regular basis?

Thanks in advance for the info

Steve[/QUOTE]
You will get 5.10 updates automagically offered to you, but to upgrade to 6.10 there will be more work involved.

Just keep an eye on the forums and instructions to upgrade to 6.10 will appear when it has been officially released.

---

### Post by Qrk on 2006-04-07
apt-get update and upgrade are scheduled to run every day through the update manager. So you don't have to manually upgrade/update unless you want to (it won't hurt).

Once Dapper is released, all you need to do is change your sources.list (/etc/apt/sources.list) to reflect the new release and then do a "dist-upgrade". This can be a little tempermental, but usually works just fine. 

For an explaination of how apt-get works, open a terminal and type:

```
man apt-get
```

---

### Post by izmaelis on 2006-04-07
It is possible for you to move from current Ubuntu release (5.10) to the new one (6.06) when it will be released with no pain at all. There is a guide about upgrading to current Breezy from any older version [here]("https://wiki.ubuntu.com/BreezyUpgrade"), so there should be such an official guide for Dapper when it will be released.
Don't worry, be happy!

---


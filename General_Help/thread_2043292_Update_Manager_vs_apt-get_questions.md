---
title: "Update Manager vs apt-get questions"
date: 2012-08-16
forum: General Help
---

### Post by ratcheer on 2012-08-16
I have hit a few curious situations recently where "apt-get upgrade" held some packages back from installation, but the GUI Update Manager happily installed them. I am starting to wonder more about the differences between the two.

I have been using Ubuntu for over three years. Early on, multiple sources convinced me that aptitude was the "best" package manager to use. It served me well and I still prefer it, generally. It did cause me to have a few bad situations over the years.

But, while testing Precise prior to its final release, strong advice was given not to use aptitude, but apt-get, instead. So, I switched reluctantly. I have no idea whether this advice is still in effect, but I have dutifully used apt-get since then.

Now, this. I will run apt-get update, then apt-get upgrade. A couple of days ago, the upgrade step held the revised Linux kernel upgrades. But then, Update Manager popped up on its own, offering to install them. I decided to allow Update Manager to go ahead and the new kernel packages were installed successfully, and no problems have ensued.

So, what differences are in play here? Inquiring minds want to know.

Tim

---

### Post by venky96 on 2012-08-16
I think I get by what you mean. If i'm wrong please excuse me. I guess because its the difference between

```
apt-get upgrade
```

and

```
apt-get dist-upgrade
```

You can find a detailed explanation here

[http://davitenio.wordpress.com/2008/08/24/difference-between-apt-get-upgrade-and-apt-get-dist-upgrade/](http://davitenio.wordpress.com/2008/08/24/difference-between-apt-get-upgrade-and-apt-get-dist-upgrade/)

---

### Post by smartboyhw on 2012-08-16
apt-get normally updates packages, update-manager does everything, including upgrading to 12.10.

---

### Post by ratcheer on 2012-08-16
Ok, I guess so.

But, in the past I have also been warned against forcing a dist-upgrade just because a few packages are held back. The usual advice has been to wait a few days for dependencies to straighten out. Sometimes waiting helps, other times not.

I guess this is why Siduction Linux, based on Debian sid and always installing the very latest packages, recommends always doing dist-upgrade. But, it seems that Update Manager always does dist-upgrade, too. Is this a proper interpretation?

Didn't you used to have to run "update-manager -d" to get a dist-upgrade? Has this changed?

Thanks,
Tim

---

### Post by smartboyhw on 2012-08-16
> **ratcheer said:**
> Ok, I guess so.
 
But, in the past I have also been warned against forcing a dist-upgrade just because a few packages are held back. The usual advice has been to wait a few days for dependencies to straighten out. Sometimes waiting helps, other times not.
 
I guess this is why Siduction Linux, based on Debian sid and always installing the very latest packages, recommends always doing dist-upgrade. But, it seems that Update Manager always does dist-upgrade, too. Is this a proper interpretation?
 
Didn't you used to have to run "update-manager -d" to get a dist-upgrade? Has this changed?
 
Thanks,
Tim
 Well, yes, it's true...

---


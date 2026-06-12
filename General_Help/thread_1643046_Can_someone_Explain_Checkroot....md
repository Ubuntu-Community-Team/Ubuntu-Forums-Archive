---
title: "Can someone Explain Checkroot...?"
date: 2010-12-11
forum: General Help
---

### Post by tajiknomi on 2010-12-11
[SIZE=2]I had Google it, but didn't get suitable answers their, I want to know everything about ***chroot***....

1)First of all ,what is Chroot? As from name,i can guess a little that it must be use for Checking-root ;)

2)Why we use Chroot...?

3)What are the benefits of it....?

Any Explanation would be Appreciated...

Thanks,
[/SIZE]

---

### Post by sikander3786 on 2010-12-11
What is check root :confused: ?

What are you talking about? Do you mean to check the root file system for errors?

Or [Check Install]("https://help.ubuntu.com/community/CheckInstall")?

Or what?

---

### Post by tajiknomi on 2010-12-11
> **sikander3786 said:**
> What is check root :confused: ?

What are you talking about? Do you mean to check the root file system for errors?

Or [Check Install]("https://help.ubuntu.com/community/CheckInstall")?

Or what?

[SIZE=2]I think you can Guess from it [/SIZE][http://ubuntuforums.org/showthread.php?t=1156240](http://ubuntuforums.org/showthread.php?t=1156240)

[SIZE=2]Sorry for my Ignorance, but i have seen this in most of threads, that's why...[/SIZE]

---

### Post by sikander3786 on 2010-12-11
Hmmmmm. Chroot.

[http://en.wikipedia.org/wiki/Chroot](http://en.wikipedia.org/wiki/Chroot)

[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)

> A chroot on Unix operating systems is an operation that changes the apparent disk root directory for the current running process and its children.

In simple terms, chroot is mostly used to make changes to your Linux install without booting it from the partition. Just by mounting it in another OS or Live CD/USB etc ;-)

The commands you do there, work as if you are booted into the original install and not the other OS or Live CD/USB.

---

### Post by sanderj on 2010-12-11
chroot stands for "change root", not for "check root": It changes the root of the filesystem experienced by the process.

See the URLs given earlier for more info.

---

### Post by tajiknomi on 2010-12-11
> **sikander3786 said:**
> Hmmmmm. Chroot.

[http://en.wikipedia.org/wiki/Chroot](http://en.wikipedia.org/wiki/Chroot)

[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)



In simple terms, chroot is mostly used to make changes to your Linux install without booting it from the partition. Just by mounting it in another OS or Live CD/USB etc ;-)

The commands you do there, work as if you are booted into the original install and not the other OS or Live CD/USB.

[SIZE=2]Soo Silly i am...i thought it is Check-root, so i was searching for check-root, and find nothing excepts bugs pages ..Lolz[/SIZE]
[SIZE=2]
and now i had Used chroot, and i get usefull pages....sorry gyz, i was totally confused ;)
[/SIZE]

---


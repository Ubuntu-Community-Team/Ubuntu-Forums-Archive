---
title: "Troubles with system upgrade"
date: 2011-03-25
forum: General Help
---

### Post by Nomicos on 2011-03-25
Hello. I am using Ubuntu 10.10 Maverick Meekat. I was upgraded my system successfully many times, but last time Ubuntu gives me an errors while I'm upgrading it. There is screenshot (in attachments) with error while upgrading system via Update Manager.

Once, Ubuntu Software Center offers me to install "Broken Deb Packages", but then my Internet connection was dropped off, so I didn't download it. Also, there are errors about some untrusted keys of maverick-repository.

Please, help me. I want to upgrade Ubuntu now. Thanks.

---

### Post by 5149.5 on 2011-03-25
Yet another problem caused by the missing Ubuntu keyerver that has been down for over a week. Very un-professional support.

---

### Post by Nomicos on 2011-03-26
***To 5149.5***:
So, is it server problem? As for my another laptop, I can easily update Ubuntu. Why so? May be, I should do smth with my repositories' lists?

**UPD0**:
There is screenshot with 'apt-get update' output.
Though, 'apt-get upgrade' works correctly.

---

### Post by Old_Grey_Wolf on 2011-03-26
> **Nomicos said:**
> ***To 5149.5***:
So, is it server problem? As for my another laptop, I can easily update Ubuntu. Why so? May be, I should do smth with my repositories' lists?

**UPD0**:
There is screenshot with 'apt-get update' output.
Though, 'apt-get upgrade' works correctly.

You are missing a GPG key. To install it enter```
gpg --keyserver keyserver.ubuntu.com --recv C5D7718106438B87

gpg --export --armor C5D7718106438B87  | sudo apt-key add -
```

---

### Post by Nomicos on 2011-03-27
[I][B]To Old_Gray_Wolf:
[/B][/I]Added. Thanks for support!

---


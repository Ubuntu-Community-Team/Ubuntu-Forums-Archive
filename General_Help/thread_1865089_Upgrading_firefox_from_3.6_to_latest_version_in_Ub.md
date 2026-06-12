---
title: "Upgrading firefox from 3.6 to latest version in Ubuntu 8.04"
date: 2011-10-19
forum: General Help
---

### Post by RedRat on 2011-10-19
I am running ubuntu 8.04 but for some reason, I cannot upgrade Firefox. This morning there was an upgrade supposedly available but I could not check the box to do so. Any ideas as to why i cannot upgrade?

(Yes, I know that I should be running the latest and greatest Ubuntu, but I will upgrade next year.)

---

### Post by philmjones on 2011-10-19
You need to add the repository to your software sources:
```
http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu
```hardy
main

I think 8.04 is Hardy. You should really upgrade to 10.04 at least; it's great!

---

### Post by RedRat on 2011-10-19
> **philmjones said:**
> You need to add the repository to your software sources:
```
http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu
```hardy
main

I think 8.04 is Hardy. You should really upgrade to 10.04 at least; it's great!
I already have this in my sources list. This morning I got the notification that there were upgrades, and Firefox was there, but I could not turn on the radio button.

---

### Post by ajgreeny on 2011-10-19
8.04 is not supported any more for the desktop version, only the server, so I also recommend that you update to 10.04 as there will be no more updated versions of anything from the repos for 8.04.

---

### Post by d.atanasov on 2011-10-19
Like [ajgreeny]("http://ubuntuforums.org/member.php?u=27747") pointed out you are no longer supported.
I`m using Karmic Koala 9.10 and what I do is just manually download the latest firefox from the web. 
And later use it just by symlink the executable script to /usr/bin/ I don`t like to really change my Ubuntu. And this is because not every new thing is great. It has a lot of troubles too...

---

### Post by philmjones on 2011-10-19
> **RedRat said:**
> I already have this in my sources list. This morning I got the notification that there were upgrades, and Firefox was there, but I could not turn on the radio button.

You got me stumped then, never seen that before. Have you tried using the terminal to upgrade packages?

---

### Post by RedRat on 2011-10-19
> **philmjones said:**
> You got me stumped then, never seen that before. Have you tried using the terminal to upgrade packages?
I am suspecting that Firefox 7, which is available from Mozilla, is not supported by 8.04 I guess. 

I agree with [ajgreeny]("http://ubuntuforums.org/member.php?u=27747") and [d.atanasov]("http://ubuntuforums.org/member.php?u=1161983") that I should upgrade and I will next year to 12.04. I run 10.04 on my laptop and it upgrades Firefox very well. 

I plan to upgrade my system at the same time, new hard drive and added memory. I am running 8.04 on a Dell Inspiron N that is now about 5 years old and only 2GB memory. even FF 3 runs poorly on it. So for the time being, I will just wait until I upgrade the system.

---


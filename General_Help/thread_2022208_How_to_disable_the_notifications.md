---
title: "How to disable the notifications?"
date: 2012-07-10
forum: General Help
---

### Post by woodyg on 2012-07-10
How can I switch off/disable the notifications (in Lubuntu 12.04) that appear in the top-right corner whenever something has happened regarding downloads, battery, wifi etc. I find of very little value and rather annoying.

---

### Post by kalehrl on 2012-07-10
Go to Preferences - Desktop Session Settings and uncheck 'Notification Daemon'.
Reboot or log out/log in again.

---

### Post by woodyg on 2012-07-10
> **kalehrl said:**
> uncheck 'Notification Daemon'

It is already unchecked.

---

### Post by woodyg on 2012-07-16
Any other ideas?

---

### Post by woodyg on 2012-07-20
Am I the only Lubuntu user with this issue?

---

### Post by Apolyonn on 2012-07-21
I'm using 12.04 and was able to just remove the notification daemon altogether (they were getting annoying as hell).  I really have no use for it, and I'd like to imagine it's not that big of a deal since I typically know what's going on in my DE.

```
sudo apt-get remove notification-daemon
```

---

### Post by woodyg on 2012-07-22
> **Apolyonn said:**
> I'm using 12.04 and was able to just remove the notification daemon altogether (they were getting annoying as hell).  I really have no use for it, and I'd like to imagine it's not that big of a deal since I typically know what's going on in my DE.

```
sudo apt-get remove notification-daemon
```

Thanks! This seems to have worked. :D

---

### Post by cheatos on 2012-11-25
Hi there,

I also want to remove the notifications but however when I try to enter the code you posted here, it says that it will remove lubuntu-desktop aswell.
Isn't this my Desktop environment and without it I won't have a GUI anymore?

Thanks for your help

---

### Post by woodyg on 2012-11-25
> **cheatos said:**
> ...it says that it will remove lubuntu-desktop aswell.
Isn't this my Desktop environment and without it I won't have a GUI anymore?

Thanks for your help

It was a while ago so I don't remember the details. I do however remember that when removing SOMETHING from the system, I got these kind of frightening messages. In the end, nothing bad happened though. Whether this was when I got rid of the notifications, that I cannot say 100% for sure. Anyway, it wasn't my primary system, so I figured I could take a gamble at the time... Sorry that I can't be of more help.

---

### Post by JKyleOKC on 2012-11-25
I believe that lubuntu-desktop is a sort of "dummy" package, that lists as dependencies all of the packages that need to be in your system for the GUI to work, but doesn't actually install anything at all itself. That's the case with the other "-desktop" packages and I would expect lubuntu to work the same way.

If that's the only package listed to be removed, you'll probably be safe in proceeding. However you may want to wait a bit longer in hopes that someone actually involved with lubuntu pops into the thread with a definitive answer.

---


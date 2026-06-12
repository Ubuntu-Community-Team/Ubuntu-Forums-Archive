---
title: "What are the Gmail Notifier Check Interval units?"
date: 2010-05-13
forum: General Help
---

### Post by Rytron on 2010-05-13
Hi.
What are the Gmail Notifier Check Interval units? Would they be in milliseconds?

---

### Post by howefield on 2010-05-13
Seconds. (I'm sure previous versions of Gmail notifier had this option named as "Mail Checking Interval (seconds)" or something like that.

But easy enough for you to check it out.

Set it to something like 300, or whatever, then send yourself an email...

---

### Post by Rytron on 2010-05-13
> **howefield said:**
> Seconds. (I'm sure previous versions of Gmail notifier had this option named as "Mail Checking Interval (seconds)" or something like that.

But easy enough for you to check it out.

Set it to something like 300, or whatever, then send yourself an email...

Hi howefield, I will try your way.

Out of curiosity I tried this in Google:
20 seconds = 20 000 milliseconds

---

### Post by howefield on 2010-05-13
> **Rytron said:**
> Hi howefield, I will try your way.

Out of curiosity I tried this in Google:
20 seconds = 20 000 milliseconds

Checking mail every 20 seconds would be pretty unusual :)

---

### Post by Rytron on 2010-05-13
I sent myself three emails.

For the first one, Gmail Notifier took about 8 seconds to notify me.
For the second one, Gmail Notifier took about 16 seconds to notify me.
For the third one, Gmail Notifier took about 22 seconds to notify me.

---

### Post by Rytron on 2010-05-13
I've decided to switch to gnome-gmail-notifier. It supports multiple Gmail accounts. :)

```
sudo apt-get install gnome-gmail-notifier
```

---

### Post by Rytron on 2010-05-14
I booted today and gnome-gmail-notifier is not checking for new emails.

I've now settled for CheckGmail.

```
sudo apt-get install checkgmail
```

---


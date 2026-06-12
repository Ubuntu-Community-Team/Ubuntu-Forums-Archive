---
title: "please help"
date: 2006-02-21
forum: General Help
---

### Post by Chimona on 2006-02-21
every time i type sudo it gives me this error, "unable to look up <hostname> via gethostbyname() "

is this because i didn't install the networking stuff with the installation, i've only got a usb 802.11g adapter.

---

### Post by gatorgrips on 2006-02-21
that doesn't seem like a network error. 
does everything load "ok" when it's booting?
like... "setting hostname...    ok" or something instead of "failed"?

---

### Post by Chimona on 2006-02-21
temporary failure in name resolution, when i boot in recovery mode i can see it.

---

### Post by gatorgrips on 2006-02-21
man i have no idea.
i'm not good at this stuff.
all i know is it's PROBABLY not a network problem. 
but i have no fuckin clue, so it very well could be.
but it's most likely not. 

lol i know that doesn't really help you at all.
sorry. 

maybe someone else knows (bump)

---

### Post by GeneralZod on 2006-02-21
The first line of your /etc/hosts file should read something like this:

```

127.0.0.1 localhost.localdomain localhost nameofmycomputer

```

---


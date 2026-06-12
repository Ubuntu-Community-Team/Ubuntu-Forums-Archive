---
title: "need software that will notify me of changes in remote log"
date: 2009-11-16
forum: General Help
---

### Post by nerdy_kid on 2009-11-16
hi all, i have an apache2 server running on a remote computer, and i want to be notified every time a new entry apears in the log.  I need a piece of software to do this...(preferably a plasma widget)

thanks

---

### Post by Giblet5 on 2009-11-16
Pretty easy to do with Python or most other scripting languages. You'll have to write it, though. There's no market for such stuff (other than you) and software development is all about fame, glory, wealth, and all the hot hot wimmenz who are natutrally attracted to mad coding skillz.

You could also look at Conky... It's kinda made for this stuff.

I'll do it for 1/10th ounce of gold per hour.

---

### Post by nerdy_kid on 2009-11-16
:(

darn, i was hoping to escape writing it myself....

and no thanks; ill pass on your kind offer to write one for me :D

---

### Post by phillw on 2009-11-16
> **nerdy_kid said:**
> hi all, i have an apache2 server running on a remote computer, and i want to be notified every time a new entry apears in the log.  I need a piece of software to do this...(preferably a plasma widget)

thanks

If you mean in /var/logs ... try Ossec.

You can configure it up to email you.

Phill.

---

### Post by Giblet5 on 2009-11-16
You can also keep a terminal window open to that remote server via ssh.

Just run the following command and you will see each new log entry as it occurs:

```
tail -f /var/log/apache2/error.log
```

if you want errors, or

```
tail -f /var/log/apache2/access.log
```

if you want to see people hitting your web.

---

### Post by nerdy_kid on 2009-11-16
thanks for the suggustions!

i think ill try the tail -f, thanks all!

---


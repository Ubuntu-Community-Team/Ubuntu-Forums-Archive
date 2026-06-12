---
title: "How do I find out why Evolution crashed?"
date: 2009-12-16
forum: General Help
---

### Post by mazz0 on 2009-12-16
God I hate Evolution (the email programme, not the thoery).

Why doesn't it give you an error message when it crashes?  I HATE that!

Anyway, rant over, is there a log somewhere I can look in to find out why it crashed?

I'm gonna have to use Thunderbird, I reckon, but then the notifications won't match the system's :(

---

### Post by akakingess on 2009-12-16
I believe if you launched Evolution from the terminal that it would keep a log of possibly why it would crash during that sesstion, but I know that doesn't help you with why it crashed in the past, but if you could recreate the problem and maybe move on to troubleshoot from there?

---

### Post by mazz0 on 2009-12-22
You're a genius, sir!

Here's the error:
```
exchange-mapi-connection.c:1317: Leaving exchange_mapi_connection_fetch_items: folder-id 9C91920600000003 Segmentation fault
```

I suspect it's something in a particular message, but how do I find out which one?  If I knew which I could delete it using Outlook or Webview.

---

### Post by 5BallJuggler on 2009-12-22
```
phil@phil-netbook:~$ evolution

(evolution:11010): atk-bridge-WARNING **: AT_SPI_REGISTRY was not started at session startup.

(evolution:11010): atk-bridge-WARNING **: IOR not set.

(evolution:11010): atk-bridge-WARNING **: Could not locate registry

(evolution:11010): atk-bridge-WARNING **: AT_SPI_REGISTRY was not started at session startup.

(evolution:11010): atk-bridge-WARNING **: IOR not set.

(evolution:11010): atk-bridge-WARNING **: Could not locate registry
** (evolution:11010): DEBUG: mailto URL command: evolution %s
** (evolution:11010): DEBUG: mailto URL program: evolution

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:11010): DEBUG: New Indicator: Inbox pop:
** (evolution:11010): DEBUG: New Inbox inidicator
** (evolution:11010): DEBUG: Number of email accounts: 2
** (evolution:11010): DEBUG: EI: SHELL STARTUP

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:11010): DEBUG: EI: mail_read_notify
** (evolution:11010): DEBUG: Setting Inbox to 0 unread messages
** (evolution:11010): DEBUG: Setting Inbox to 0 unread messages

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:11010): DEBUG: EI: mail_read_notify
** (evolution:11010): DEBUG: Setting Inbox to 0 unread messages
** (evolution:11010): DEBUG: Setting Inbox to 0 unread messages

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:11010): DEBUG: EI: mail_read_notify
** (evolution:11010): DEBUG: Setting Inbox to 0 unread messages
** (evolution:11010): DEBUG: Setting Inbox to 0 unread messages

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:11010): DEBUG: EI: mail_read_notify
** (evolution:11010): DEBUG: Setting Inbox to 0 unread messages
** (evolution:11010): DEBUG: Setting Inbox to 0 unread messages

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:11010): DEBUG: EI: mail_read_notify
** (evolution:11010): DEBUG: Setting Inbox to 0 unread messages
** (evolution:11010): DEBUG: Setting Inbox to 0 unread messages

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:11010): DEBUG: EI: mail_read_notify
** (evolution:11010): DEBUG: Setting Inbox to 0 unread messages
** (evolution:11010): DEBUG: Setting Inbox to 0 unread messages

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:11010): DEBUG: EI: mail_read_notify
** (evolution:11010): DEBUG: Setting Inbox to 0 unread messages
** (evolution:11010): DEBUG: Setting Inbox to 0 unread messages

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:11010): DEBUG: EI: mail_read_notify
** (evolution:11010): DEBUG: Setting Inbox to 0 unread messages
** (evolution:11010): DEBUG: Setting Inbox to 0 unread messages

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:11010): DEBUG: EI: mail_read_notify
** (evolution:11010): DEBUG: Setting Inbox to 0 unread messages
** (evolution:11010): DEBUG: Setting Inbox to 0 unread messages

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:11010): DEBUG: EI: mail_read_notify
** (evolution:11010): DEBUG: Setting Inbox to 0 unread messages
** (evolution:11010): DEBUG: Setting Inbox to 0 unread messages

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:11010): DEBUG: EI: mail_read_notify
** (evolution:11010): DEBUG: Setting Inbox to 0 unread messages
** (evolution:11010): DEBUG: Setting Inbox to 0 unread messages

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:11010): DEBUG: EI: mail_read_notify
** (evolution:11010): DEBUG: Setting Inbox to 0 unread messages
** (evolution:11010): DEBUG: Setting Inbox to 0 unread messages

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:11010): DEBUG: EI: mail_read_notify
** (evolution:11010): DEBUG: Setting Inbox to 0 unread messages
** (evolution:11010): DEBUG: Setting Inbox to 0 unread messages

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:11010): DEBUG: EI: mail_read_notify
** (evolution:11010): DEBUG: Setting Inbox to 0 unread messages
** (evolution:11010): DEBUG: Setting Inbox to 0 unread messages

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:11010): DEBUG: EI: mail_read_notify
** (evolution:11010): DEBUG: Setting Inbox to 0 unread messages
** (evolution:11010): DEBUG: Setting Inbox to 0 unread messages

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:11010): DEBUG: EI: mail_read_notify
** (evolution:11010): DEBUG: Setting Inbox to 0 unread messages
** (evolution:11010): DEBUG: Setting Inbox to 0 unread messages

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:11010): DEBUG: EI: mail_read_notify
** (evolution:11010): DEBUG: Setting Inbox to 0 unread messages
** (evolution:11010): DEBUG: Setting Inbox to 0 unread messages

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:11010): DEBUG: EI: mail_read_notify
** (evolution:11010): DEBUG: Setting Inbox to 0 unread messages
** (evolution:11010): DEBUG: Setting Inbox to 0 unread messages

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

(evolution:11010): gtkhtml-WARNING **: found token with no valid name

(evolution:11010): gtkhtml-WARNING **: found token with no valid name

(evolution:11010): gtkhtml-WARNING **: found token with no valid name

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:11010): DEBUG: EI: mail_read_notify
** (evolution:11010): DEBUG: Setting Inbox to 0 unread messages
** (evolution:11010): DEBUG: Setting Inbox to 0 unread messages

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:11010): DEBUG: EI: mail_read_notify
** (evolution:11010): DEBUG: Setting Inbox to 0 unread messages
** (evolution:11010): DEBUG: Setting Inbox to 0 unread messages

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:11010): DEBUG: EI: mail_read_notify
** (evolution:11010): DEBUG: Setting Inbox to 0 unread messages
** (evolution:11010): DEBUG: Setting Inbox to 0 unread messages

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:11010): DEBUG: EI: mail_read_notify
** (evolution:11010): DEBUG: Setting Inbox to 0 unread messages
** (evolution:11010): DEBUG: Setting Inbox to 0 unread messages

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:11010): DEBUG: EI: mail_read_notify
** (evolution:11010): DEBUG: Setting Inbox to 0 unread messages
** (evolution:11010): DEBUG: Setting Inbox to 0 unread messages

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:11010): DEBUG: EI: mail_read_notify
** (evolution:11010): DEBUG: Setting Inbox to 0 unread messages
** (evolution:11010): DEBUG: Setting Inbox to 0 unread messages

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:11010): DEBUG: EI: mail_read_notify
** (evolution:11010): DEBUG: Setting Inbox to 0 unread messages
** (evolution:11010): DEBUG: Setting Inbox to 0 unread messages

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:11010): DEBUG: EI: mail_read_notify
** (evolution:11010): DEBUG: Setting Inbox to 0 unread messages
** (evolution:11010): DEBUG: Setting Inbox to 0 unread messages

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:11010): DEBUG: EI: mail_read_notify
** (evolution:11010): DEBUG: Setting Inbox to 0 unread messages
** (evolution:11010): DEBUG: Setting Inbox to 0 unread messages

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:11010): DEBUG: EI: mail_read_notify
** (evolution:11010): DEBUG: Setting Inbox to 0 unread messages
** (evolution:11010): DEBUG: Setting Inbox to 0 unread messages

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:11010): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:11010): DEBUG: EI: mail_read_notify
** (evolution:11010): DEBUG: Setting Inbox to 0 unread messages
** (evolution:11010): DEBUG: Setting Inbox to 0 unread messages
Segmentation fault
```

I have the same final error, but the entire session looks riddled with critical errors.

Does anyone else see the same issue?

Phil

---

### Post by 5BallJuggler on 2009-12-22
I've just backed up all of the data, and removed Evolution
on re-install the problem is still present.

---

### Post by llawwehttam on 2009-12-22
I had a similar problem when I was using 8.10 so I went to thunderbird. Works better for me but I'd still like to know what caused the problem.

---

### Post by mazz0 on 2009-12-22
Phil - I had a load of criticals like that too, but since I've never run it in a terminal before I don't know if they're normal.

I've switched to Thunderbird for now, but I can't get it to send messages via Exchange (or lookup contacts), only read.  I'm using Outlook in VirtualBox to send emails at the moment :(

---


---
title: "Monitor other IMAP folders in Messaging Menu"
date: 2010-10-27
forum: General Help
---

### Post by danduq on 2010-10-27
I've finally found out how to add Thunderbird to and remove Evolution from the Messaging Menu. the only problem is that the Thunderbird notifier will only monitor my inbox.

I use procmail to filter messages server-side, and want to check for the presence of new messages in another folder. The only app I've found that can do this so far is mail-notification, which can be pointed to directories other than Inbox.

Any idea if/how I can integrate this into the Messaging Menu interface? Or are there any other solutions?

---

### Post by blueridgedog on 2010-10-27
Conky can do what you want, but you can not integrate it into the Messaging Menu.

From the conky docs regarding imap_unseen:

```
Displays the number of unseen messages in your global IMAP inbox by default. You can define individual IMAP inboxes separately by passing arguments to this object. Arguments are: "host user pass [-i interval (in seconds)] [-f 'folder'] [-p port] [-e 'command'] [-r retries]". Default port is 143, default folder is 'INBOX', default interval is 5 minutes, and default number of retries before giving up is 5. If the password is supplied as '*', you will be prompted to enter the password when Conky starts.
```

---

### Post by danduq on 2010-10-28
Thanks, but I already have a functioning monitor for the IMAP folder I want to watch. I would just like something that integrates with the Messaging Menu so that I don't end up with loads of icons.

The mail-notification icon also has a pale background, so doesn't look good on the new Ambiance themed panel.

---


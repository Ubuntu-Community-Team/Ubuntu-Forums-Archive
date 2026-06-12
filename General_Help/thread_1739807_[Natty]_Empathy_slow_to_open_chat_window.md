---
title: "[Natty] Empathy slow to open chat window"
date: 2011-04-26
forum: General Help
---

### Post by Kelvari on 2011-04-26
I'm currently using Ubuntu Natty and have noticed a severe lag - sometimes upwards of 30 seconds - when opening a conversation window in Empathy. Is there anything that I could do to speed it up a bit?

Computer Specs
AMD Athlon 64x2 3800+ (2.4 GHz)
2GB (512MB x4) DDR-400 (PC3200)
nVidia GeForce 7600 GT KO (PCI-express; restricted drivers)

---

### Post by Mark Phelps on 2011-04-26
While Ubuntu 11.04 remains in testing, you will get better and faster responses if you post your 11.04 questions to the Natty Development forum.  That is located at: Other Community Discussions --> Development & Programming --> Natty Narwhal Testing and Discussion.

Good Luck

---

### Post by Kelvari on 2011-04-29
Sadly, I checked back here late, and the forum's closed, so I guess I'll just go ahead and leave it here...

Any help would be appreciated, though.

---

### Post by juanchito2006 on 2011-05-01
I'm experiencing this same issue, pretty annoying, and a regression itself. Have you already reported in Launchpad?

---

### Post by pablomme on 2011-05-03
By any chance, do you have chat logs disabled? My girlfriend is seeing this and I'm not, and this is the only difference in empathy's configuration.

---

### Post by pablomme on 2011-05-03
Going through the output from "EMPATHY_DEBUG=all empathy" I see this at the place where it takes most of the time between the user trying to open the chat window and the window opening (including one line after and one before):

> 
Tue May  3 22:00:29 BST 2011 (empathy:19837): empathy-DEBUG: individual_view_expand_idle_cb: individual_view_expand_idle_cb
Tue May  3 22:00:35 BST 2011 (empathy:19837): empathy-DEBUG: logger_favourite_contacts_get_cb: Failed to get the FavouriteContacts property: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(empathy:19837): telepathy-WARNING **: Couldn't get list of favorite contacts: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Tue May  3 22:00:47 BST 2011 (empathy:19837): tp-glib/channel-DEBUG: tp_channel_init: 0x16422a0


Any ideas?

NB, dates on standard output are mine, standard error has no dates.

---

### Post by pablomme on 2011-05-03
It turned out that telepathy-logger had hung, using 100% CPU. Killing telepathy-logger resolved the problem. I don't know if it will come back, though.

---


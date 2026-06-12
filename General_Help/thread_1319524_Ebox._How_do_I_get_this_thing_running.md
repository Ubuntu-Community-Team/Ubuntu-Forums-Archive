---
title: "Ebox. How do I get this thing running?"
date: 2009-11-08
forum: General Help
---

### Post by Roasted on 2009-11-08
So I installed Ebox, and the guide I used said it would prompt me during the installation to put in an IP address - I assume of the server I'm using. Well, it didn't. I installed/purged/removed it about 4 times. It didn't.

So now, I'm stuck. All it asked is HTTPS port (default 443, left it unchanged) and my password to set up for the ebox administrator account.

I hate to be very broad - but uh, I'm kind of stuck at a blunt wall here. What do I do now?

---

### Post by foolano on 2009-11-09
Now you can access the web UI from other computer using a browser: https://<ebox-ip>

Take a look at the doc:

[http://doc.ebox-platform.com](http://doc.ebox-platform.com)

---

### Post by Roasted on 2009-11-09
That's weird... I installed ebox on my ubuntu server and tried its IP and it didn't work. I'll work on it more later today...

---

### Post by Roasted on 2009-11-09
All righty, we're up and running. I'm trying to figure out how to add modules now. I'm a little bit confused because I'm reading that they come disabled by default, but I can enable them. I don't see them listed under module status to be enabled.

Are they tied up in a separate package that I need to grab? If so - where do I grab it? In particular I'm looking for the Samba module.

EDIT - Nevermind. I got the other modules installed. I'm a little confused though. When I set up a new samba share, it doesn't create it on the server. Do I have to create directories on the server first and then create them on ebox to link them together?

---


---
title: "Send email from the terminal (with multiple account support)"
date: 2011-10-01
forum: General Help
---

### Post by therealop on 2011-10-01
I'm looking for a way to send (smtp) emails from the terminal, with multiple account support.

I need a way to set the username, password, etc.. all in the command. similar to:
mail -pass"password" -user"some_user1@some_address" -server"smtp.some_server.com" -port"465" -to"some_user2@some_address.com" -subject"subject" -message"message"

I've been using ssmtp, and msmtp, but they dont support the aforementioned options.

I'm pretty compitent when it comes to the terminal, so I dont need you to write the code for me, just point me in the right direction.:)

EDIT: SOLVED!

I'm now using openssl

---


---
title: "[SSH] Don't stop the activity when  closing client"
date: 2010-08-12
forum: General Help
---

### Post by j_arquimbau on 2010-08-12
My situation is de next:

I've got a client running ubuntu (10.04) and a server running FreeBSD (8.1). I connected via SSH the client to the server and begun making endless compilations. Now I have to shut down the client but I wish the server didn't stop compilating. Is that possible? When I closed the gnome-terminal from the client yesterday, the server stopped. Is there a way to do what I want? 

Thank you!

---

### Post by Fludizz on 2010-08-12
Install screen on your server :)

You can then start a shell in a "screen" session and this shell will remain active and working. You can reattach to the existing screen when you log in again :)

Check the manpage of screen after you installed it, you can do a lot with it :)

---

### Post by j_arquimbau on 2010-08-12
> **Fludizz said:**
> Install screen on your server :)

You can then start a shell in a "screen" session and this shell will remain active and working. You can reattach to the existing screen when you log in again :)

Check the manpage of screen after you installed it, you can do a lot with it :)

Thank you for your quick answer!:D

---

### Post by bilkay on 2010-08-23
$ at now
>{yourscript}
>^D
$ exit

yourscript will continue to run after you log out.

---


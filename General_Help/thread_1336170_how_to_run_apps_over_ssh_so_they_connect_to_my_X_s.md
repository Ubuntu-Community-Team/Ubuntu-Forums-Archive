---
title: "how to run apps over ssh so they connect to my X server"
date: 2009-11-24
forum: General Help
---

### Post by nerdy_kid on 2009-11-24
ok, so i want to ssh into a server/desktop of mine, and set the DISPLAY env var so that say gedit pops up on my pc.  I know this is possible, i just cant figure out how....

thanks

---

### Post by polki@mac.com on 2009-11-24
Could it be something like this you're looking for?

ssh -Y user@server

Just off the top of my head, it was all the sprang to mind...

EDIT: Make sure xforward = yes on the server.

---

### Post by nerdy_kid on 2009-11-24
ok, thanks, i did some googling and ended up running:

```

 ssh -Y -o ForwardX11=yes remote-pc

```

i got an authencation error:

```

/usr/bin/X11/xauth:  error in locking authority file /home/____/.Xauthority
____@____-desktop:~$ gedit
X11 connection rejected because of wrong authentication.

```

---

### Post by nerdy_kid on 2009-11-24
never mind, i got it fixed: had to delete some Xauthority files from the server: thanks for the hint!

---

### Post by polki@mac.com on 2009-11-25
Good to hear you solved it!

Don't forget to mark the thread solved.

Cheers!

---


---
title: "Really bad problem with my Ubuntu Install"
date: 2009-07-15
forum: General Help
---

### Post by IceRayn on 2009-07-15
Hello, 

I made a very stupid mistake, and managed to nuke my home directory. Kind of.

I used to use the root terminal all the time, not sudo, as in su root, but I have stopped that practice now, and wanted to reverse the changes to my home directory, so I entered (stupid mistake) sudo chown -R (my name) /home/(my name)

Now when I try to log in, it throws errors at me about dbus, and other things. My question is, is there any way to reverse it? I can still log in to the root user account, (Thank god I enabled it.)

Thank You,
IceRayn

Never mind, my subconscious for some reason wanted me to enter that it be owned by root. The problem is fixed by entering my root account, su name sudo chown name -R /home/name

---


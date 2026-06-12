---
title: "Samba Server"
date: 2012-07-30
forum: General Help
---

### Post by jdm2 on 2012-07-30
I'm setting up a samba server again and it has been a couple of years since I did it last.  I have all of it set up.  This time I'm just using the home folders for the users to be able to use.  I know this isn't the best way, but they won't be logging in to use the box.  They are just using it for a file server.  I was wondering if there was a way to hide the . files from the window clients that will be logging in to use this server if not can I just change the permission so they can't write to those files.  I know you need some of these files to login or for ssh, but if all they are doing is logging over the network for a samba share do they really need permission to access these files?

Thanks for the help.

Sincerely yours;

jdm2

---

### Post by luvshines on 2012-07-31
Guess you are looking for ```
hide dot files
``` from smb.conf
Haven't used it myself, but shud help you

---

### Post by jdm2 on 2012-08-04
Thanks for the help.  Will give that a try.

---


---
title: "Gimp launch error"
date: 2011-05-19
forum: General Help
---

### Post by electronictim on 2011-05-19
Hi all.

When I try to launch gimp I get the following message:
__________________
It appears that you are using GIMP for the first time.  GIMP will now create a folder named '/home/theeb/.gimp-2.6' and copy some files to it.

Creating folder '/home/theeb/.gimp-2.6'...
Cannot create folder '/home/theeb/.gimp-2.6': Permission denied
__________________

From terminal, 'gimp' returns same message, but 'sudo gimp' and it starts up fine?

What's gone on with my permissions?!  I've installed gimp a number of times and never run into this...

Thanks.

---

### Post by TeoBigusGeekus on 2011-05-19
Can you create the folder yourself before launching gimp?
Even if it works, I'd check for ownership your whole home folder.

---


---
title: "Missing folder?"
date: 2010-03-26
forum: General Help
---

### Post by cityydude on 2010-03-26
I'm a noobie and trying my first server. Installed Ubuntu 8.04 LS 32 bit. Got to the point where I get the "It works" message and can connect through my SFTP  (as long as shorewall is off but that's a whole other nightmare!) 

Problem is I'm supposed to upload all the files to a folder called /var/www only problem is it does not exist on the server. Or perhaps its there but hidden and I don't know how to locate it? If its not there can it be created? If so what would be the command to create it and would that work?  There has to be some reason why its not there. According to the instructions I followed to install Ubuntu its supposed to be there.

Any help would be appreciated.

---

### Post by Barriehie on 2010-03-28
/var/www starts at the root of the file system.  Your home dir is /home/*username* and /var/www is the same way.  From terminal go:
```

cd ..  # takes you to /home/
cd ..  # takes you to /
cd ./var  # now you're in /var directory
cd ./www  # now you're in /var/www

or

cd /var/www # to get there directly from anywhere

```

---


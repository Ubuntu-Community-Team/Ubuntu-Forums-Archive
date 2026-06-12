---
title: "Can't change permissions or owner of folder"
date: 2011-01-09
forum: General Help
---

### Post by dchurch24 on 2011-01-09
Hi,

I have a folder in which I have ripped all my DVDs, I've also sorted them in order of genre, and I have one subfolder called "Kids" - which, you guessed it, it where the kids films go.
I generally sorted them into folders, but I have about 40 in there that all start with the year, I used different ripping software that somehow extracted the date of the film from the net. I've just written a script to extract the name of the file, create a folder for it, then copy the file to the folder. I tested it locally and it works like a charm. However, on my network drive where the films are all stored (a WD MyBookWorld), it won't even let me change the script to +x.
When I look, all the files in that folder are owned by www-data for some reason.
I tried to chown them to me, but I keep getting the same error, even if I am in as root:

```

chown: changing ownership of `/media/mybook/Videos/Kids/': Invalid argument

```

```

chmod: changing permissions of `cleanup.sh': Permission denied

```

I'm a bit stuck to be honest, I have no idea how the files/folder came to be owned by www-data for one thing, and I can't understand why I can't change them.

Is there anyone who is better at this than me that could kindly point me in the right direction please?

EDIT: Forgot to mention, the drive is shared on all machines by using smbmount. On the MyBook there is no user of the name to which I want to change the owner to, could that be it?

---


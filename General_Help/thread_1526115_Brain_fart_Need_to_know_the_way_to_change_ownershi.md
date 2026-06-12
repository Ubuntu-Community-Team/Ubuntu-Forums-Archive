---
title: "Brain fart: Need to know the way to change ownership of a file"
date: 2010-07-07
forum: General Help
---

### Post by winterfire on 2010-07-07
I need to install a script into my Gimp folder which is owned by root. I tried "chown my name usr/share/gimp2.0/scripts" in terminal, but it tells me folder does not exist. I know I'm missing something, but I haven't done this in a while, so I'm not sure what it is. Any help?
                                      Thanks

---

### Post by marshmallow1304 on 2010-07-07
There should be a leading slash: /usr/...
Also, you'll probably need to use
```
sudo chown <username> /usr/...
```


It may be easier to just copy the file there with root privileges:
```
sudo cp /location/of/script /usr/share/gimp2.0/scripts/
```
unless you *need* that directory to be owned by you.

---

### Post by winterfire on 2010-07-08
> There should be a leading slash: /usr/...

 Aah yes,the old leading slash trick.:) Thanks.

---


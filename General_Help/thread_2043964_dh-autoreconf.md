---
title: "dh-autoreconf"
date: 2012-08-17
forum: General Help
---

### Post by drakorg on 2012-08-17
Hello there, I'm having trouble installing some libraries that seem to depend on dh-autoreconf. However, this package is not available through apt-get, should it? Is it an active regular package? Or the libraries that I'm trying to install are more likely "broken"?

PS: I even tried downloading the .deb from debian page, but it then required an even newer version of libtool, which, again, I wasn't able to acquire by means of apt-get. My fear is if I start to messup with installing manually, all the deps further on will start to get messy.

Thank you,
Eduardo.

---

### Post by ads52 on 2012-08-17
Certainly available here, on Precise Pangolin:

```

andrew@corinth:~$ **[COLOR="Red"]apt-cache search dh-autoreconf[/COLOR]**
dh-autoreconf - debhelper add-on to call autoreconf and clean up after the build

```

Try this command on your system and see what comes up :).

---


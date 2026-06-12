---
title: "Where is the default PATH set?"
date: 2010-05-14
forum: General Help
---

### Post by jsbiff on 2010-05-14
I'm using Ubuntu 9.10, and trying to figure out where my shell is getting the 'default' PATH environment variable from?

Historically, Linux distros used to put a PATH statement in /etc/profile, or maybe /etc/bash.bashrc. There doesn't appear to be any such statement in either file.

I also noticed that /etc/profile invokes scripts in /etc/profile.d, but it doesn't appear that either of the two files in that directory are setting the path.

So, I'm not sure how bash is getting any path? Does it have a default path hard-coded into the executable, and it's just using the default path?

If I want to globally add a directory to the path, what's the 'best' place to put it? I'm thinking maybe in a file in /etc/profile.d? That way, if an Ubuntu package update overwrite /etc/profile, my local change isn't lost?

---

### Post by fancypiper on 2010-05-14
I hope this helps somewhat.  You can show your current paths with this command:

# List paths
echo -e ${PATH//:/\\n}

I can't give specifics on what you are wanting.

---

### Post by sisco311 on 2010-05-14
The system-wide PATH variable is defined in /etc/environment.

---


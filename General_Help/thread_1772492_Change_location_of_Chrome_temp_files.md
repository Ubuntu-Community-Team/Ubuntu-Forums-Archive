---
title: "Change location of Chrome temp files?"
date: 2011-05-31
forum: General Help
---

### Post by dfarrell07 on 2011-05-31
Is there a way to change the default download location of Chrome temp files? Or perhaps map the current one (/home/user/.cache/chromium/Default/Cache/) to /temp somehow? I have /temp mounted in RAM, and would like Chrome to store its temp files there to boost speed and reduce usage of my Vertex 3 (the other option I would like to move browser temp files to).

I've found some stuff saying its not supported by Chrome, but nothing about it not being possible in Linux by some other method. I'm still searching, and will post back as I learn more.

Thanks for any help!

---

### Post by dfarrell07 on 2011-06-10
Update: I still haven't found a way. All ideas are welcome. :)

---

### Post by BrendanM on 2011-07-16
So here's my solution to this issue. I'm not promising it's the optimal/cleanest way to accomplish this, but it seems to work fine for me.

First, make sure you have a filesystem in RAM somewhere (you mentioned you were already mounting /temp to RAM)

In my case I have the following lines in my /etc/fstab:
```
#Mount /tmp in RAM as per http://brainstorm.ubuntu.com/idea/16244/
tmpfs /tmp tmpfs nodev,nosuid,noexec,mode=1777 0 0
```

Next, create a little bash script that will remove the chromium cache directory, create a new directory in your tmpfs, and then symlink the old location to the new one.

Mine looks like this:

```
#!/bin/bash

rm -r ~/.cache/chromium
mkdir /tmp/chromium
ln -s /tmp/chromium ~/.cache/chromium
```

(yours would presumably have /temp instead of /tmp)

You can save that script anywhere you like, but mine lives at ~/scripts/chromium_tmp_cache.sh

Finally, to make sure that script gets run automatically whenever you login, you'll need to [add it to your .bash_profile file]("http://www.cyberciti.biz/faq/change-bash-profile/") (create this file if it doesn't already exist)

```
~/scripts/chromium_tmp_cache.sh
```

Once you've done that, it will be invoked automatically whenever you log in. I make no promises this will not cause Chromium to freak out, but so far I haven't seen any adverse effects.

---

### Post by dfarrell07 on 2012-09-15
This is a wonderful solution, thank you so much! Simple, fairly clean, quick to implement. Really, thank you for your thoughts! :D

---


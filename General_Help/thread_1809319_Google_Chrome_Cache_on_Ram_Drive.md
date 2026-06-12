---
title: "Google Chrome Cache on Ram Drive"
date: 2011-07-21
forum: General Help
---

### Post by Deathmoon on 2011-07-21
I just upgraded my HDD to a SDD yesterday and I'm in the process of tweaking it.  I first followed these two articles ([#1]("http://www.howtogeek.com/62761/how-to-tweak-your-ssd-in-ubuntu-for-better-performance/") and [#2]("https://wiki.ubuntu.com/MagicFab/SSDchecklist")) and then I started to look for a way to move my Google Chrome Cache over to my recently created /tmp (ram drive); unlike Firefox, there is no cache setting therefore I came up with the following:

```
sudo mkdir /tmp/google-chrome
```

then I deleted the /home/username/.cache/google-chrome directory and created a shortcut to the newly created directly above

```
sudo gedit /etc/init.d/chromecache
```

in the file I placed the following lines of code:

```
/bin/mkdir /tmp/google-chrome
chown username:username /tmp/google-chrome -R
```

Save & Exit.

```
sudo chmod +x /etc/init.d/chromecache
sudo update-rc.d chromecache defaults
```

That's it.

---

### Post by ron999 on 2011-07-21
Hi
I have my Firefox cache in RAM.

Previously I did same as you, mounted a **/tmp** folder in RAM each time.
But now I use the **/dev/shm** folder instead.
Apparently /dev/shm is a ramdisk that gets mounted by Ubuntu automatically at bootup.

So instead of this:-
"Find/create this key: browser.cache.disk.parent_directory. Set it to /tmp"

My Firefox browser.cache.disk.parent_directory is /dev/shm

Perhaps this location will be suitable for Chrome too.:)

---


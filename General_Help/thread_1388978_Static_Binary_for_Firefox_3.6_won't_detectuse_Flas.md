---
title: "Static Binary for Firefox 3.6 won't detect/use Flash"
date: 2010-01-23
forum: General Help
---

### Post by Mike_IronFist on 2010-01-23
Hey, I'm running Ubuntu Karmic 9.10, I just downloaded Firefox 3.6 (the static tarball package, not the source code) and it runs smoother than 3.5, but it has one small issue: it won't use my flash plugin!

I don't want to install via APT (the Mozilla Daily Builds PPA breaks my Firefox installation) but I DO want to use Firefox 3.6, so how do I make the static binary version of Firefox 3.6 use flash?

---

### Post by lovinglinux on 2010-01-23
Go to /usr/lib/mozilla/plugins and copy the plugin libflashplayer.so then paste it inside your plugin folder in the extracted firefox directory.

You could alternatively create a symlink so, you don't need to copy it again when you update flash.

Assuming you have extracted firefox into /opt, then:

```
sudo ln -s /usr/lib/mozilla/plugins/libflashplayer.so /opt/firefox/plugins/libflashplayer.so
```

Better would be to create a symlink for the entire plugin folder, so other plugins get recognized too.

```
mv  /opt/firefox/plugins  /opt/firefox/plugins.backup
sudo ln -s /usr/lib/mozilla/plugins /opt/firefox/plugins
```

---

### Post by Mike_IronFist on 2010-01-24
> **lovinglinux said:**
> Go to /usr/lib/mozilla/plugins and copy the plugin libflashplayer.so then paste it inside your plugin folder in the extracted firefox directory.

You could alternatively create a symlink so, you don't need to copy it again when you update flash.

Assuming you have extracted firefox into /opt, then:

```
sudo ln -s /usr/lib/mozilla/plugins/libflashplayer.so /opt/firefox/plugins/libflashplayer.so
```

Better would be to create a symlink for the entire plugin folder, so other plugins get recognized too.

```
mv  /opt/firefox/plugins  /opt/firefox/plugins.backup
sudo ln -s /usr/lib/mozilla/plugins /opt/firefox/plugins
```

Thanks, that worked splendidly! All I had to do grab a 64-bit build and do what you told me, and it worked! Thanks alot.

---

### Post by lovinglinux on 2010-01-24
> **Mike_IronFist said:**
> Thanks, that worked splendidly! All I had to do grab a 64-bit build and do what you told me, and it worked! Thanks alot.

You are welcome.

---


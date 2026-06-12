---
title: "Change default location (path) for Documents, Pictures, etc."
date: 2011-10-10
forum: General Help
---

### Post by scottbomb on 2011-10-10
I'm using Ubuntu 11.04, trying to figure out how I can change the default folder paths for items such as "documents", "music", "pictures", etc. I already have these things on a seperate hard drive that I can easily access (I dual-boot with Win 7 so I work with the files using either OS). It would just be nice and convenient to click on "documents" and have it go to where I actually store my documents. Tweak Ubuntu had a feature to do this but it didn't work. Anyone know where I can go to edit this?

---

### Post by peter d on 2011-10-11
I'm not quite sure this is what you mean, but it might be a work around, so here goes.

Open Nautilus. The short cuts on the left can be deleted. Just right click and click remove. Then drag the new locations from the main pane to replace them.

I hope that achieves what you want.

---

### Post by bodhi.zazen on 2011-10-11
```
rm ~/Dcouments
ln -s /your/other/location/Documents /home/your_user/Documents
```

And on

---

### Post by scottbomb on 2011-10-11
Awesome. Thanks! Learned a new command today.

---


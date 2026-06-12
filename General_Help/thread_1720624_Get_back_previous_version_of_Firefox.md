---
title: "Get back previous version of Firefox?"
date: 2011-04-03
forum: General Help
---

### Post by xdeathcorex on 2011-04-03
So I did an update to Firefox 3.6.16 and now it crashes each time it loads the homepage. I don't want to use Firefox 4 yet because some of the addons are still incompatible.  So, how do I get the previous version of Firefox 3.6.15 for Ubuntu 10.10?  Thanks

---

### Post by WorMzy on 2011-04-03
The old version's installer may still be in /var/cache/apt/archives. If you can find it in there, install it with
```
sudo dpkg -i /var/cache/apt/archives/firefoxwhatever.deb
```

Then lock the package to prevent the system from updating it.

```
echo "firefox hold" | sudo dpkg --set-selections
```

---

### Post by techunit on 2011-04-03
Firefox 4 has been in beta so long like 9 months that almost all add-ons are now compatible! I would go the route of trying firefox 4 first and then going back if you have to.

Please note that firefox 4 has a new interface that can be reverted easily thought the menus.

Good Luck.

---


---
title: "Updating Flash?"
date: 2011-09-20
forum: General Help
---

### Post by Nymn on 2011-09-20
How do I update Flash? I already have it installed (says ver. 10.0.32) but a lot of sites have been telling me I need to update to the current version (10.3). There's no update option in the Software Center.:confused:

---

### Post by haqking on 2011-09-20
> **Nymn said:**
> How do I update Flash? I already have it installed (says ver. 10.0.32) but a lot of sites have been telling me I need to update to the current version (10.3). There's no update option in the Software Center.:confused:

The best way if you use firefox is to install the [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/versions/") plugin made by one of our members, it will download and install the best version for your system and will be used across your system.

if you dont have firefox then see here for flash on your system [https://help.ubuntu.com/community/RestrictedFormats/Flash](https://help.ubuntu.com/community/RestrictedFormats/Flash)

---

### Post by philinux on 2011-09-20
> **Nymn said:**
> How do I update Flash? I already have it installed (says ver. 10.0.32) but a lot of sites have been telling me I need to update to the current version (10.3). There's no update option in the Software Center.:confused:

Has your system been updating ok.

Open a terminal and report back any errors from this. Copy and paste the command to avoid typos.

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Nymn on 2011-09-20
Yah, I have it set to check updates daily (I think that's default, anyway). That Flash-Aid plugin seems to have done the trick. I wasn't getting the message anymore when I went to the site. Thanks!:P

---

### Post by haqking on 2011-09-20
> **Nymn said:**
> Yah, I have it set to check updates daily (I think that's default, anyway). That Flash-Aid plugin seems to have done the trick. I wasn't getting the message anymore when I went to the site. Thanks!:P

NO worries you are very welcome, Flash-Aid is a cool tool.  However yes check your update settings as well though.

Peace

---

### Post by alexvy13 on 2011-09-20
is there a similar solution to Chromium? Chrome 14 is out and shouldn't that mean the latest Chromium is out too? I couldnt update it manually and sudo apt-get update wouldn't show anything. I had to switch back to firefox :/

---

### Post by haqking on 2011-09-20
> **alexvy13 said:**
> is there a similar solution to Chromium? Chrome 14 is out and shouldn't that mean the latest Chromium is out too? I couldnt update it manually and sudo apt-get update wouldn't show anything. I had to switch back to firefox :/

I am using chromium 13 and flash works fine

---


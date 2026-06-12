---
title: "Upgrade Questions"
date: 2010-04-20
forum: General Help
---

### Post by huggs on 2010-04-20
I have Karmic installed via Wubi, and I am wondering , if I was to upgrade to Lucid, will I lose the data and settings I have on Karmic? I guess the most importnt thing is my firefox settings, it takes forever to re-set my firefox stuff up. If it doesnt automatically carry over, is there a backup method for Firefox settings, to make it a little less painful? And if I upgrade to the beta right now, would I be able to upgrade to the stable release 9 days from now?

Thanks and sorry for the noob questions, I searched but I'm not very familiar with with how to look for vague yet specific type of stuff like this

---

### Post by Megaptera on 2010-04-20
Hi,
Have you looked at this for backing-up your Firefox profile?

[http://support.mozilla.com/en-US/kb/Profiles](http://support.mozilla.com/en-US/kb/Profiles)

Richard

---

### Post by garvinrick4 on 2010-04-20
No if you upgrade and not do a clean install. Here is upgrade Code:

sudo sed -i 's/karmic/lucid/g' /etc/apt/sources.list  && sudo aptitude update && sudo aptitude dist-upgrade


I would wait until lucid is stable right now they are still looking for WUBI testers so I do
not know what shape it is in for WUBI. Up to you, but code is here anyway to upgrade when ever you want to copy and paste it.

On firefox always keep a backup of Bookmarks and such. Bookmarks/Organize/Back-up   in firefox.

---

### Post by lovinglinux on 2010-04-20
If you upgrade or if you have a separate partition for home (I guess not), then you won't lose any settings.

Nevertheless, I strongly recommend to backup your Firefox profiles on a daily basis, if you don't want to eventually re-configure settings, because lots of problems in Firefox are due to corrupted profiles. You can do that automatically with [FEBE](https://addons.mozilla.org/en-US/firefox/collection/lovinglinux) extension.

For more info [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567)

---


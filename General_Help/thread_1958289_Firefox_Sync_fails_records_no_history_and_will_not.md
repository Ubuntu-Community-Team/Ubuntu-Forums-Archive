---
title: "Firefox Sync fails records no history and will not and has no bookmarks"
date: 2012-04-14
forum: General Help
---

### Post by Raibert on 2012-04-14
[FONT=Arial][SIZE=2]I am running Firefox 11 on Ubuntu 11.10 (AMD 64bit).

Starting last night I started to get the message "Sync encountered an error while syncing: unknown error...." at the same time I seem it seems to have stopped recording history entries has no bookmarks and will not record new ones.

I unlinked the machine from my account, un-installed  Firefox and shut down the machine.  After a cold boot I reinstalled Firefox and relinked to my account. Same result.

Ubuntu 11.10 64 bit and all software are up to date (as of 00:12 on 14/04/2012)

System: AMD FX(tm)-8120 Eight-Core Processor × 8 with 15.7 GB memory, 64GB SSD and a 1TB with a[/SIZE][/FONT][FONT=Arial][SIZE=2] SAPPHIRE Radeon HD 6970 2GB graphics card.

Does any one have any idea where I should look for the problem:confused:?

Thank for reading this and hoping some one can help.

Raibert

"Reality only matters to those too slow to get out of it's way."
[/SIZE][/FONT]  [B][SIZE=1]
[/SIZE][/B]

---

### Post by drcmcs on 2012-04-14
I'm having a similar problem on Ubuntu 10.04 - when I ask to sync bookmarks I get no code and sometimes the link is dead.  I purged and reinstalled Firefox and got the following message:
 firefox-globalmenu: Depends: firefox (= 4.0.1+build1+nobinonly-0ubuntu0.11.04.1~mfs~lucid1) but 11.0+build1-0ubuntu0.10.04.2 is to be installed

I'm not a linux techie and don't know what to do if anyone can help.  Thanks

---

### Post by lovinglinux on 2012-04-14
Try to sync a clean Firefox profile. It could be a corruption in your databases.

```
firefox -P
```

> **drcmcs said:**
>  firefox-globalmenu: Depends: firefox (= 4.0.1+build1+nobinonly-0ubuntu0.11.04.1~mfs~lucid1) but 11.0+build1-0ubuntu0.10.04.2 is to be installed

Please  create a new thread for that particular issue.

---

### Post by drcmcs on 2012-04-14
I think I've resolved my problem. I just did away with the install of Firefox globalmenu and then reinstalled firefox and firefox-gnome-support.  I can now sync bookmarks with my other computers and everything seems to be working.  Not sure what globalmenu does but may hit a bump if I need it.

---


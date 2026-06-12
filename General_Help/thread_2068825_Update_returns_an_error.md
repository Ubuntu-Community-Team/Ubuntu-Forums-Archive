---
title: "Update returns an error"
date: 2012-10-10
forum: General Help
---

### Post by Randy M on 2012-10-10
I'm running 10.04 and it shows an error when I try to update.

Failed to fetch [http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

Is there a problem with the repository, or do I need to remove this one?

Thanks for any and all help.

---

### Post by conradin on 2012-10-10
edit /etc/apt/sources.list, removing that source. You should be able to ignore and continue as well.

---

### Post by hydn79 on 2012-10-10
Yes that entry is related to thunderbird. So remove as per above advice.

---

### Post by Randy M on 2012-10-10
> **conradin said:**
> edit /etc/apt/sources.list, removing that source. You should be able to ignore and continue as well.

Thanks, does that mean I won't get Thunderbird updates in the future?

---

### Post by 2F4U on 2012-10-10
After looking at the ppa it seems to me as if it is no longer maintained. So I guess you are right in assuming that there will be no more updates from this ppa.

---

### Post by oldos2er on 2012-10-10
> **Randy M said:**
> Thanks, does that mean I won't get Thunderbird updates in the future?

There's the Thunderbird beta PPA: [https://launchpad.net/~mozillateam/+archive/thunderbird-next](https://launchpad.net/~mozillateam/+archive/thunderbird-next)
but obviously its software might not be stable.

---

### Post by Randy M on 2012-10-10
Thanks to all. I'll leave this one out and check for updates manually once in a while.

---


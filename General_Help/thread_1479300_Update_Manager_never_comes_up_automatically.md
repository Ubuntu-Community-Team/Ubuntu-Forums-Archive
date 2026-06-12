---
title: "Update Manager never comes up automatically?"
date: 2010-05-10
forum: General Help
---

### Post by Mad dog on 2010-05-10
Ever since I've been using 10.04 I have never once had the update manager come up by itself like it used to with 9.04. I've given it a week one time thinking maybe there were no updates but then when I finally selected it myself it worked just fine (and had about 20 updates waiting). I've just been opening it every few days and manually getting my updates since then. This bothers me because in the future I may forget to update and miss something important. Is there any one else having this problem?

My settings are:
-Important updates
-Recommended updates

-Check for updates Daily
-Only notify about available updates

-Distribution upgrades Never

Any help would be appreciated, Thanks.

[SOLVED]

-run "gconf-edit"

-go to apps>update-notifier

-tick "auto launch"

-and set "regular auto launch interval" to 0 (for launch as soon as available) or any other number for the number of days you want it to launch. I set mine to 2

Thanks to Plucky for the solution (or at least the pertinent info and a nudge in the right direction) :-)

---

### Post by Soul-Sing on 2010-05-10
> Is there any one else having this problem?
yep

---

### Post by Mad dog on 2010-05-10
> **leoquant said:**
> yep

Good to know...

---

### Post by spiky001 on 2010-05-10
Have you check that update manager is in start up applications is ticked

---

### Post by Mad dog on 2010-05-10
> **spiky001 said:**
> Have you check that update manager is in start up applications is ticked

Yea it is.

---

### Post by plucky on 2010-05-10
> Ever since I've been using 10.04 I have never once had the update manager come up by itself like it used to with 9.04. I've given it a week one time thinking maybe there were no updates but then when I finally selected it myself it worked just fine (and had about 20 updates waiting). I've just been opening it every few days and manually getting my updates since then. This bothers me because in the future I may forget to update and miss something important. Is there any one else having this problem?




That is how it is designed.It will only open daily for security updates.Ever since the final release,there have only been recommended updates which will only get updated once a week.

This behaviour was started in Karmic.

Good Luck

---

### Post by Keith1212 on 2010-05-10
> **spiky001 said:**
> Have you check that update manager is in start up applications is ticked

I have the same problem, and I have update notifier checked in start up apps.

```
NAME: Update Notifier
Command: update-notifier
Comments: Check for available updates automatically

```

---

### Post by Mad dog on 2010-05-10
> **plucky said:**
> That is how it is designed.It will only open daily for security updates.Ever since the final release,there have only been recommended updates which will only get updated once a week.

This behaviour was started in Karmic.

Good Luck

So I should set my update manager to download and install security updates automatically and just trust that it's working?

I like the old way better where I would come to my computer and updates were waiting for me. But if what you say is true and there is no way around it, I'll just have to deal with it.

---

### Post by 98cwitr on 2010-05-10
im having the same problem...i dont have a problem installing manually...automatic download still works though.

---

### Post by plucky on 2010-05-10
From the [Lucid release notes](http://www.ubuntu.com/getubuntu/releasenotes/1004)

> Ubuntu 10.04 LTS launches update-manager  directly to handle package updates, instead of displaying a notification icon in the GNOME panel. Users are notified of security updates on a daily basis, but for updates that are not security-related, users will only be prompted once a week.   

Users who wish to continue receiving update notifications in the previous manner can restore the earlier behavior using the following command:   

gconftool -s --type bool /apps/update-notifier/auto_launch false

(This change was made in Ubuntu 9.04.)   

Good Luck

---

### Post by another_sam on 2010-05-12
I must be wrong but I'd say since I -installed- upgraded from 9.10 to 10.04 on May 2 (10 days ago) on my daily machine I've never been prompted for updates.

After installation I set "Install security updates without confirmation". This could be relevant.

Security updates (if any) have been applied correctly during these 10 days; there wasn't any one listed when I manually launched "Update Manager" 5 minutes ago. But at the same time, a lot of "Recommended updates" do were listed. I've should been prompted for them 3 days ago (7 days after installation) shouldn't I?

I'll keep watching.

---


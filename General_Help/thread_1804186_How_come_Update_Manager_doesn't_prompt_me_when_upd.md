---
title: "How come Update Manager doesn't prompt me when update is available?"
date: 2011-07-14
forum: General Help
---

### Post by nrundy on 2011-07-14
I have Update Manager set to check for updates on a daily basis but to prompt me before downloading or installing them. Because I have Update Manager set to check on a Daily basis, I expect that I will receive a prompt that an update is available no later than the day after the update is available (assuming of course I have my computer turned on). Yet I only receive a prompt days or even a week after the update was made available.

For example, let's say that my PPA of Google Chrome issues an update on Tuesday. Despite the fact that my ubuntu computer was on for a couple hours in the morning on Wednesday, Thursday, and Friday, no update prompt appears alerting me to available updates. If I manually open Update Manager on Friday afternoon, then the update is there and waiting for installation. But how come I don't get an automatic prompt that an update is available? Do I have my settings wrong or something?

---

### Post by nrundy on 2011-07-14
bump

---

### Post by mikejonesey on 2011-07-14
you can set how often updates are search for...

go to system->admin->software sources and select the tab updates; you can switch on/off and how often and which updates...

---

### Post by plucky on 2011-07-14
Update Notification behaviour changed in Jaunty.

From the Release Notes >  Change in notifications of available updates

Ubuntu 9.04 introduces a change to the handling of package updates, launching update-manager directly instead of displaying a notification icon in the GNOME panel. **Users will still be notified of security updates on a daily basis, but for updates that are not security-related, users will only be prompted once a week.**

Users who wish to continue receiving update notifications in the previous manner can restore the earlier behavior using the following command:

gconftool -s --type bool /apps/update-notifier/auto_launch false

So it is behaving as designed.

What version of Ubuntu are you using?

---

### Post by nrundy on 2011-07-14
> **mikejonesey said:**
> you can set how often updates are search for...

go to system->admin->software sources and select the tab updates; you can switch on/off and how often and which updates...

Yes. As I explained in the OP, I have this set at DAILY.

---

### Post by nrundy on 2011-07-14
> **plucky said:**
> Update Notification behaviour changed in Jaunty.

From the Release Notes 

So it is behaving as designed.

What version of Ubuntu are you using?

The problem with this Plucky is that some updates are security-related and I am not getting a DAILY update (e.g., Google Chrome PPA).

I'm using 10.04. Is there any way to make update manager give me DAILY updates for EVERYTHING?

---

### Post by plucky on 2011-07-14
> I'm using 10.04. Is there any way to make update manager give me DAILY updates for EVERYTHING? 

Run the command at the bottom of the article I quoted from the Release Notes

```
gconftool -s --type bool /apps/update-notifier/auto_launch false
```

I cannot verify this will work as I have never tried it,but as it is also in the Release notes for Lucid, it should work.

Good Luck

---

### Post by nrundy on 2011-07-14
> **plucky said:**
> Run the command at the bottom of the article I quoted from the Release Notes

```
gconftool -s --type bool /apps/update-notifier/auto_launch false
```

I cannot verify this will work as I have never tried it,but as it is also in the Release notes for Lucid, it should work.

Good Luck

Isn't this command to make Notifications appear in the top-panel? I have no problem with notifications appearing the bottom-panel next to the "application tabs" that line up in 10.04. Will making notifications appear in the top-panel like pre-9.04 make Update Manager Check & Notify Daily for updates when the alternative (notification appearing the bottom panel) does not?

---

### Post by plucky on 2011-07-14
> **nrundy said:**
> Isn't this command to make Notifications appear in the top-panel? I have no problem with notifications appearing the bottom-panel next to the "application tabs" that line up in 10.04. Will making notifications appear in the top-panel like pre-9.04 make Update Manager Check & Notify Daily for updates when the alternative (notification appearing the bottom panel) does not?

Try it and see. You can always revert the command by changing the "false" to a "true".

Good Luck

---

### Post by nrundy on 2011-07-14
I think I got it!

For anyone else with this issue, here's what I think fixes it:

1. Run (alt + F2)
2. gconf-editor
3. apps/update-notifier/regular_auto_launch_interval
4. change the value to zero (0)

---

### Post by nrundy on 2011-07-14
> **plucky said:**
> Try it and see. You can always revert the command by changing the "false" to a "true".

Good Luck

This didn't work. But thanks for trying to help :)

---


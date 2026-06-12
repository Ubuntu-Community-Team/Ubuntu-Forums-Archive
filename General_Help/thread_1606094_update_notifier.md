---
title: "update notifier"
date: 2010-10-26
forum: General Help
---

### Post by bioShark on 2010-10-26
Hello

I have noticed that in Settings in Update Manager, for "Automatic Updates" I have the option "Daily". When exactly does it check for updates and how does it notify me? I have had my Ubuntu open all day long yesterday, and nothing notified me about the updates. Of course when I've manually checked Update Manager I had over 50 updates. 
I know from previous versions that there was a small notification icon on the panel and it informed you regading the updates. The updates where automatically checked every time you booted, so right from the start you were informed that you have a certain amount of updates available.

Cheers.

---

### Post by plucky on 2010-10-26
From the 10.04 [Release Notes](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes)

> Change in notifications of available updates

Ubuntu 10.04 LTS launches update-manager directly to handle package updates, instead of displaying a notification icon in the GNOME panel. Users are notified of security updates on a daily basis, but for updates that are not security-related, users will only be prompted once a week.

Users who wish to continue receiving update notifications in the previous manner can restore the earlier behavior using the following command:

gconftool -s --type bool /apps/update-notifier/auto_launch false

(This change was made in Ubuntu 9.04.)

Good luck

---

### Post by bioShark on 2010-10-26
Thanks for the quick reply.

> gconftool -s --type bool /apps/update-notifier/auto_launch false

I have done the same thing using Configuration Editor.

Now let's see how that turns out.

Cheers

---


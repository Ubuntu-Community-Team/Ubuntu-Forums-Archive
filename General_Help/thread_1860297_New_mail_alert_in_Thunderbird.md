---
title: "New mail alert in Thunderbird"
date: 2011-10-14
forum: General Help
---

### Post by SyncMr on 2011-10-14
Hi,

I successfully configured Mozilla Thunderbird in my Ubuntu v10. I would like to have some addon for popping up the new mails. some thing like New Mail alert in a separate dialog box as we can set in outlook. I tried few addons (like New Mail Attention)  but nothing worked. :(

Thanks.

---

### Post by sgage on 2011-10-14
> **SyncMr said:**
> Hi,

I successfully configured Mozilla Thunderbird in my Ubuntu v10. I would like to have some addon for popping up the new mails. some thing like New Mail alert in a separate dialog box as we can set in outlook. I tried few addons (like New Mail Attention)  but nothing worked. :(

Thanks.

sudo apt-get install notification-daemon

For some reason, it doesn't seem to get installed by default.

---

### Post by SyncMr on 2011-10-14
Even after executing the command I don't get any notifications. Should I check something else.?

---

### Post by dcstar on 2011-10-14
> **SyncMr said:**
> Even after executing the command I don't get any notifications. Should I check something else.?

Did you set it up, it won't configure itself?

---

### Post by SyncMr on 2011-10-18
Nope I didnot set it up. I just ran the command and restarted thunderbird and tried. It didnot work. I badly want new mail alerts in a separate window.

---

### Post by azmyth on 2011-10-18
You need to use something like notify-osd. There's a plugin someone developed at 

[https://launchpad.net/libnotify-mozilla](https://launchpad.net/libnotify-mozilla)

Someone also wrote something but it looks a bit old.

[http://ubuntuforums.org/showthread.php?t=1116693](http://ubuntuforums.org/showthread.php?t=1116693)

---

### Post by SyncMr on 2011-10-19
unfortunately none of them are working. :(

---


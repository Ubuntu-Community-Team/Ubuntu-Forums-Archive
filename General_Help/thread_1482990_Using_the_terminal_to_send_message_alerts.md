---
title: "Using the terminal to send message alerts"
date: 2010-05-14
forum: General Help
---

### Post by Richbuntu on 2010-05-14
Hi,
Can someone tell me how to send a message alert from the terminal?
I googled it, but I didn't find anything.

---

### Post by 3rdalbum on 2010-05-14
You can send notifications from the terminal by installing the "libnotify-bin" package and running the 'notify-send' command:

```
notify-send "This is a notification"
```

You can look at the manual page for notify-send to find out how to make prettier notifications.

---


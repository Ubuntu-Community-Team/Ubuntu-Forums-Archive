---
title: "command line help pl0X?"
date: 2010-02-27
forum: General Help
---

### Post by buhmillion on 2010-02-27
How do i generate a new notifyOSD bubble from a command line?

---

### Post by Apollo87 on 2010-02-27
You need to install the libnotify-bin package first

```
sudo apt-get install libnotify-bin
```

then

```
notify-send "Adam" "This is a test" -i notification-message-im

```

---


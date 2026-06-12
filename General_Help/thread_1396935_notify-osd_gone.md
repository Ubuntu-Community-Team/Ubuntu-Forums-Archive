---
title: "notify-osd gone"
date: 2010-02-02
forum: General Help
---

### Post by ThatGuy07 on 2010-02-02
A while back I decided I didnt like notify-osd. so I switch it to the notification-daemon. Well times and feelings change, as such I decided to go back to notify-osd. Epic failure. Now I have no notifications what so ever.

the tut I used to switch
> **gradinaruvasile said:**
> U can revert to the older style notification by (commands in terminal):

1. Install the notification-daemon package:

```
sudo apt-get install notification-daemon
```

2. Rename the /usr/lib/notify-osd/notify-osd executable

```
sudo mv /usr/lib/notify-osd/notify-osd /usr/lib/notify-osd/notify-osd-original
```

3. Create a symbolic link:

```
sudo ln -s /usr/lib/notification-daemon/notification-daemon /usr/lib/notify-osd/notify-osd
```

4. Kill the original notification:

```
sudo killall notify-osd
```

5. Launch the new notification - press alt+F2, type /usr/lib/notify-osd/notify-osd

6. Test:

```
notify-send test test
```

With this older notification type u can use the notification-ptoperties tool to set the location of the notification pop ups

and clue how to get notify-osd back up and running?

---

### Post by ibuclaw on 2010-02-02
In reverse order of the tut then.

```
sudo killall notification-daemon
```
```
sudo unlink /usr/lib/notify-osd/notify-osd
```
```
sudo mv /usr/lib/notify-osd/notify-osd-original /usr/lib/notify-osd/notify-osd
```
```
sudo apt-get purge notification-daemon
```

Then to test:
```
notify-send test test
```

Regards
Iain

---

### Post by ibuclaw on 2010-02-02
FYI, for future reference, the **simple** way to do it would be to remove notify osd and replace with notification daemon instead.

To switch to notification daemon:
```
sudo apt-get purge notify-osd && sudo apt-get install notification-daemon
```
And to switch to notify osd
```
sudo apt-get purge notification-daemon && sudo apt-get install notify-osd
```

Regards

---

### Post by ThatGuy07 on 2010-02-02
that did it for me. thanks for the quick replys.

---


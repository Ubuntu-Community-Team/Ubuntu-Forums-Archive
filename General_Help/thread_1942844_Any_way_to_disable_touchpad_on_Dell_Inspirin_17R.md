---
title: "Any way to disable touchpad on Dell Inspirin 17R?"
date: 2012-03-18
forum: General Help
---

### Post by donsy on 2012-03-18
I loaded 11.10 on my Dell Inspiron 17R and I've been very satisfied so far except for one MAJOR annoyance. The touchpad is enabled while I'm typing and I can't disable it. Here's what I've tried so far:

[LIST]
[*]Bios -- no option to disable pointing devices.
[*]Hotkey FN-F3 -- Doesn't work in Ubuntu (works fine in Windows).
[*]System Settings > Mouse and Touchpad -- no option to disable touchpad while typing.
[*]syndaemon -- has no effect.
[*]synclient -- has no effect.
[/LIST]
This is driving me crazy, Is there anything else I can try?

---

### Post by TeoBigusGeekus on 2012-03-18
Try [this]("https://lists.ubuntu.com/archives/ubuntu-users/2010-July/223786.html").

---

### Post by donsy on 2012-03-18
> **TeoBigusGeekus said:**
> Try [this]("https://lists.ubuntu.com/archives/ubuntu-users/2010-July/223786.html").
It works!!! Thank you so much.

---

### Post by TeoBigusGeekus on 2012-03-18
You're welcome.

---

### Post by donmatas on 2013-02-03
> **TeoBigusGeekus said:**
> Try [this]("https://lists.ubuntu.com/archives/ubuntu-users/2010-July/223786.html").

Amazing. It works for my netbook Samsung N210 with Xubuntu 12.04:

You have to create the file "blacklist-touchpad.conf" with root privileges in "/etc/modprobe.d/" and add to it this single line: "blacklist	psmouse". If you need to enable it again, just comment the line like this: "#blacklist	psmouse".

Step by step for beginners:

1. Go to your terminal and open Leafpad with as super user:

```
sudo leafpad
```

2. Write in the new page the following line:

```
blacklist	psmouse
```

3. Go to "save as" and save the new file into the following directory: /etc/modprobe.d/ and name it like this: blacklist-touchpad.conf

4. After saving it, reboot your machine and the touchpad will be deactivated.

If you need to activate it again:

1. Open the file as super user:

```
sudo leafpad /etc/modprobe.d/blacklist-touchpad.conf

```

2. Comment the line by adding a "#" simbol to it. The line should now look like this:

```
#blacklist	psmouse
```

3. Save changes and reboot.

---


---
title: "Card Reader USB 2.0"
date: 2006-05-02
forum: General Help
---

### Post by jedimasterk on 2006-05-02
I have a GGI card reader, that works in Windows, but is unable to mount with Ubuntu 5.10. What do I need to do to make it mountable. HAL identifies it as a 7 and 1 card reader. I prefer using a card reader over plugging the camera up directly. Saves battery life. Fairly new to Linux.](*,)

---

### Post by Zimmer on 2006-05-02
[QUOTE=jedimasterk]I have a GGI card reader, that works in Windows, but is unable to mount with Ubuntu 5.10. What do I need to do to make it mountable. HAL identifies it as a 7 and 1 card reader. I prefer using a card reader over plugging the camera up directly. Saves battery life. Fairly new to Linux.](*,)[/QUOTE]

Have you tried (yes I know this sounds daft, but before everyone gets technical on you....)
 1) plugging it in firmly
    2) Inserting some media into the reader.
(Remember to unmount it and wait a moment or two before removing the media....)

I have a Trust 16-1 USB card reader. It automounts when the media is inserted.
I bought it because my previous card reader would work with windows, but not Ubuntu.
A friend took it away to check it out with SUSE and found damage to the connection pins in the CF slot: it still works with Windows....???

---

### Post by Sutekh on 2006-05-03
Here's something to try that wil help out

Start with the card reader unplugged, then use this command from a terminal window.
```
tail -f /var/log/messages
```
Then plug in your card reader and take note of the messages that appear.

Then also try inserting some media into the reader.

If the card reader wants to be mounted it will in amongst those messages, tell you the device node that it is located on, like sda or sdb, etc.  If you can determine this then you can mount the media using a guide like

[http://www.psychocats.net/ubuntu/mountwindows.php](http://www.psychocats.net/ubuntu/mountwindows.php)

If you are unsure what to do, just post back the output from the **tail** command.

---

### Post by bluenova on 2006-05-03
I have a very simple 19in1 card reader, and ubuntu gnome automagically mounts all the drives and displays them in 'computer'.

---


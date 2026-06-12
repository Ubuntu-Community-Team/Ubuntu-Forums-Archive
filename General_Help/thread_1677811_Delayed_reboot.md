---
title: "Delayed reboot"
date: 2011-01-29
forum: General Help
---

### Post by megabuffen on 2011-01-29
Is there a command i can enter into the terminal or over an SSH session to make an Ubuntu system reboot a few hours later? Sometimes I want to reboot my server and it should take place in the middle of the night when I'm asleep.

---

### Post by tredegar on 2011-01-29
Become root.
Sleep for 4 hours
Reboot.```
sudo -i
sleep 4h; reboot
```
Edit:
If you want to be able to logout of the ssh session you'll need to use **screen** to detach that process, and leave it running in the background when you logout.
/Edit

---

### Post by Smart Viking on 2011-01-29
```
sleep 6h && shutdown -r
```wait 6 hours, and then reboot.

EDIT: Ye that's right as tredegar says shutdown command requires root privileges, but this can be changed.

---

### Post by tredegar on 2011-01-29
Even easier is ```
sudo shutdown -r 23:59 &
```
Which will reboot at one minute to midnight.
No need for **sleep** **nohup** or **screen**

---

### Post by megabuffen on 2011-01-29
Thanks a lot! That's exactly what I needed.

---


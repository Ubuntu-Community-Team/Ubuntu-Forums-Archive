---
title: "Is there a way to get username when root and not using a terminal?"
date: 2012-06-11
forum: General Help
---

### Post by WongFuChu on 2012-06-11
I had a script that would change the hdmi audio profile via udev. I used to use
```
sudo -u $USER pactl set-card-profile 0 output:hdmi-surround
```
to change the sound profile, because when running as root (when udev runs the script) pactl doesn't change th sound profile without the 
```
sudo -u $USER
```
In Ubuntu 11.10, I set $USER with:
```
USER="$(who -H | grep :0\) | cut -f 1 -d ' ')"
```
and the script worked (didn't know how; found that online somewhere). In 12.04, I can't get it to work. If I have my udev script call "who" and output it to a file, it doesn't show any user logged in (unless I had a terminal open at the time udev ran the script).

So... I know this is a weird question, but, is there a way to get the username of the user logged into a gnome/unity/etc. session? AFAIK, it seems as if "who" only shows any user logged into a tty or that has a terminal window open.

---


---
title: "Black screen after screen saver"
date: 2012-08-24
forum: General Help
---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-08-24
If screensaver is started on my computer, I can't get the display back again. No matter what I try, the screen remains black. All I can is hard restart computer to get it back to run. what can be the cause?

---

### Post by Rexilion on 2012-08-24
If you have the issue, check the following things:

output of the 'dmesg' command
content of /var/log/Xorg.0.log

Could be that the screensaver is making X / kernel unhappy?

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-08-27
Rexilion thanks for the reply. I'm afraid this didn't tell me much. I'm still not able to fix my issue.

---

### Post by Rexilion on 2012-08-27
No problem, I'll try to be more specific.

Please open a terminal and copy paste the following commands:

```
sudo dmesg
cat /var/log/Xorg.0.log
```

Copy the output of the above commands, paste them at [www.pastebin.com](www.pastebin.com) and place the returned link here. So we can inspect your system logs and see if you have issue's with the drivers.

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-08-27
Rexilion you're a star.

Here's the [output of sudo dmesg]("http://pastebin.com/embed_iframe.php?i=RMmGWzxm"), and here's the [output of cat /var/log/Xorg.0.log]("http://pastebin.com/embed_iframe.php?i=BMCdBmKp").

I hope I didn't make any mistakes.

---

### Post by Rexilion on 2012-08-27
Do you know which screensaver you use?

The following command will confirm that (no sudo needed):

```
dpkg --get-selections | grep -i screen
```

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-08-27
Here's the output:
```
$ dpkg --get-selections | grep -i screen
gnome-screensaver				install
gnome-screenshot				install
```

---

### Post by Rexilion on 2012-08-28
Ok try this:

- Lock screen
- Press: Ctrl+Alt+F1
- Login as your normal user
- ```
killall gnome-screensaver
```
- Press: Ctrl+Alt+F7

If I'm correct, then after locking and doing the above. Your desktop should be visible again. That means we have narrowed it down to the screensaver.

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-08-31
Rexilion it seems to be fixed by some update. I think it's back to normal... Weird :-k But thank you so much for your time and good will. Much appreciated!

---


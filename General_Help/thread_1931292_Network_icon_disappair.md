---
title: "Network icon disappair"
date: 2012-02-25
forum: General Help
---

### Post by SteMMo on 2012-02-25
Hi all,
with the last upgrade to 11.10 happens that Ubuntu starts normally with the network icon shown near the clock.
When i connect the wifi network (by 'sudo modprobe ndiswrapper') the icon disappair and the network is on.

Any idea?

---

### Post by raja.genupula on 2012-02-25
is there any effect , if you change the theme from appearance settings ?

edit : if it wont help try this 
**unity --reset**

---

### Post by SteMMo on 2012-02-25
If i change the theme, the icon doesn't appair.(from Radiance to Ambiance).

If i type 'unity --reset' I had some flashes and then the terminal shown me a Segmentation fault. Then all the windows did nothave title or border. I rebooted.

---

### Post by raja.genupula on 2012-02-25
after reboot how they are ? 
is issue solved ?

---

### Post by pbrane on 2012-02-25
That happens to me sometimes on Xubuntu 11.10. I'm not running Unity or ndiswrapper but I can correct the issue by running 
```

nm-applet &

```
in a terminal.

---

### Post by SteMMo on 2012-02-25
After the boot the icon is visible until i connect the net.

Typing the command:

stefano@ghilba:~$ nm-applet &
[1] 2430
stefano@ghilba:~$ ** Message: applet now removed from the notification area
** (nm-applet:2430): DEBUG: old state indicates that this was not a disconnect 0

Now the icon is visible!

---

### Post by SteMMo on 2012-02-26
So, is it a bug or whatelse?

---


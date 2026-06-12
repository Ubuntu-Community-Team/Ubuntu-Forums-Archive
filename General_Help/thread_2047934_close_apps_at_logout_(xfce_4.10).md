---
title: "close apps at logout (xfce 4.10)"
date: 2012-08-25
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2012-08-25
is there a way to close gmusicbrowser at logout, it seems to be getting its process killed or is crashing at logout which results in it not saving it data (eg track/position )

---

### Post by dgharmon on 2012-08-25
> **pqwoerituytrueiwoq said:**
> is there a way to close gmusicbrowser at logout, it seems to be getting its process killed or is crashing at logout which results in it not saving it data (eg track/position )

Put this "gmusicbrowser -cmd Quit" in your [logout script]("http://stackoverflow.com/questions/7579438/how-to-execute-a-script-when-xfce-session-ends") ...

---

### Post by pqwoerituytrueiwoq on 2012-08-25
worked
does not take effect till after you login again

---

### Post by pqwoerituytrueiwoq on 2012-10-05
better solution:
[http://ubuntuforums.org/showthread.php?t=1918649](http://ubuntuforums.org/showthread.php?t=1918649)
```
~$ cat /usr/local/bin/xfce-logout-script
#!/bin/bash
echo "`date`" > /var/log/xfce-logout-script
pid="`pgrep -f gmusicbrowser | head -1`" # need a way to get user name at logout (only supports 1 user)
echo "pid = $pid" >> /var/log/xfce-logout-script
if [ "0$pid" -gt "0" ]; then
    user="`ps aux | awk '{print $1" "$2}' | grep $pid | awk '{print $1}'`"
    echo "user = $user" >> /var/log/xfce-logout-script
    sudo -u $user gmusicbrowser -cmd Quit
fi
```

---


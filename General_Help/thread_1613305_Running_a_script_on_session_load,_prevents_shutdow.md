---
title: "Running a script on session load, prevents shutdown?"
date: 2010-11-04
forum: General Help
---

### Post by Gorlist on 2010-11-04
Hi, I need to run a script on boot up, however when its added to the rc it seems to prevent ubuntu from shutting down and has done since 10.04 (just sits on the closing logo indefinitely). 

Ive created a sh file and set to execute in init.d with the following:

```
sudo -s
echo USB4 > /proc/acpi/wakeup
```

Then added:

```
sudo update-rc.d wake.sh defaults
```

Any suggestions on the cause, or how else to run the script on load?

---

### Post by trikster_x on 2010-11-06
Use the sudo crontab and instead of specifying any time or day modifiers, use the "@reboot" modifier.  Your crontab entry should look like this:

```
@reboot /path/to/script
```

Your code will then run anytime someone logs in.

---

### Post by dcstar on 2010-11-06
> **Gorlist said:**
> Hi, I need to run a script on boot up, however when its added to the rc it seems to prevent ubuntu from shutting down and has done since 10.04 (just sits on the closing logo indefinitely). 

Ive created a sh file and set to execute in init.d with the following:

```
sudo -s
echo USB4 > /proc/acpi/wakeup
```

Then added:

```
sudo update-rc.d wake.sh defaults
```

Any suggestions on the cause, or how else to run the script on load?

Look at the other scripts and structure yours in the same way.

---

### Post by Gorlist on 2010-11-07
thanks for the replies, working via crontab.

---


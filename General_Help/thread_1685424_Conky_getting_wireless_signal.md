---
title: "Conky getting wireless signal"
date: 2011-02-10
forum: General Help
---

### Post by spoonman184 on 2011-02-10
So I wrote up a very simple bash script to find the quality of my wireless connection:

/home/devin/.scripts/wnicquality.sh
```
#!/bin/bash

sudo iwconfig wlan0 > wireless_details
grep "Link Quality=" wireless_details

```

But it isn't outputting anything in Conky. Here is the part of the config thats relevant:

.conkyrc
```
ESSID: ${wireless_essid wlan0} Quality: ${execi 300 .scripts/wnicquality.sh}
```

---

### Post by Brandon Williams on 2011-02-10
Did you modify sudoers to allow you to run 'sudo iwconfig' without authentication? You would need to add something like this to /etc/sudoers:```
username ALL = NOPASSWD: /sbin/iwconfig
```Please note that making this change would allow the specified user to run any iwconfig command as root without entering a password, which could be a security risk. An alternative would be to not use sudo in the script itself, but instead run the whole script with sudo. Then, you would update sudoers to allow your script to be run without a password, thus limiting how iwconfig can be used.

---

### Post by spoonman184 on 2011-02-10
I have Conky in automatic startup, so won't root be the one executing it anyway? If not, what user would be running it?

---

### Post by Brandon Williams on 2011-02-10
When you say "automatic startup" what do you mean? If it's started as an startup application via your login session manager, then it's running as you. If it's started via upstart, then yes, it's probably running as root. Just run 'ps -ef | grep conky' to figure out who the owning user is.

If it's running as root, then you're right that the unnecessary use of sudo is probably not the issue.

---

### Post by spoonman184 on 2011-02-10
I am a little bit confused as to which command I will be adding so I don't need a password.

I think I need to do: "sudo bash script" but I don't know whether to add bash to sudoers, or the script.

EDIT: Was the script I needed to add. Thanks.

---

### Post by m_duck on 2011-02-10
Conky has its own variables for wireless quality, ***wireless_link_qual*** and ***wireless_link_qual_perc***. [This](http://conky.sourceforge.net/variables.html) is a good reference for the available Conky variables and descriptions.

---

### Post by spoonman184 on 2011-02-10
The variables didn't work on my system. I tried using them to no avail =\. Oddly enough I could get the ESSID.

---

### Post by m_duck on 2011-02-10
Ah OK. I assumed such would be the case but thought I'd add the above for the sake of completeness. They don't work on one of my machines either which I attributed that to using Wicd rather than Network Manager, but never looked into it.

---


---
title: "Executing bash scripts with sudo, not in the directory they are saved"
date: 2010-03-13
forum: General Help
---

### Post by constanthatz on 2010-03-13
I have created two bash scripts, script1 and script2, that require sudo to execute.  I have placed these scripts in ~/scripts, which I have added to my path via .bashrc and .bashrc_profile. When I try to execute these scripts from outside ~/scripts with sudo the result is command not found.  Doing the same thing without sudo, the script is found and tries to run but I get a Permission Denied error, which I expect.


Can anyone explain to me the last case?  I don't understand that at all.  For clarity I have included examples of what happens in different cases of trying to run the script.

```
~/scripts $ script1
```
Results in Permission Denied.

```
~/scripts $ sudo script1
```
Results in properly executed script.

```
~ $ scripts/script1
```
Results in Permission Denied.

```
~ $ sudo scripts/script1
```
Results in properly executed script

```
~ $ script1
```
Results in Permission Denied.

```
~ $ sudo script1
```
Results in command not found.

Thanks

---

### Post by gmargo on 2010-03-13
**sudo** creates a sane $PATH, which does not include your ~/scripts directory.

Compare the output of the following two commands:
```

env | grep PATH
sudo env | grep PATH

```and you will see the different execution environment.

As far as the "permission denied" message: what are the permissions on the script?

---

### Post by constanthatz on 2010-03-14
Thank you.  Is it possible for me to change the $PATH sudo uses? I am going to move my scripts to a directory in the $PATH sudo creates, but I would like to know for future use.

The scripts I wrote are a kludge to get around the problem that I can't change my laptop's, Ideapad Y450, brightness unless I am in a virtual console.

```
#!/bin/bash
chvt 1
echo -n 15 > /proc/acpi/video/VGA/LCD/brightness
chvt 7
```

The echo line results in Permission Denied if the script is run without sudo.

---

### Post by gmargo on 2010-03-15
> **constanthatz said:**
> Is it possible for me to change the $PATH sudo uses? I am going to move my scripts to a directory in the $PATH sudo creates, but I would like to know for future use.
The default PATH is set in **/etc/environment**.  However, you'll find this is not quite the same as sudo's PATH, which seems to be a "safer" version of the user's PATH.  Best bet is to put the scripts in **/usr/local/bin/** or **/usr/local/sbin/**.

---

### Post by constanthatz on 2010-03-15
Thank you, that is what I am going to do.

---

### Post by gmargo on 2010-03-15
Just a quick addendum: Nothing prevents you from just using symbolic links in **/usr/local/bin/** pointing back to your scripts in **/home/username/scripts/**.  (Like **/usr/local/bin/script1** points to **/home/username/scripts/script1**.)  The advantage is that the script gets backed up when you back up your home directory.

---

### Post by constanthatz on 2010-03-15
Perfect, thanks.

---


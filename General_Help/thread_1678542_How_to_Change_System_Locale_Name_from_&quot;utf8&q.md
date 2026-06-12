---
title: "How to Change System Locale Name from &quot;utf8&quot; to &quot;UTF-8&quot;"
date: 2011-01-30
forum: General Help
---

### Post by lancelotj on 2011-01-30
I'm using Ubuntu 10.04 and the default system locale is:

```
LANG=en_US.utf8
LANGUAGE=en_US:en
LC_CTYPE="en_US.utf8"
LC_NUMERIC="en_US.utf8"
LC_TIME="en_US.utf8"
LC_COLLATE="en_US.utf8"
LC_MONETARY="en_US.utf8"
LC_MESSAGES="en_US.utf8"
LC_PAPER="en_US.utf8"
LC_NAME="en_US.utf8"
LC_ADDRESS="en_US.utf8"
LC_TELEPHONE="en_US.utf8"
LC_MEASUREMENT="en_US.utf8"
LC_IDENTIFICATION="en_US.utf8"

```
I want to change them to "en_US.UTF-8", but I after I changed "/etc/environment" and "/etc/default/locale", nothing happens. Where is this string defined?

---

### Post by lancelotj on 2011-06-19
I finally solved this problem by reading this bug report: 

[https://bugs.launchpad.net/ubuntu/+source/language-selector/+bug/666565](https://bugs.launchpad.net/ubuntu/+source/language-selector/+bug/666565)

Enable the backports:


* System -> Administration -> Update Manager -> Settings...

* Select the "Updates" tab and check the "Unsupported updates" option.

Then do a system update, all fixed.

---


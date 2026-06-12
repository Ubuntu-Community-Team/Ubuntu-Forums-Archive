---
title: "Collect information for an already existing bug reported by someone else"
date: 2012-04-08
forum: General Help
---

### Post by palimmo on 2012-04-08
I have read here but I haven't understood.
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

How can I collect information for an already existing bug reported by someone else?

Thanks!

---

### Post by 2F4U on 2012-04-08
For an already existing bug you could directly login to launchpad, search for the bug, and then add your information. Or am I misunderstanding your question?

---

### Post by palimmo on 2012-04-08
```
Adding Apport Debug Information to an Existing Launchpad Bug
If **you** have already reported a bug directly via Launchpad, but want to add additional debugging information via Apport to the bug report, you can do this by running the command apport-collect bug_number via "Run Application" or terminal window.
```

I think it doesn't work for bugs reported by someone else.

---

### Post by palimmo on 2012-04-08
> **2F4U said:**
> For an already existing bug you could directly login to launchpad, search for the bug, and then add your information. Or am I misunderstanding your question?
How can I collect precise information to post?

---

### Post by palimmo on 2012-04-08
maybe
*apport-cli -f -p <package name> --save bug.apport *

---

### Post by palimmo on 2012-04-08
> **palimmo said:**
> maybe
*apport-cli -f -p <package name> --save bug.apport *
I've tried
alt+F2
apport-cli -f -p <terminal> --save bug.apport 
and apport itslef crashed... hahah

---


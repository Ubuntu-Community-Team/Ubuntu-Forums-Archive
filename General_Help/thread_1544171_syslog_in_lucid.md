---
title: "syslog in lucid"
date: 2010-08-02
forum: General Help
---

### Post by naftali on 2010-08-02
Hi, I'm trying to follow the instructions on [this blog]("http://www.fewt.com/2010/07/move-your-logs-and-temp-files-to-ram.html") post, but it seems that ubuntu's (Lucid) log system is different, because I get the following error: 
"sudo: /etc/init.d/sysklogd: command not found"
What is the proper way of doing this in Lucid?

Thanks

---

### Post by robsoles on 2010-08-02
Depends on your set up.

try
```
/etc/init.d/rsysl[Tab]
```
(I mean press the [Tab] key at that point)

If that doesn't complete as a valid script file name then try
```
/etc/init.d/sysl[Tab]
```

One of them is likely to be on your system, more likely the first by the sound of things but you might need to switch to using the second to get what you are trying to do done.

---

### Post by dcstar on 2010-08-02
> **naftali said:**
> Hi, I'm trying to follow the instructions on [this blog]("http://www.fewt.com/2010/07/move-your-logs-and-temp-files-to-ram.html") post, but it seems that ubuntu's (Lucid) log system is different, because I get the following error: 
"sudo: /etc/init.d/sysklogd: command not found"
What is the proper way of doing this in Lucid?

Thanks

Urrr, another brain-dead blog that ignores the fact that you can set up Memory Cache in Firefox and then basically turn off Disk caching without any mucking around with permanently using RAM resources for a program that may not even be running.

---

### Post by robsoles on 2010-08-02
> **dcstar said:**
> Urrr, another brain-dead blog that ignores the fact that you can set up Memory Cache in Firefox and then basically turn off Disk caching without any mucking around with permanently using RAM resources for a program that may not even be running.

Gotta hand it to you David, I looked at OP's request for info without looking at that blog - just checked the blog post. Pretty much may as well kill or void logging rather than lose RAM to anything like that.

---


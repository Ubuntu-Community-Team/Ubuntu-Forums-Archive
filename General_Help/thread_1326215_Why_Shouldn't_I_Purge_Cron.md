---
title: "Why Shouldn't I Purge Cron?"
date: 2009-11-14
forum: General Help
---

### Post by moore.bryan on 2009-11-14
I have expressly set nothing to be automatically run at any particular time and, as far as I know, I have not automatic downloads set for Synaptic or Update-Manager; so, why should I even have cron installed?

---

### Post by StOoZ on 2009-11-14
because your system uses it anyway?
and you may need it in the future?

---

### Post by srijeevadurai1 on 2009-11-14
Hi, Sorry to post my question in this thread. I am new to forum and don't know how to create a new thread for my question. Help me with my question please.
 
I am using wxDownload in Ubuntu. When I copy rar link into wxDownload manager and start download the same. It downloads HTML pages instead of actual rar file. Could any one advice me how should I over come this ? Thanks a lot for your reply in advance.

---

### Post by mdatye on 2009-11-14
srijeevadurai1, I have created a new thread for you. 

On the bread crumbs above... just go to whatever section you want and you will have a button to start a new thread at the top left.

---

### Post by moore.bryan on 2009-11-14
> **StOoZ said:**
> because your system uses it anyway?
and you may need it in the future?

I guess that kinda gets to my point: for what does my system use it if I've setup *nothing* **to** use it? Need it for what?

---

### Post by QLee on 2009-11-14
[QUOTE=moore.bryan]I guess that kinda gets to my point: for what does my system use it if I've setup *nothing* **to** use it? Need it for what?[/QUOTE]

Even if *you* haven't set up anything to use it, was anything setup to use it when you installed the system? Do you care if the logs are rotated, etc., etc.?

Have a look at the cron folders in /etc, see if there is anything you think is necessary or desirable in those.

---

### Post by falconindy on 2009-11-14
Because the system uses cron fairly extensively to keep itself healthy, even if you don't. Do: 
```
ls /etc/cron.{hourly,daily,weekly,monthly}
```
All those scripts are being run by cron on a regular basis.

---

### Post by moore.bryan on 2009-11-14
> **falconindy said:**
> Because the system uses cron fairly extensively to keep itself healthy, even if you don't. Do: 
```
ls /etc/cron.{hourly,daily,weekly,monthly}
```
All those scripts are being run by cron on a regular basis.

Hmm... that's an interesting look at things falconindy. There are some entries in there (like popularity-contest) which I *specifically* did not opt into during install and some (like google-chrome) which I don't even know what they are. Almost all the folders are empty, except for some @anacron entries.

---


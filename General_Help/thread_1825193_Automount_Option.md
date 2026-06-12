---
title: "Automount Option"
date: 2011-08-14
forum: General Help
---

### Post by JohnH on 2011-08-14
Hi everyone,

I guess I'm here because I've just spent a long time sorting out a problem to do with auto mounting drives and partitions. I won't bore you with the details other than to say while I was muddling my way through this tedious process, (yes I know about the gui options but they cause problems too), I kept thinking, "Wouldn't it be nice if Ubuntu had a right click option on a mounted drive/partition that would ensure that particular drive was auto mounted from then on." Likewise an un-auto mount option to reverse this process too.

Simple idea but often the simple things get overlooked by the glitzy ones I suppose. If I could program, I would have a go myself...

I feel better now,

John

---

### Post by aysiu on 2011-08-14
This may help:
[http://www.techsupportalert.com/content/ubuntu-tips-and-tricks.htm#Auto-Mount-Drives-at-System-Startup](http://www.techsupportalert.com/content/ubuntu-tips-and-tricks.htm#Auto-Mount-Drives-at-System-Startup)

---

### Post by varunendra on 2011-08-15
> **aysiu said:**
> This may help:
[http://www.techsupportalert.com/content/ubuntu-tips-and-tricks.htm#Auto-Mount-Drives-at-System-Startup](http://www.techsupportalert.com/content/ubuntu-tips-and-tricks.htm#Auto-Mount-Drives-at-System-Startup)
@aysiu,
The link leads me to an error page:
> **Warning**:  opendir(themes) [[function.opendir]("http://www.techsupportalert.com/function.opendir")]: failed to open dir: Permission denied in **/home/ccgnome/public_html/includes/file.inc** on line **993**

**Warning**:  Cannot modify header information - headers already sent  by (output started at /home/ccgnome/public_html/includes/file.inc:993)  in **/home/ccgnome/public_html/includes/install.inc** on line **617**

**Warning**:  Cannot modify header information - headers already sent  by (output started at /home/ccgnome/public_html/includes/file.inc:993)  in **/home/ccgnome/public_html/includes/install.inc** on line **618**Not sure if it is just me or a link error. Please confirm.


@JohnH
I'm assuming for the moment that the link aysiu provided links to some fstab editing tutorial.

So, did you have a look on this tutorial?- [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)



**_EDIT_:**
Got the google-cached version of the page aysiu linked. It's an excellent tutorial for many post-installation tricks. Thanks aysiu for the link! I could attach the pdf copy of the page but it may violate copyright permissions. So try this keyword yourself in google search and click on "cached" in the top result: **techsupportalert ubuntu Auto-Mount-Drives-at-System-Startup**
You won't need to edit /etc/fstab manually following this guide.

---


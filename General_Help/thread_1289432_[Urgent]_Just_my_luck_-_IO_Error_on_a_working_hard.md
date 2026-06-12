---
title: "[Urgent] Just my luck - I/O Error on a working harddrive..."
date: 2009-10-12
forum: General Help
---

### Post by mac666 on 2009-10-12
Hey
After some usage on my fresh installed ubuntu i get I/O Error on another drive...
Why does this happen?
The drive works for a random period of time and then i cant start anything from it, not read or anything... but i can explore all the folders and see all the files :|

In Windows it works great

What i did was install Storage Disk manager and gave some of my larger drives automounting... nothing more...

Please?! I want to listen to my music :(

---

### Post by mac666 on 2009-10-12
No replies?! :|
This must be a simple matter? :S

---

### Post by rippin on 2009-10-12
> **mac666 said:**
> Hey
After some usage on my fresh installed ubuntu i get I/O Error on another drive...
Why does this happen?
The drive works for a random period of time and then i cant start anything from it, not read or anything... but i can explore all the folders and see all the files :|

In Windows it works great

What i did was install Storage Disk manager and gave some of my larger drives automounting... nothing more...

Please?! I want to listen to my music :(

You installed something and you don't know what it does!? Gee.

"Storage Disk manager is policy-based management of file backup and archiving in a way that uses storage devices economically and without the user needing to be aware of when files are being retrieved from backup storage media. "

Guess it'll be accessing hard drives, as mentioned, from time-to-time, and doing backups, huh?

Do you have rights to the files?

---

### Post by mac666 on 2009-10-12
It had nothing to do with Disk Manager.

What i did was:

Booted into recovery mode, edit /etc/fstab and removed the line that mounted my effected drive.
Rebooted and then made a fsck - p /dev/sdX

Wolla...!!!

---

### Post by rippin on 2009-10-12
> **mac666 said:**
> It had nothing to do with Disk Manager.

What i did was:

Booted into recovery mode, edit /etc/fstab and removed the line that mounted my effected drive.
Rebooted and then made a fsck - p /dev/sdX

Wolla...!!!

<sarcasm> EXCELLENT </sarcasm> !

Now then, for our sake, before your next post study this: [http://catb.org/~esr/faqs/smart-questions.html]("http://catb.org/%7Eesr/faqs/smart-questions.html")

Just in case, here's a premier:

"
[B][SIZE=3]Before You Ask

[/SIZE][/B]Before asking a technical question by e-mail, or in a newsgroup, or on a website chat board, do the following:

[LIST=1]
[*]Try to find an answer by searching the archives of the forum you plan to post to.
[*]Try to find an answer by searching the Web.
[*]Try to find an answer by reading the manual.
[*]Try to find an answer by reading a FAQ.
[*]Try to find an answer by inspection or experimentation.
[*]Try to find an answer by asking a skilled friend.
[*]If you're a programmer, try to find an answer by reading the source code.
[/LIST]
<snip>
**[When you ask,] be precise and informative about your problem**


[LIST]
[*] Describe the symptoms of your problem or bug carefully and clearly. 
[*] Describe the environment in which it occurs (machine, OS, application, whatever).  Provide your vendor's distribution and release level (e.g.: “Fedora Core 7”, “Slackware 9.1”, etc.).  
[*] Describe the research you did to try and understand the problem  before you asked the question. 
[*] Describe the diagnostic steps you took to try and pin down the problem yourself before you asked the question. 
[*] Describe any possibly relevant recent changes in your computer or software configuration. 
[*] If at all possible, provide a way to *reproduce the problem in a controlled environment*. 
[/LIST]



<snip>

"

---


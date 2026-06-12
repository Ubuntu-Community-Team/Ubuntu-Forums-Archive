---
title: "sshd Keeps Re-Spawning"
date: 2010-06-25
forum: General Help
---

### Post by Professor Ducky on 2010-06-25
Hi!

First off, The system in question is using Mint 9, but the forums there aren't as active and since its Ubuntu based I didn't think it would be a concern bringing my problem here. If this is an issue, apologies, lock the thread and I'll head over to the Mint forums.

So I have an SSH server running on the system, but I only like to have it running at certain times, so I removed it from the rc scripts using the command: *sudo update-rc.d -f ssh remove*.

Anyway, later I found that SSH was turning on at boot time anyway. I checked the rc scripts manually and couldn't find reference to it. I then tried to stop the process using the command: *sudo /etc/init.d/ssh stop* which reported that it was working, but after checking the processes and consulting syslog I found that it was re-spawning after I had told it to stop.

I found 2 ways to stop the process without it re-spawning:

*sudo initctl stop ssh*

and 

*sudo service ssh stop*

So whilst I can turn it off at each boot, or script it to shutdown at login, I'm still wondering why update-rc.d isn't working.

Any advice would be greatly appreciated.

Regards

Ducky

---

### Post by ThesaurusRex on 2010-06-25
SSH turning on automatically on your system is so that other systems can potentially connect to you. It doesn't mean you have to connect, or that you will be connected. Plus, OpenSSH isn't even noticeable when it's running on your system. Why do you need it off?

---

### Post by Professor Ducky on 2010-06-25
In short; because I'm paranoid. 

I would rather just have it disabled by default as the system in question is rarely used for ssh, its just nice to have it available as and when I do need it, but it is frustrating me that I've lost a portion of control over my system since the last release.

Regards

Ducky

---

### Post by Professor Ducky on 2010-06-29
Bump?

---


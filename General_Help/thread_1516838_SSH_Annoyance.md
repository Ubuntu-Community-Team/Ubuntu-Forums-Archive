---
title: "SSH Annoyance"
date: 2010-06-24
forum: General Help
---

### Post by ThesaurusRex on 2010-06-24
I'm not new to SSH, but I'm having this rather annoying problem which only occurs with one of my devices. Whenever I reboot the device and try to SSH to the device (for the first time after I reboot), I get the error message that I may be under a middleman attack. Thus, I have to go into my known_hosts file, delete the record of ever being connected to that IP address before, and try to SSH into it again (at which point it always asks me whether or not to accept the key). This wouldn't be too annoying, except for the fact that I'm debugging the heck out of the device and have been rebooting pretty frequently recently. Also, with what I'm doing I'm trying to automate a lot of things, and I don't want to automate going into the known_hosts file and expunging the record, then typing yes after I try to connect.

My question is: Is there a way to get SSH to disregard the fact that there may be a man-in-the-middle attack and just continue connecting?

The device I'm connecting to runs Busybox.

---

### Post by ThesaurusRex on 2010-06-24
I "solved" it. I simply added the following alias into .bashrc:
```
alias ssh=ssh -o UserKnownHostsFile=/dev/null -o StrictHostKeyChecking=no
```
I wouldn't suggest anyone use such an alias unless they were sure they'll only ever connect to computers on their private network and that they are absolutely certain of the IP addresses. Marking thread as closed.

---

### Post by ThesaurusRex on 2010-06-24
Or, even better, I went into the .ssh directory, created a file called "config", and typed:
```
Host 192.168.0.*
   StrictHostKeyChecking no
   UserKnownHostsFile=/dev/null
```
Source: [http://linuxcommando.blogspot.com/2008/10/how-to-disable-ssh-host-key-checking.html]("http://linuxcommando.blogspot.com/2008/10/how-to-disable-ssh-host-key-checking.html")

---

### Post by CharlesA on 2010-06-24
Is the machine getting a new IP address when it reboots? I've not run into that problem with any of the devices I've got running Linux.

---


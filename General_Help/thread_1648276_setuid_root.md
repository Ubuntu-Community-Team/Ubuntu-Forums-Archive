---
title: "setuid root"
date: 2010-12-18
forum: General Help
---

### Post by kaj on 2010-12-18
I have a computer running Ubuntu 10.04 LTS server edition.
I had just installed the drivers to my Canon mp540 printer, but the didn't work. I found out, that the problem was, that the driver files were owned by the regular user in stead of root, allthough i had used sudo during installation.

I then wanted to change the user to root. I cd'ed to /usr/ and wanted to change the owner of directories /bin, /lib, and /share.

First I typed the command sudo chown -R root:root bin, and everything seemed to be fine.
The next command Was sudo chown -R root:root lib, but then I got the reaction:
sudo: must be setuid root.

No matter what I tried, I got the same answer.
Then I tried: setuid root <command> and got the answer:
setuid is currently not installed. You can install it by typing:
sudo apt-get install super
Well, I did that, but it said:
sudo: must be setuid root

It is completely impossible to do any administrator work.
I thought that I could install super from Synaptic, but synaptic cannot open. Neither can other programs or tasks, that need root privileges.

What on earth can I do?

In 10.04 I even cannot open in maintenance mode because it uses grub2 as bootloader.
(Could we please have the old grub back again.)

I have searched this forum, and I have found others in the same situation, and they are advised to to give the command: sudo chown root:root /usr/bin/sudo, but my /usr/bin/sudo is allready owned by root, and guess what the reaction is to this command:
sudo: must be setuid root

---

### Post by kaj on 2010-12-19
Can't anyone give me a hint?

Would it be worth while to send a bug report?

---

### Post by CharlesA on 2010-12-19
You should never chown or chmod system directories using the -R switch. Doing so can have unpredictable, and usually bad, repercussions.

How did you know the driver files were owned by your user and not root?

---

### Post by kaj on 2010-12-20
I found out the hard way, that it is a bad idea.
I found out, who owned the files by looking at the privileges.

I also followed a fault seeking procedure in the print manager, that told me, that the problem was, that the drivers were not owned by root.

It would have been a big job to change the ownership of the files one file at a time, especially when it came to /usr/share/cups/, but I didn't get that far.

Although it is a server, I have a desktop installed. I like it that way, and the machine is for private use only.

---

### Post by CharlesA on 2010-12-20
Best thing to do would be to backup your stuff and reinstall. Permission problems can cause a load of problems down the line.

Perhaps try adding the printer from a livecd to see if it sees it or not.

---


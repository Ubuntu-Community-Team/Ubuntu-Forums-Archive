---
title: "Crashes - Lower file is not in a valid eCryptfs format"
date: 2010-01-10
forum: General Help
---

### Post by silentjon on 2010-01-10
Hello everyone,

Hopefully this won't be too tricky to solve. I should begin by pointing out that I am very very new to Linux so apologies if I am asking simple questions . . .

Right, I seem to get very random system crashes. My machine will stay up for long periods of time, or sometimes only a few mins, also it doesn't seem related to just using a particular program. As you can imagine this is leading to a bag of woes. After reading on a forum about logs I went to /var/log and in the system log found the following entry . . .

"Jan 10 18:46:10 jon-desktop kernel: [   92.718896] Either the lower file is not in a valid eCryptfs format, or the key could not be retrieved. Plaintext passthrough mode is not enabled; returning -EIO"

This is repeated multiple times and having checked after a few crashes seems to be the central problem. Being specific about the crashes, they freeze the entire system. Can't ctl-alt-del and sound loops, have to hard reset.

I have a feeling that when I first installed Ubuntu 9.10 I selected to use an encrypted file system but have a feeling that I didn't set it up correctly. Not sure exactly what I didn't do but I seem to remember it was to do with generating a passphrase.

So . . .

1) What is this error from my logs?
2) Is it linked to me not setting up the encrypted filesystem correctly?
3) Is there a way to check the settings / sort them out properly?
4) Is there documentation for my dullard state which can aid me in this, or is it quite simple?

Thanks very much everyone,

Jon

---

### Post by gazso on 2010-03-03
I know it won't help you but I have the same problem.

When I login to my account and skype asks me to accept the license for the nth time again I know that it happened again. 

I can not even open a terminal window, it comes up blank. Can not logout, it is blank too. Evolution can not retrieve my addressbook from couchDB. 

Then I go to a virtual console and reboot. The system does not come up. There is a need to manually run the fsck, which spits out not only inodes but filenames too.  After booting again, I need to remove my .Skype directory and fix my couchdb.

In the past there were unreadable files too. 

I am running Ubuntu 9.10 at work, which has a SAS disk and it is stable, but at home, which is an SSD, it is very unstable. And yes, I disabled SMART in /lib/udev/rules.d/95-devkit-disks.rules for my SSD drive without which I would not have a single reboot without filesystem corruption.

Is it not possible that SSD is causing this problem? On a separate box I have CentOS 5.4 server with a manually upgraded kernel 2.6.32.8 on an SSD and hdparm destroys the filesystem when I run it. If I don't run it it is very stable.

Do you have an Solid State Disk too?

---

### Post by mrtorrent on 2011-06-10
Sorry to revive an old thread, but I seem to be having the same issue. I've already lost several working days to trying to find a solution with no joy -- did either of you ever come up with anything satisfactory?

Every bug report in Launchpad with the same error messages has been marked as a duplicate of this report: [https://bugs.launchpad.net/ecryptfs/+bug/509180](https://bugs.launchpad.net/ecryptfs/+bug/509180) There's talk of a patch but it's not clear whether it's been released and nobody knowledgeable has replied in a month or more.

---


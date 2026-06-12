---
title: "Boot problem"
date: 2011-06-11
forum: General Help
---

### Post by kronerboner79 on 2011-06-11
Hi Ive been using Ubuntu for a long time, but im still a beginner when it comes to the command lingo.
 
Here's the issue:
 
My computer was at the purple screen, and it said it was trying to fix errors. At the bottom it had three options. The third option was to "manually boot". Not really knowing what it meant, I selected it. My computer rebooted and instead of going from a black screen to the purple loading screen, it displayed a bunch of stuff and then prompted "(initramfs)". I dont know commands at all so when it said type help for built-in command prompts, they all meant nothing to me. Can someone please help me in what to type so I can get it to boot normally again?
 
Thank you

---

### Post by Herman on 2011-06-11
I'm guessing you probably interrupted a routine file system check. 

You should be able to easily fix it by booting your Ubuntu Live CD and opening GParted partition editor, right-clicking on your hard disk-installed Ubuntu partition, and selecting 'check' from the right-click menu. There will be a couple of confirmation buttons to click on to apply the operation, then you will need to wait for a few minutes for the process to complete. After it is over you can reboot and you should (with luck) be able to boot your Ubuntu normally again.

Never attempt to run a file system check on a partition while it is mounted.

Ubuntu and most other GNU/Linux operating systems run a file system check about once every thirty or so boots or once every six months, whichever comes first. When it happens, it's always best to be patient and wait for that to finish as interrupting it could cause file system damage. It normally only takes a minute or so, but larger hard drives and large quantities of file data may take longer.

If you don't want to be delayed by these file system checks occurring unexpectedly, you should use your Ubuntu Live CD or some other Ubuntu to run a file system check on your file systems regularly. File system checks are good for your system and you can run them as often as you like, especially if you have some idle time available.

---


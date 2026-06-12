---
title: "HELP! How do I download and test Kernel?"
date: 2012-08-14
forum: General Help
---

### Post by Alcidious on 2012-08-14
So I reported a screen brightness bug, in Ubuntu 12.04, related to my samsung laptop.  They have determined the problem, and asked me to test a kernel.  I have copied the email below...

I have tried to read up on what to do, but I am still unsure of exactly what I will be doing.  So I download this specific kernel, put it in my source tree, and then what? Do I put it on a separate partition, or do I put it directly into my current OS?  Any help, advice, or pointers directly to related help pages EXTREMELY APPRECIATED!

"Would it be possible for you to test the latest upstream kernel?  Refer
to [https://wiki.ubuntu.com/KernelMainlineBuilds](https://wiki.ubuntu.com/KernelMainlineBuilds) . Please test the latest
v3.5kernel[0] (Not a kernel in the daily directory) and install both the
linux-image and linux-image-extra .deb packages.

Once you've tested the upstream kernel, please remove the 'needs-
upstream-testing' tag.  Please only remove that one tag and leave the
other tags. This can be done by clicking on the yellow pencil icon next
to the tag located at the bottom of the bug description and deleting the
'needs-upstream-testing' text.

If this bug is fixed in the mainline kernel, please add the following
tag 'kernel-fixed-upstream'.

If the mainline kernel does not fix this bug, please add the tag:
'kernel-bug-exists-upstream'.

If you are unable to test the mainline kernel, for example it will not boot, please add the tag: 'kernel-unable-to-test-upstream'.
Once testing of the upstream kernel is complete, please mark this bug as "Confirmed".


Thanks in advance."

---

### Post by Alcidious on 2012-08-14
So, I followed the instructions listed on wiki.ubuntu.com/Kernel/MainlineBuilds, and downloaded the common headers, the i386 headers, and i386 image.  However, there were several .patch files I did not download.  I then ran sudo dpkg -i *.deb from the terminal, and everything was installed.

But when I rebooted, there was no Grub menu to choose which kernel to run.  Did I do something wrong? I am eager to test this kernel to see if my issue is fixed...

---

### Post by Doug S on 2012-08-14
What you described should have worked. 
 
I find that the default grub screen goes by so fast that I don't even see it.
I always make a change to give me time to see it and decide what to do.
edit /etc/default/grub and change this line:```
GRUB_TIMEOUT=2
```to, say, this
```
GRUB_TIMEOUT=15
```Then re-build the grub stuff:```
sudo update-grub
```Note that you will need to edit as super user, ie:```
sudo nano /etc/default/grub
```
 
You might have loaded the desired version of the OS already. Check via```
uname -a
```and/or```
cat /proc/version
```

---

### Post by Alcidious on 2012-08-15
DOUG S, 

Thank you! I did change the grub time, but I haven't checked yet to see if it comes up when I boot.  The time was already set to 10, but perhaps b/c I am only running one partition, it just skipped the grub process?  Is there something else in the grub file to look at to see if that is the issue?

As to the kernel, I ran the commands you suggested, and my laptop is running the downloaded kernel.  So far my flickering/brightness issue has not returned, so I am happy with it.  But will this affect my updates or support or anything like that? If I find that it works, should I tell the bug squad, and then delete the new kernel? I really appreciate it!

---

### Post by Doug S on 2012-08-15
Interesting. I have only known the default time to be 2. I don't know why you didn't see the menu if it was 10. Do you have a "GRUB_HIDDEN_TIMEOUT" line? If yes, try commenting it out.
 
Yes, I would suggest to delete the test kernel once you have finished testing. I had an issue just earlier today where I had forgotten to delete a test 3.5RC7 kernel and some updates were applied to it (i.e. it re-did the boot stuff) instead of the proper 3.2.-29 #46 one. Definately update the launchpad bug report, but be patient it can take awhile before the fix will find its way to a 12.04 kernel update. If your issue is very annoying. you could continue to run the fixed kernel.

---

### Post by Alcidious on 2012-08-15
This is what the file says:

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=15
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

I've never really altered these types of files, except to add an apt repository.  So, to comment it out, should I comment out Hidden_Timeout_Quiet="true",or Hidden_Timeout="0", or both?

Also, yes, the issue is incredibly annoying.  I have to reboot several times to get it to work, and sometimes I don't. I was thinking about just not allowing updates until I manually install them, and I figured I could just not use any of the kernel updates? Would that work, at least until they finally patch it?  Thanks a bunch!

---

### Post by Doug S on 2012-08-15
change to this:```
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=15
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

```Yes, you should be O.K. until the fix is backported.

---

### Post by Alcidious on 2012-08-15
Thanks a bunch Doug! That was one heck of  a learning experience!

---


---
title: "Choice of kernels at boot: How can I get it back?"
date: 2011-10-25
forum: General Help
---

### Post by bjrnfrdnnd on 2011-10-25
Hello, 

i seem to have the opposite problem than many other people.
My 11.04 ubuntu does NOT give me a choice of kernels when it boots.
I do have a number of them installed though.

I have a problem with Virtualbox and the newest kernel, and would like to run 
one of the older kernels, but as I do not have grub asking me for the kernel, 
I do not know how to do that. 

I installed startupmanager and changed the default kernel, but it still boots on the newest 
kernel. 

I also unchecked the splash checker and checked the thting that it should start in text.

No change. 
It always boots with the newest kernel, never asks.

What can I do?

---

### Post by duke.tim on 2011-10-25
Take a look at this thread, i'm assuming you are using grub2

[http://ubuntuforums.org/showthread.php?t=1285897](http://ubuntuforums.org/showthread.php?t=1285897)

---

### Post by bjrnfrdnnd on 2011-10-26
I seem to be using grub:

```
dpkg --get-selections |grep grub
```

gives this output:

grub-common					install
grub-gfxpayload-lists				install
grub-pc						install

On the other hand, I do have the 
/etc/grub.d 
directory with all the files in there that were mentioned in your link.

I have no 
/boot/grub/menu.lst


My startupmanager does not look like this:
[http://www.ubuntugeek.com/startup-manager-change-settings-in-grub-grub2-and-usplash.html]("http://www.ubuntugeek.com/startup-manager-change-settings-in-grub-grub2-and-usplash.html")

but rather like the pictures in the attachments.
The choices for the "Default operating system" are also attached.

---

### Post by Dave_L on 2011-10-26
Edit /etc/default/grub and comment out this line, so that the boot menu will display:

```
#GRUB_HIDDEN_TIMEOUT=0
```

Then run update-grub to propagate the change to /boot/grub/grub.cfg:

```
sudo update-grub
```

---

### Post by bjrnfrdnnd on 2011-10-26
That worked, thanks.
Am I running grub or grub2?

---

### Post by Dave_L on 2011-10-26
Since the above worked, it must be grub 2.

To check the version:

```
$ grub-mkconfig -v
/usr/sbin/grub-mkconfig (GNU GRUB 1.98-1ubuntu12)
```

Even though the number 1.98 is a bit less than 2, it's called "grub 2".

---


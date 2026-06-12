---
title: "Change My Account Type Back To Administrator"
date: 2012-05-21
forum: General Help
---

### Post by EDLIU on 2012-05-21
Hi,

I accidently changed my account type from "Administrator" to "Standard".

Now I want to change back my account type to "Administrator" but was asked to enter the "Root Pwd".

What's my "Root Pwd"? I have entered the pwd that I created when installing my Ubuntu, but it did not work.

So what should I do?

Thanks.

Ed

---

### Post by zombifier25 on 2012-05-21
Enter a terminal and post this:
```
id
```
and post the output.

---

### Post by EDLIU on 2012-05-21
> **zombifier25 said:**
> Enter a terminal and post this:
```
id
```and post the output.

uid=1000(rickliu) gid=1000(rickliu) groups=1000(rickliu),4(adm),20(dialout),24(cdrom),46(plugdev),116(lpadmin),124(sambashare)

Thanks.

Ed

---

### Post by zombifier25 on 2012-05-21
I see the problem. You are not in the group *sudo* (or *admin* for Ubuntu 11.10 and below), which is required in order to sudo.
Reboot your machine, choose recovery mode at Grub, get into root prompt and type this command:
```
adduser rickliu sudo
```
for 12.04 only. For other versions of Ubuntu, do the following instead:
```
adduser rickliu admin
```

---

### Post by EDLIU on 2012-05-21
> **zombifier25 said:**
> I see the problem. You are not in the group *sudo* (or *admin* for Ubuntu 11.10 and below), which is required in order to sudo.
Reboot your machine, choose recovery mode at Grub, get into root prompt and type this command:
```
adduser rickliu sudo
```for 12.04 only. For other versions of Ubuntu, do the following instead:
```
adduser rickliu admin
```

Hi,

Can I change the settings from "System Settings/User Account"?

Will I need the "Root PWD" to change the settings?

What is my "Root PWD"?

Thanks.

Ed

---

### Post by zombifier25 on 2012-05-21
No (because your user is no longer allowed to change system-wide settings), no and no need (getting into recovery mode will give you full root access without needing password).

---

### Post by EDLIU on 2012-05-21
> **EDLIU said:**
> Hi,

Can I change the settings from "System Settings/User Account"?

Will I need the "Root PWD" to change the settings?

What is my "Root PWD"?

Thanks.

Ed

Hi,

I booted into "Recover Mode". But the screen freezes at Recovery Menu. I can't select the "root Drop to root shell prompt.

What do I do?

Thanks.

Ed

ps. I'm running the Ubuntu 11.10 on my Mac. It's a triple boot.

---

### Post by EDLIU on 2012-05-22
> **EDLIU said:**
> Hi,

I booted into "Recover Mode". But the screen freezes at Recovery Menu. I can't select the "root Drop to root shell prompt.

What do I do?

Thanks.

Ed

ps. I'm running the Ubuntu 11.10 on my Mac. It's a triple boot.


Any one that can help me?

Thanks.

ED

---

### Post by JKyleOKC on 2012-05-22
> **EDLIU said:**
> Hi,

I booted into "Recover Mode". But the screen freezes at Recovery Menu. I can't select the "root Drop to root shell prompt.Are you trying to select it using the mouse? If so, try using the up and down arrows. In at least some versions, the recovery mode menu is actually a terminal window in which the mouse doesn't work.

If you can highlight the "drop to root shell" line with the arrow keys, then just hit Enter and you should get the root prompt, ending with "#" to let you know it's running as root. From there, add the group to your user name. No "sudo" is necessary at this point. When the prompt returns, then reboot and log in normally.

---

### Post by EDLIU on 2012-05-22
> **JKyleOKC said:**
> Are you trying to select it using the mouse? If so, try using the up and down arrows. In at least some versions, the recovery mode menu is actually a terminal window in which the mouse doesn't work.

If you can highlight the "drop to root shell" line with the arrow keys, then just hit Enter and you should get the root prompt, ending with "#" to let you know it's running as root. From there, add the group to your user name. No "sudo" is necessary at this point. When the prompt returns, then reboot and log in normally.


The Recovery Menu showed:

2.985730 usb 3-1.1 : new full speed usb device number 3 using uhci_...

And I still cannot use "Up & Down Arrow Keys" to select the Recovery Mode in the Recovery Menu.

Thanks.

Ed

---

### Post by JKyleOKC on 2012-05-22
What you report as being on the screen appears to be part of the (usually hidden) running report of boot-up actions. It indicates that the boot sequence got as far as attempting to enable a USB port, and froze up at that point.

This, in turn, suggests that the system isn't getting as far as actually displaying the recovery-mode menu. Possibly the GRUB loader has been damaged. I'll have to leave it to other people, more expert in troubleshooting boot problems than I am, to come to your aid for this one!

I'm sure that the problem can be solved, but not sure on the exact steps that will be needed to solve it. All I can recommend is patience until a more expert forum member shows up to assist!

---

### Post by EDLIU on 2012-05-22
> **JKyleOKC said:**
> What you report as being on the screen appears to be part of the (usually hidden) running report of boot-up actions. It indicates that the boot sequence got as far as attempting to enable a USB port, and froze up at that point.

This, in turn, suggests that the system isn't getting as far as actually displaying the recovery-mode menu. Possibly the GRUB loader has been damaged. I'll have to leave it to other people, more expert in troubleshooting boot problems than I am, to come to your aid for this one!

I'm sure that the problem can be solved, but not sure on the exact steps that will be needed to solve it. All I can recommend is patience until a more expert forum member shows up to assist!

Thanks.

Ed

---

### Post by kanikilu on 2012-05-22
Sorry, I can't help with the booting to recovery issue (hopefully this at least serves as a thread bump). That said, having just gone through this myself yesterday, I thought I should mention that if you do get to a root shell, you'll need to remount the root (/) partition as read-write. Otherwise, the adduser command will fail...

```
mount -o rw,remount /
```

You can use this guide for reference, but note that since you don't need to change your password, you don't need to do that step:

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by EDLIU on 2012-05-23
Hi,

So what should I do?

Can you give me "step by step" procedures since I'm new to Ubuntu and Linux?

Thanks.

Ed

---

### Post by kanikilu on 2012-05-23
> **EDLIU said:**
> Hi,

I booted into "Recover Mode". But the screen freezes at Recovery Menu. I can't select the "root Drop to root shell prompt.

What do I do?

Can you describe what you mean by it "freezes"? Do you see the menu? This may be a really dumb question, but you aren't trying to use your mouse in that menu, are you? It'll only accept keyboard input, so use the cursor/arrow keys to move down to "drop to root shell" and press enter/return.

If you already knew that and the keyboard doesn't even work, are you using a wireless or bluetooth keyboard? If so, maybe try a wired keyboard if you have access to one...

---

### Post by EDLIU on 2012-05-23
> **kanikilu said:**
> Can you describe what you mean by it "freezes"? Do you see the menu? This may be a really dumb question, but you aren't trying to use your mouse in that menu, are you? It'll only accept keyboard input, so use the cursor/arrow keys to move down to "drop to root shell" and press enter/return.

If you already knew that and the keyboard doesn't even work, are you using a wireless or bluetooth keyboard? If so, maybe try a wired keyboard if you have access to one...

The computer runs to the Menu. And freezes at the menu. On the screen, shows the message i mentioned above.

It's a mouse link to the keyboard that link the the machine by usb.

Thanks.

Ed

---

### Post by kanikilu on 2012-05-23
Oops, apparently I missed that part of the thread, sorry. Anyways, I'm not really sure what to suggest. Do you have another keyboard you can try - plugged directly into the computer, not through any other devices or hubs? Unplug anything else...

Actually, I found a similar topic on askubuntu, and people seem to suggest the same:

[http://askubuntu.com/questions/75358/how-do-i-get-my-usb-keyboard-to-not-freeze-up-in-the-recovery-menu](http://askubuntu.com/questions/75358/how-do-i-get-my-usb-keyboard-to-not-freeze-up-in-the-recovery-menu)

---

### Post by EDLIU on 2012-05-25
> **zombifier25 said:**
> I see the problem. You are not in the group *sudo* (or *admin* for Ubuntu 11.10 and below), which is required in order to sudo.
Reboot your machine, choose recovery mode at Grub, get into root prompt and type this command:
```
adduser rickliu sudo
```for 12.04 only. For other versions of Ubuntu, do the following instead:
```
adduser rickliu admin
```

I cannot boot into "recovery mode at Grub". So I just boot into Unbuntu.

I tried to "adduser rickliu admin" but it didn't work.

So what should I do now?

Thanks.

Ed

---

### Post by EDLIU on 2012-05-25
> **JKyleOKC said:**
> What you report as being on the screen appears to be part of the (usually hidden) running report of boot-up actions. It indicates that the boot sequence got as far as attempting to enable a USB port, and froze up at that point.

This, in turn, suggests that the system isn't getting as far as actually displaying the recovery-mode menu. Possibly the GRUB loader has been damaged. I'll have to leave it to other people, more expert in troubleshooting boot problems than I am, to come to your aid for this one!

I'm sure that the problem can be solved, but not sure on the exact steps that will be needed to solve it. All I can recommend is patience until a more expert forum member shows up to assist!

Thanks. Appreciated.

Ed

---

### Post by kanikilu on 2012-05-25
Did you try another keyboard or at least make sure it was plugged directly into the computer (not through a USB hub), and remove all other devices?

According to the thread I posted earlier, other people have experienced this same issue, and that's how they fixed it...

There's also a bug filed, that says a fix is released, but people have continued to report the same issue:

[https://bugs.launchpad.net/ubuntu/+source/friendly-recovery/+bug/203385](https://bugs.launchpad.net/ubuntu/+source/friendly-recovery/+bug/203385)

Lastly, I've never tried this method, but supposedly you can change your group membership from the Live CD/USB, if you have one handy:

[https://help.ubuntu.com/community/LiveCdRecovery](https://help.ubuntu.com/community/LiveCdRecovery)

The section you'd want is "Add user to group" and the *groupname* you'd use would be sudo if on 12.04 or I think admin if on an earlier version.

---

### Post by EDLIU on 2012-05-26
Hi,

I found the "LiveCdRecovery" from Ubuntu's official website.

It said that it can fix the boot problems from the live CD.

But I'm running Ubuntu 11.10 right now, should I use the 11.10 version or the lately released 12.04 LTS version?

Thanks.

Ed

ps. I cannot find the Ubuntu Live CD download for the v.11.10.

---

### Post by EDLIU on 2012-05-29
> **EDLIU said:**
> Hi,

I found the "LiveCdRecovery" from Ubuntu's official website.

It said that it can fix the boot problems from the live CD.

But I'm running Ubuntu 11.10 right now, should I use the 11.10 version or the lately released 12.04 LTS version?

Thanks.

Ed

ps. I cannot find the Ubuntu Live CD download for the v.11.10.


Anyone that can help me?

Thanks in advance.

Ed

---


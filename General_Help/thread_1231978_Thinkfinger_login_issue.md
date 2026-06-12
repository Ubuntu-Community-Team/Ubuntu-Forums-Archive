---
title: "Thinkfinger login issue"
date: 2009-08-05
forum: General Help
---

### Post by Paresh on 2009-08-05
Hey guys

I used this [guide]("http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader_with_ThinkFinger") to enable the fingerprint reader on my Toshiba laptop, running an up-to-date 9.04 installation.

It's working fine, but I have an issue with the network manager applet, and private folders (ecryptfs).

If I power up and login and type my password, network manager logs in and connects to my wireless network automatically, and my private folder auto mounts, ready for use.

However, if I login by swiping my finger, I then need to login to the keyring to allow the network manager to connect to my wifi and need to manually mount the private folder.

How do I configure my login so that fingerprint works the same as typing in the password?

---

### Post by jsuhr on 2009-08-07
Same issue here. It looks like bugs 221900 and 276384. Not sure if it is a legitimate bug, or how bugs are classified here, it just doesn't send password info to keyring. I'd be surprised if there is not at least one way to do this, if anyone has a solution we'd love to hear it, and thanks in advance.

---

### Post by mad0master on 2009-09-01
I have Lenovo T61 and Ubuntu 9.04.

It works. But! It initializes slowly. I need to wait 5-7 seconds before I swipe my finger.

Configured as described on the thinkwiki page

---

### Post by Paresh on 2009-09-01
The scanner works as I can login by swiping my finger.

the issue for me is that the authentication is not passed on in quite the same way that typing the password is.

---

### Post by mad0master on 2009-09-01
Yep, that doesn't work.
It requires the password to be entered one more time for keyring

---

### Post by Paresh on 2009-09-02
Well, you've now put your finger on the problem :D

bump (in case anyone has a solution)

---

### Post by P4man on 2009-09-02
keyring is not opened when you enable automatic login. Im guessing the thinkfinger thing logs you in in a similar way, or at least the keyring app for some reason thinks you didnt log in through gdm.

Perhaps this solutions works:

[http://maketecheasier.com/auto-unlock-keyring-manager-in-ubuntu-intrepid/2009/03/14](http://maketecheasier.com/auto-unlock-keyring-manager-in-ubuntu-intrepid/2009/03/14)

---

### Post by Paresh on 2009-09-02
Sorry, I'm not a fan of blank passwords, but I'll give it a try over the next day or so and see if that works.

But it cannot be a permanent solution.

---

### Post by P4man on 2009-09-02
its the only way im afraid.

[https://bugs.launchpad.net/gnome-keyring/+bug/276384](https://bugs.launchpad.net/gnome-keyring/+bug/276384)

If you read through that thread, you'll understand why its impossible to securely save passwords and decrypt them with a stroke of the finger (short story: the password itself is the secret that unlocks the encrypted keys in the keyring. A fingerprint is too random to do that.).

If you are worried about security, you shouldn't be relying on fingerprints, or at least not to decrypt all your passwords, so having to enter a password makes sense. If you're not concerned about that, then having a blank keyring password could be an acceptable risk.

---

### Post by bjo101 on 2009-10-21
.Can someone please give me step by step direction to configure thinkfinger on Ubuntu 9.10.  It allows me to enroll fingerprints and verify them, however I do not get the swipe finger or enter password prompt when using su or sudo or in the gdm.  Below is a list of what I have done

1. Install Thinkfinger packages from repos.
enrolled and verified fingerpring for my use account and root.
3, edited /etc/pam.d/common-auth accounding to think wiki fior Jaunty suince karmic isn't covered.
4. Enabled the fingerprint rader using the command listed in the think wiki
5. Created /etc/udev/rules.d/60-thinkfinger.rule as discribed in the think wiki
[COLOR=Black]6. Executed the above file with udevadm trigger as descibed in the Think wiki
7. Edited /etc/pam.d/gnome-screensaver as described in the thinkwiki
8. Edited rc.local file with the following lines
modprobe uinput
chmod a+r /dev/input/uinput
so uinput would load on startup.

Is their something elswe I need tio do to see the prompt at the terminal and the gdm and screensaver?


[/COLOR]

---

### Post by bjo101 on 2009-10-24
Please disregard my previous post I was able to resolve the issue on my own.

Thanks.

---

### Post by sibble on 2009-11-03
> **bjo101 said:**
> Please disregard my previous post I was able to resolve the issue on my own.

Thanks.

What did you do?

---


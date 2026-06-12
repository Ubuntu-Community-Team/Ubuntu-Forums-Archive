---
title: "Why doesn't everything continue to work after an upgrade?"
date: 2011-07-06
forum: General Help
---

### Post by unckybob on 2011-07-06
I'm just a newbie to this operating system. Even though I'm having some trouble, it still seems more sensible to me than Windows. I'd like to continue to use it, but I'd like to know why it doesn't work for me sometimes, and I'd like to see if I can't make it work better for me.

After I upgraded to 11.04 I've had a host of problems. My USB ports have intermittant trouble recognizing storage devices. My USB ports also have intermittant trouble recognizing my USB WiFi device. The VLC player will crash the Gnome Desktop whenever I use it. I still haven't figured it out.

I'm interested in the following question:

Why can't software and hardware that already works be insured to continue to work after an upgrade?

I would like to read more about this subject. If anyone can recommend any reading or study about this subject, I'd really appreciate your direction.

Thanks.

---

### Post by u.rusty on 2011-07-06
Sometimes, considering the vast number of possible hardware combinations, I'm amazed operating systems work at all.

Have you installed updates?

```

sudo apt-get update

sudo apt-get upgrade

```

---

### Post by TeoBigusGeekus on 2011-07-06
IMHO, never upgrade ubuntu; always go for a clean installation.
I've never done an upgrade that resulted in a functioning system; others in these forums have experienced exactly the opposite.
...however, 11.04, even with a clean installation, is extremely buggy - if you don't have a particular reason for installing natty, stay with lucid or maverick.

---

### Post by Cheesehead on 2011-07-06
> **unckybob said:**
> Why can't software and hardware that already works be insured to continue to work after an upgrade?

Ubuntu is community based, so a more appropriate question may be 'What can I do to ensure good QA?'

Somebody (including lots of volunteers) must do that testing. The [Ubuntu Testing Team]("https://wiki.ubuntu.com/Testing") welcomes new members to do precisely that. You may have hardware that the team doesn't have access to, so is not currently being tested - you can change that.

You should report update-reversions and other bugs to the bug tracker. Unreported bugs won't get fixed. The [wiki]("https://wiki.ubuntu.com") and this forum have a lot of good information on how to troubleshoot your problems to see if they are reportable bugs, and how to report them with enough detail so they can be Triaged and fixed. Once you understand the process, please use your new skills to help others.

---


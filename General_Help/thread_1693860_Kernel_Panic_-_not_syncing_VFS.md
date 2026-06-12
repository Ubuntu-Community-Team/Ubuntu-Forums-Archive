---
title: "Kernel Panic - not syncing VFS"
date: 2011-02-23
forum: General Help
---

### Post by epud on 2011-02-23
I get this Kernel Panic when I start my PC once in a while. After a restart or two it boots normally. I have included a screenshot taken with my camera. Anybody have any idea what this is and how I can get rid of it?

[IMG]http://s3.amazonaws.com/twitpic/photos/full/246855308.jpg?AWSAccessKeyId=0ZRYP5X5F6FSMBCCSE82&Expires=1298485256&Signature=w1PVPTPopgCdX%2BjLW2Za0GNiARk%3D[/IMG]

Cheers

---

### Post by An Sanct on 2011-02-23
Greetings!

I see no screenshot :)

*Same as tych*... 
Could you  please post the contents of the kernel log? You can find it throug  System > Administration > Log File Viewer, named something like  "kern.log" or "kern.log.1" or, from terminal in this directory ```
/var/log/kern.log
```

---

### Post by epud on 2011-02-23
Hello.

Here is a part of the Kernel log which I think might be of interest. I have also uploaded the photo of the screen.

Thanks

---

### Post by An Sanct on 2011-02-24
Hm ... Is it a custom kernel build? (there is no support for that)

Maybe take a [look here]("http://kerneltrap.org/node/7053")

---

### Post by epud on 2011-02-24
It is not a custom kernel build. I would not even know where to start to change the kernel. This problem happens about one time in 5 startups. To get past the problem I restart the PC, but it keeps coming back.

It is a problem for me as I sometimes reboot the computer remotely through ssh.

Thanks for your help so far!

---

### Post by An Sanct on 2011-02-24
Wow, browsing the net, I found, that this is a more common problem, then I thought...

But since you say it happens every now and then (thus not always), my guess would be, that you have some bad memory in that box, please try running memtest86...

For the resources I found take a look [here]("http://www.linuxquestions.org/questions/linux-newbie-8/vfs-cannot-open-root-device-sda3-or-unknown-block-0-0-a-409426/"), again [something from kerneltrap]("http://kerneltrap.org/node/2318"), something [here]("http://www.linuxquestions.org/questions/gentoo-87/diskless-kernel-panic-not-syncing-no-init-found-try-passing-init%3D-option-to-kernel-798110/"), a [launchpad bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/290504") its actually a duplicate of [this.]("https://bugs.launchpad.net/bugs/286285")

---

### Post by epud on 2011-02-24
Thank you very much for investing your time in this. It is appriciated.

You are right. I have bad memory in my PC. When I do the memtest86 I get the following error:

```
error: too small lower memory 0x99100 > 0x93400
```

What memory are we talking about here? The RAM? How would I fix this?

I see a possible solution from one of the forum links you sent me. I might try that. Thanks.

---


---
title: "dual boot?"
date: 2010-10-09
forum: General Help
---

### Post by fjsimpkins on 2010-10-09
Good morning!!! So recently I installed Kubuntu 10.04 beside Ubuntu 10.04. I read it would work smoother and be less bloated as  opposed to adding kde to my ubuntu desktop. Anyways to make a long story short I want ubuntu to stay in place. I would like to switch out kubuntu for a different distro to just mess around with. My only problem is the last time i went from dual boot to single or changed one of the distros via livecd i was unable to boot into either of them. I only had a black screen. Any advice on how to avoid this. Would it be a GRUB issue? Thanks in advance

Jim

---

### Post by xjesse on 2010-10-09
Most distributions do a very good job of detecting currently installed operating systems. Of course, just be sure not to format the the partition Ubuntu is installed on and yes, you want to install Grub on the master boot record. 

What other distro did you have in mind?

---

### Post by fjsimpkins on 2010-10-09
well my wife likes ubuntu and fedora. they both seem to work well for her. i tried dual booting with fedora but its kind of beyond me. i read a few forums that said do fedora first because ubuntu uses grub 2 which would auto detect fedora but I get nothing when I do that. I'd like to give debian a shot again and leave ubuntu intact for my wife fran. There were a few issues with debian that made it harder for her to do her college work ie( screen resolution was distorted, wireless not working) I just dont want to get the black screen again considering shes in school. Thank you for the quick reply

---

### Post by xjesse on 2010-10-09
With Debian, I actually recommend trying out Debian *testing*. I had better luck with Squeeze than Lenny as far as wireless goes and applications aren't so outdated. 

I've never actually dual booted two distributions. I'm the type to either run it in a virtual box or flat out install it and give it a go. However, I do remember installing the lastest Fedora over Ubuntu and it did ask if I wanted to install them side by side. Obviously I chose no so I'm not exactly sure how the outcome would have been as far as Grub. One could only assume it would work correctly. I wish I could be of more help! But you definitely want to try out Debian's Squeeze. :)

---

### Post by fjsimpkins on 2010-10-09
I'll check out Squeeze sometime. To my understanding you had ubuntu installed first and then popped in the fedora disc? i can try that too. Thanks for the info.

---

### Post by xjesse on 2010-10-09
> **fjsimpkins said:**
> I'll check out Squeeze sometime. To my understanding you had ubuntu installed first and then popped in the fedora disc? i can try that too. Thanks for the info.

Yep, I had Ubuntu installed and Fedora detected it during install. I did some quick browsing on the Fedora forums and I can see why you had/may have trouble with dual booting. Regardless of what you try, be sure to back up any important data just in case the worst happens. However, it seems as people are installing Fedora over Ubuntu and only being able to boot into Fedora. Obviously you will be able to edit Grub through Fedora so I'm sure there's a way to make it work. This is just from what I've read just now. Ha.

Good luck and have fun. It's all about learning. :P

---

### Post by fjsimpkins on 2010-10-09
Hey thanks for looking that stuff up. I'll make back ups for sure. Im always trying to learn something new. A little off topic but I just started researching scripting. Im hoping to make a script to install the apps i use that dont come preloaded. Thanks again for the help

---


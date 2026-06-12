---
title: "Compiling Linux"
date: 2011-06-15
forum: General Help
---

### Post by UART16550 on 2011-06-15
I am compiling the Linux kernel for the second time around.

I'm up to the 'make config' command... Now its asking me a tone of questions, such as which drivers I wish to include in the kernel.

Is there a nice simple way to just compile the damn thing without the 5000 questions?

---

### Post by Barrucadu on 2011-06-15
Yes, just reuse the config of an existing build.

---

### Post by UART16550 on 2011-06-15
There isn't another existing build.

---

### Post by moma on 2011-06-15
Hello,
Take the old .config file from /boot directory.
See:
$ [COLOR="Green"]ls -l /boot/config-*[/COLOR]

An example:
# [COLOR="green"]cd /usr/src/linux[/COLOR]
# [COLOR="green"]cp /boot/config-2.6.38-8-generic  .config[/COLOR]

Then 
# [COLOR="green"]make oldconfig [/COLOR] # Apply the old config
# [COLOR="green"]make menuconfig[/COLOR]  # New kernel features

Some distros [compress and bake]("http://www.linuxinsight.com/proc_config.gz.html") the config into the kernel, but ubuntu does not.
$ [COLOR="Green"]zcat /proc/config.gz[/COLOR]

---

### Post by UART16550 on 2011-06-15
I'd rather not depend on previous existences. I am starting from scratch.

---

### Post by jhonan on 2011-06-15
Yeah, but the config file is basically the list of answers to the questions you're answering when you compile. It just makes it easier to read it from a file rather than doing the yes/no thing every time.

---

### Post by Bandit on 2011-06-15
> **jhonan said:**
> Yeah, but the config file is basically the list of answers to the questions you're answering when you compile. It just makes it easier to read it from a file rather than doing the yes/no thing every time.

Exactly, plus it doesnt stop you from going through and removing all the crap out like Ham Radio or Voodoo video drivers I am sure you will need next week. ;-)

---

### Post by UART16550 on 2011-06-15
I see, thanks!

Is there any other way?

---

### Post by hakermania on 2011-06-15
> **UART16550 said:**
> I'd rather not depend on previous existences. I am starting from scratch.

but if you are starting from scratch then specif what you want

---

### Post by MadCow108 on 2011-06-15
there is kernelcheck which makes compiling it a little easier.
[https://launchpad.net/kernelcheck](https://launchpad.net/kernelcheck)
its been a while since I last used it, don't know how it works now

---

### Post by UART16550 on 2011-06-15
Thanks for that, but I want to compile with official Linux way only.

I think theres not going to be any 'easy' way, I think I am gonna have to sit it out and answer all the questions.


Thanks for all your input!

---

### Post by jhonan on 2011-06-15
> **UART16550 said:**
> I see, thanks!

Is there any other way?
You're trying to compile the kernel. The kernel needs to know what to include, you can either tell it at compile time with the yes/no (5000 questions as you called it) OR you can tell it in a config file.

Either way you'll have to set up the config file, at least once. Whether you start from a pre-existing config (the easiest way) or lovingly hand-craft a config file from scratch (more difficult) it's up to you.

But there is no other way - The kernel needs a config file, otherwise it won't know what to include in the compile.

---

### Post by 3Miro on 2011-06-15
Use Menuconfig
```
make menuconfig
```

It is much easier, simpler, friendlier and more helpful.

---

### Post by wizard10000 on 2011-06-15
> **UART16550 said:**
> I'd rather not depend on previous existences. I am starting from scratch.

Then you get to answer 5000 questions  :D

---


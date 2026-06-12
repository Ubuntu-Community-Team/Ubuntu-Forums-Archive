---
title: "Get faster boot."
date: 2011-10-02
forum: General Help
---

### Post by vaporise on 2011-10-02
my boot time is just under 1 min.is it possible to reduce it further?here is my bootchart

> [http://dl.dropbox.com/u/8663680/natty-20111002.png](http://dl.dropbox.com/u/8663680/natty-20111002.png)Thanks for the help.:)

---

### Post by Megaptera on 2011-10-02
I'm just curious, how many times a day do you re-boot that you need to try to shave a few seconds off that boot time?

---

### Post by dino99 on 2011-10-02
you can deactivate some apps from loading at boot time via the menu

---

### Post by vaporise on 2011-10-02
> **Megaptera said:**
> I'm just curious, how many times a day do you re-boot that you need to try to shave a few seconds off that boot time?

just wanted to see how low i can make it without a ssd drive.

i have disabled splash,
i mount only root filesystem at boot,
disabled all services i dont use (bluetooth etc).

what else can be done?or this this the lowest it can get on my configuration?

---

### Post by dodo3773 on 2011-10-02
Under a minute is not that bad. It depends on your hardware specs though. I guess the real questions are how much are you willing to sacrifice and how much time and effort are you willing to spend? Some things I can think of right off the bat are:

You could use a lighter desktop environment / window manager (you may miss a lot of the features and user-friendly ease of use that you are used to). 

You could disable services / daemons from auto-loading at boot (then you would have to start them manually if you wanted to use applications that depend on them). 

You could compile your own kernel specific to your hardware needs (might not speed it up that much though (also it might be a long and complicated process)).

You could try out e4rat (this one worked really well for me).

I would say e4rat + a lighter window manager would probably get you the biggest speed increase.

---

### Post by ajgreeny on 2011-10-02
How much of that time is the real ubuntu bootup, and how much is your BIOS running the POST, etc etc?

 It takes my fairly old desktop system quite a large percentage of the total time from power-switch to desktop just to get through the POST and reach grub, then the rest is fairly quick.

Is yours the same?

---

### Post by vaporise on 2011-10-02
> **ajgreeny said:**
> How much of that time is the real ubuntu bootup, and how much is your BIOS running the POST, etc etc?

 It takes my fairly old desktop system quite a large percentage of the total time from power-switch to desktop just to get through the POST and reach grub, then the rest is fairly quick.

Is yours the same?

no,the time mentioned is for ubuntu boot up only..

@[dodo3773]("http://ubuntuforums.org/member.php?u=912419") i'll try e4rat,thanks

---


---
title: "Google Chrome Crashes"
date: 2012-05-21
forum: General Help
---

### Post by Shadius on 2012-05-21
Hey everybody, 

I'm on Ubuntu 12.04. Sometimes, Google Chrome abruptly crashes! It's highly frustrating at this point. I did some Google-ing and found that signing into Google Chrome and allowing it to sync might cause it to crash so I stopped signing in, but it still crashes! I'll try to restart it, and it'll crash over and over and over! By now, I'm so mad that steam is coming out of my ears! What is the problem here? Please, I beg you, help me!

---

### Post by raja.genupula on 2012-05-21
what version you are using ?

could you stalk at what actions google chrome moving to crash , is it specific / Random ?

---

### Post by vasa1 on 2012-05-21
> **Shadius said:**
> Hey everybody, 

I'm on Ubuntu 12.04. Sometimes, Google Chrome abruptly crashes! It's highly frustrating at this point. I did some Google-ing and found that signing into Google Chrome and allowing it to sync might cause it to crash so I stopped signing in, but it still crashes! I'll try to restart it, and it'll crash over and over and over! By now, I'm so mad that steam is coming out of my ears! What is the problem here? Please, I beg you, help me!

Without Chrome running, rename your profile to something else to back it up and to automatically create a new one. Your profile is a folder called **Default** and should be here:
~/.config/google-chrome/Default (I'm typing this from memory) so please verify.

BTW, no problems for me with Chrome 19 on Ubuntu 12.04.

---

### Post by Shadius on 2012-05-21
> **raja.genupula said:**
> what version you are using ?

could you stalk at what actions google chrome moving to crash , is it specific / Random ?

Hey Raja,

I'm using version 19.0.1084.46. It seems to be random crashes. I'll be surfing the internet and boom, crash!

---

### Post by kcallis on 2012-06-24
> **raja.genupula said:**
> what version you are using ?

could you stalk at what actions google chrome moving to crash , is it specific / Random ?

I run into the problem and time I download a file. To be more specific, I might able to download a file, but if I follow up with another file, it crashes.

I am using Version 21.0.1180.0 dev, and I will add that I do have a nvidia graphics chip running:

Operating System: Linux-x86_64
NVIDIA Driver Version: 295.49

This is one bug that is driving me nucking futs!

](*,)

---

### Post by initialhit on 2012-09-23
Hey yall, did a ton of digging on this to find out it is caused mismatch between the new Chrome and nvidia... simply put, if you use the NVidia driver and the Chrome it will crash sooner or later. Best bet is to download a slightly older Chrome and do not update it ;)

---

### Post by initialhit on 2012-09-23
Found one solution I think, download the rpm version and install using yum localinstall option (requires you to download yum, sudo apt-get install yum). Hope this helps yall!

---


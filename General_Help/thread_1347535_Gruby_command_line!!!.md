---
title: "Gruby command line!!!"
date: 2009-12-06
forum: General Help
---

### Post by w_1_n_d on 2009-12-06
For some reason now when i boot linux i get the "GNU command line " interface and idk how to use it and i don't want to use it i want to use the other one that was there before....u know the one were u wana select what you wana boot....some plz help..i can;'t get on linux anymore!!! ;'(



i get a command line :( idk what to type...i used to get a menu but now i don;t :(

---

### Post by sikander3786 on 2009-12-06
Can't understand what is happening. Does the GRUB menu show up? Do you have a choice to choose between kernels and recovery mode? Are you dual booting?

---

### Post by w_1_n_d on 2009-12-06
i get a command line :( idk what to type...i used to get a menu but now i don;t :(

---

### Post by sikander3786 on 2009-12-06
Are you dual booting? Is Ubuntu installed inside Windows (Wubi)?

---

### Post by ibuclaw on 2009-12-06
What does the prompt look like?

Does it look like this?
```
grub> 
```
Regards
Iain

---

### Post by w_1_n_d on 2009-12-06
yes i have windows vista and ubuntu 9.04 installed...but it was working perfectly before but now it takes me to the command line when i choose to boot ubuntu :(

---

### Post by Rimdeker on 2009-12-06
I have the exact same problem. After UNR (Ubuntu Netbook Remix) updated I could not boot Ubuntu as usual, anymore. I get some kinda command line. Apparantly several people have that problem ever since they updated their Ubuntu in the past 36-ish hours.

[http://ubuntuforums.org/showthread.php?t=1347109](http://ubuntuforums.org/showthread.php?t=1347109)
This is the thread I created yesterday. Also two friends of mine have the same problem.

I couldn't find a way to fix it so I had to delete Ubuntu and well... 
I do not intend to re-install it for a while, would suck if I did the update again and then have the exact same problem.

---

### Post by w_1_n_d on 2009-12-06
ya it looks grub> and above it, it  talks about pressing tab and to get a list of options and etc....but i wana know how to get back the other one....where u just select what u want

---

### Post by w_1_n_d on 2009-12-06
rimdeker thats right i did update ubuntu yesterday and it asked for a restart but i didn't restart it untill now :O

---

### Post by ibuclaw on 2009-12-06
> **w_1_n_d said:**
> ya it looks grub> and above it, it  talks about pressing tab and to get a list of options and etc....but i wana know how to get back the other one....where u just select what u want

type into it:
```
find /boot/grub/stage1
```
And you be given a *(hdX,Y)* value.

type in:
```
root (hd**X**,**Y**)
```
Replacing 'X' and 'Y' with the numbers you were given from the find command.

then type in:
```
setup (hd0)
```
and GRUB will be installed on your system again.

Lastly
```
reboot
```
To reboot.

If problems persist - the chances may be that your grub menu has been removed for some unforseen reason.

Regards
Iain

---

### Post by w_1_n_d on 2009-12-06
> **tinivole said:**
> type into it:
```
find /boot/grub/stage1
```And you be given a *(hdX,Y)* value.

type in:
```
root (hd**X**,**Y**)
```Replacing 'X' and 'Y' with the numbers you were given from the find command.

then type in:
```
setup (hd0)
```and GRUB will be installed on your system again.

Lastly
```
reboot
```To reboot.

If problems persist - the chances may be that your grub menu has been removed for some unforseen reason.

Regards
Iain


thanks for getting back to me but unfortunatly it did not work....to begin with it turns out the command prompt didnt look like this grub> it actually looks like this sh:grub> i tried the following commands but it did not work....if u have any solutions i would really appreciate them :):KS

---

### Post by ibuclaw on 2009-12-06
> **w_1_n_d said:**
> thanks for getting back to me but unfortunatly it did not work....to begin with it turns out the command prompt didnt look like this grub> it actually looks like this sh:grub> i tried the following commands but it did not work....if u have any solutions i would really appreciate them :):KS

Hmm, I probably can't help further - as it seems you are using Wubi, and my knowledge of that is limited.

There are success stories of your such issue here though: [http://ubuntuforums.org/showthread.php?t=1339203](http://ubuntuforums.org/showthread.php?t=1339203)

The post that you will want to point your interest in is this one: [http://ubuntuforums.org/showpost.php?p=8444565&postcount=10](http://ubuntuforums.org/showpost.php?p=8444565&postcount=10)

Regards
Iain

---


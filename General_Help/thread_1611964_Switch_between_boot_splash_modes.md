---
title: "Switch between boot splash modes"
date: 2010-11-02
forum: General Help
---

### Post by tamerucar on 2010-11-02
Hi,

I'm using Ubuntu 10.10. How can I switch between text-based splash and GUI splash? My computer is currently showing a purple text based splash screen when booting Ubuntu. How can I switch it to GUI mode?

Thanks in advance...

---

### Post by tamerucar on 2010-11-03
Any idea?

---

### Post by Deepak Jindal on 2010-11-03
Plymouth is responsible for graphics at boot time ( after grub starts ). simple type this in terminal 

```
sudo update-alternatives --config default.plymouth 
```

then choose from the list which theme you want to use as your splash screen, then this to make it permanent. 

```
sudo update-initramfs -u 
```

reboot and you will have your new splash screen.

---

### Post by tamerucar on 2010-11-03
Firstly, thanks for your reply.

```
sudo update-alternatives --config default.plymouth 
```

But when I type this code I get the following message:

[I][B]There is only one alternative in link group default.plymouth: /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth
Nothing to configure.[/B][/I]

What does that mean?

---

### Post by tamerucar on 2010-11-03
I realized that the problem is related with Nvidia drivers. So I made a little search about the topic and found the solution in the following post:

[http://ubuntuforums.org/showthread.php?p=9749207]("http://ubuntuforums.org/showthread.php?p=9749207")

---


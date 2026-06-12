---
title: "error occured in package manager"
date: 2011-04-15
forum: General Help
---

### Post by serj21 on 2011-04-15
hi everyone, i am new to linux, ubuntu, i dont know how to solve such error, now i cant even download anything. today morning when i just switched on the pc, i got this message:
[b][noparse]"(E:encountered a section with no package:header, E:problem with mergelist /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_mavarick-security_restricted_binery-i386,
E:the package lists or status file could not be parsed or opened.)'this usually means that your installed packages have unmet dependencies".[/noparse][/b]
somebody plzz help me.[-o<

---

### Post by plucky on 2011-04-16
> **serj21 said:**
> hi everyone, i am new to linux, ubuntu, i dont know how to solve such error, now i cant even download anything. today morning when i just switched on the pc, i got this message:
"[B](E:encountered a section with no package:header, E:problem with mergelist /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_mavarick-security_restricted_binery-i386,
E:the package lists or status file could not be parsed or opened.)'this usually means that your installed packages have unmet dependencies[/B]".
somebody plzz help me.[-o<

For a start Mavarick is spelt incorrectly should be maverick.Did you copy and paste or did you type it in manually?

Open a terminal and ```
cd /var/lib/apt/lists
ls
sudo rm *
sudo apt-get update
sudo apt-get upgrade
```

The sudo rm * is a dangerous command so I put in the ls command to make sure you check you are in the correct directory.

It will also complain that you cannot delete the "partial" directory.Don't bother about that.

The sudo apt-get update will reload the list files. and the sudo apt-get upgrade will install any updates it finds.

Good Luck

---

### Post by kiyop on 2011-04-16
I do not know if it is good to delete files in /var/lib/apt/lists.

> **plucky said:**
> 
Open a terminal and ```
cd /var/lib/apt/lists
ls
sudo rm *
sudo apt-get update
sudo apt-get upgrade
```The sudo rm * is a dangerous command so I put in the ls command to make sure you check you are in the correct directory.
 
It is very dangerous, if somebody mistypes "/var/lib/apt/lists", "cd" command fails, he cannot understand what should be the output of "ls", and he executes "sudo rm *".

Thus, the following may be better:
```
sudo rm /var/lib/apt/lists/*[FONT=monospace]
[/FONT]sudo apt-get update[FONT=monospace]
[/FONT]sudo apt-get upgrade
```

---

### Post by serj21 on 2011-04-16
This is the message I am getting in the terminal. I did as per what plucky said and i got the following message:
**rm: cannot remove `/var/lib/apt/lists/partial': Is a directory**

---

### Post by serj21 on 2011-04-16
i am very sorry, not plucky, i did as per _[U]kiyop _
[/U]

---

### Post by serj21 on 2011-04-16
you guys rock!:guitar:
I am able to open synaptic package manager now, i followed kiyop's step, it gave an error, then I typed sudo apt-get update and it worked

---

### Post by serj21 on 2011-04-16
My problem was solved because of u guys. thanks a ton!!!

---

### Post by kiyop on 2011-04-16
> **serj21 said:**
> This is the message I am getting in the terminal. I did as per what plucky said and i got the following message:
**rm: cannot remove `/var/lib/apt/lists/partial': Is a directory**
This is expected error message, because "rm" (without "-r" option) cannot delete any directory.
The above error message shows that plucky's way is effective.

I only modified commands in order to decrease the probability of accident, without changing the effect.

---


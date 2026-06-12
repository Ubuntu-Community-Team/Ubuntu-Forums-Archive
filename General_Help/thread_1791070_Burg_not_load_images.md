---
title: "Burg not load images"
date: 2011-06-26
forum: General Help
---

### Post by Yeyo53 on 2011-06-26
Hello, at first sorry for my english.

I'm having problems with BURG. I installed it and it's working but he only show text. I'm using "ubuntu" theme.

If I run "sudo burg-emu", it look fine but then in boot, not. It's running in graphical mode because if I press 'f8' it changes to text-mode.

I have tried to change resolution without results.

Thanks.

---

### Post by nzjethro on 2011-06-26
Hi yeyo, and welcome to the forums. I had a similar problem, my Burg configuration was last, and I had a text grub instead my GUI Burg, even though burg-emu was showing it as it should. My solution was to reinstall Burg, it only takes a few minutes, and it solved the problem for me. Run:

```
sudo burg-install /dev/sdXX
```

Where sdXX is your HDD where Ubuntu is installed (e.g. I would run **sudo burg-install /dev/sda**.

---

### Post by Yeyo53 on 2011-06-26
Not solved.

I see the orange letters from ubuntu's theme and I can change the theme but anyone show images. Only ugly text. For example sora_extended only shows 1 line of white letters.

I have an "old" laptop with Intel 855GM graphics and Pentium M 1.7Ghz and I'm using Ubuntu 10.10.

---

### Post by Yeyo53 on 2011-06-26
Nobody with this problem?

---


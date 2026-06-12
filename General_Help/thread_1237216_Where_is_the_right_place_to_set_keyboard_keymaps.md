---
title: "Where is the right place to set keyboard keymaps?"
date: 2009-08-11
forum: General Help
---

### Post by yogg on 2009-08-11
Hi

I have created my own live CD with special software (from scratch -> debootstrap). Now I have the problem that when I boot the live CD the System loads the wrong keymap.

The right keymaps are already downloaded in the chroot environment:
```

aptitude install -y console-keymaps

```I can also load them in the tty:
```

sudo loadkeys /usr/share/keymaps/i386/azerty/be-latin1.kmap.gz

```But this does not work for xorg (I use IceWM), so I have to set them on a second way:
```

startx
# open console
setxkbmap -rules xorg -model pc104 -layout be

```This is not realy comfortable, so I'm searching for a single point where I can change the keymap for the whole system (tty, xorg, ...). Is there a config file or somthing else that I can change? Best would be if I can change it in the chroot environment when I create the live CD ;)

---

### Post by yogg on 2009-08-13
Does nobody know this, or is this so hard?

This is the second time I ask in a Forum where I can change the keyboard setting permanently for the whole System. Google does not give me the right answers :(

---


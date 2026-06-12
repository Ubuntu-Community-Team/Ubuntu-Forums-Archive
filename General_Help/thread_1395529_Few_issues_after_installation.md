---
title: "Few issues after installation"
date: 2010-02-01
forum: General Help
---

### Post by quag on 2010-02-01
I just installed Ubuntu 9.10 from wubi. I am dual booting with Windows XP.

Installation and everything went fine until it got to updating packages the first time Ubuntu was ran. It asked for a computer restart and I let it restart.

Now whenever I boot up Ubuntu, I get stuck at the grub screen, and have to type in
```

set root=(loop0)
linux /vmlinuz root=/dev/sda1 loop=/ubuntu/disks/root.disk ro
initrd /initrd.img
boot

```to get Ubuntu to boot now. It wasn't like that previously, it's sort of annoying to have to type this in every time I want to run Ubuntu. Upon login after this restart, I find out that my laptop's keyboard and touchpad no longer work anymore (they worked on the grub screen; typing all of this now with USB keyboard & mouse). Also, now suspend/restart/shutdown (don't know about hibernate) no longer function properly. It puts the computer in a sleep and wont "wake up" unless I remove the battery and unplug the power then press the power button again.

All of these functions worked properly when Ubuntu was booted for the first time; how can I fix these issues?

The laptop is an Alienware M5500 with 1gb of ram. Let me know what other information you need as I cannot think of what all would be required. I'm new to Ubuntu and sort of new to the linux environment, so keep that in mind.

Thanks!!



EDIT: Nevermind, a friend just came online and helped me solve problem. All I had to do was reinstall grub. Man, I thought I was going to have to mess with a lot of stuff to get these problems fixed, guess not lol.

---


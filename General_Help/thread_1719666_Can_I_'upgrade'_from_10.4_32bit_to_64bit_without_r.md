---
title: "Can I 'upgrade' from 10.4 32bit to 64bit without reinstall?"
date: 2011-04-02
forum: General Help
---

### Post by Razmear on 2011-04-02
Title pretty much say it all.

---

### Post by Elfy on 2011-04-02
Not that I know of.

---

### Post by Vaphell on 2011-04-02
if you had separate /home partition, such upgrade via reinstall would be a breeze. System partition is overwritten with 64bit versions of everything in 15 minutes and your personal data happily stays where you left it

---

### Post by Razmear on 2011-04-02
> **Vaphell said:**
> if you had separate /home partition, such upgrade via reinstall would be a breeze. System partition is overwritten with 64bit versions of everything in 15 minutes and your personal data happily stays where you left it

Thanks for the tip, currently I don't have a seperate /home partition, but will look into how to do so, and if not then I'll know to make one when I reinstall in case I want to go back.

edit: found tutorial on create home partition after install:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Vaphell on 2011-04-02
creating during installation is easy, but it's possible to create one for existing configuration. It's more complicated, most likely includes partition resize+repartitioning which always is somewhat risky - backup of valuable data is highly recomended (it's recommended either way, having only 1 copy of precious stuff is a road to disaster in case of brainlessness, hardware failure or software bug), also modification of configuration files is required so system knows about new location of user files.
If you can't be bothered to get your hands dirty wait for good opportunity to do full reinstall.

Separate /home is very useful when you like to tinker with system. When you break it, often it's easier to reinstall system files than to fix it. Your data is safe so you are up and running in 15 minutes.
Some people have even better configuration. They put their data on yet another partition that can be linked from different linux installations (some ppl like to test stuff) because using 1 /home for all distros is bound to fail (in a non-critical way) - configs files would get overwritten when going from distro to distro. So people do
- system1+small /home for configuration files
- system2+small /home for configuration files
...
...
- DATA partition where all goodies are located

---


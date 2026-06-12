---
title: "Optimisations"
date: 2010-11-21
forum: General Help
---

### Post by nnn= on 2010-11-21
I'm looking to optimise the performance of my pc. There are various recommendations on what is best, so I thought to ask what would be a good idea in your opinion. I can provide system specifics, if you give me the commands which can poll those characteristics.

---

### Post by Finalfantasykid on 2010-11-21
See if you can disable some of your system services, and start up programs.

If you value performance, then disabling Compiz will go a long way.

If you computer has lots of ram, then you can try lowering the swappiness.  This will lower the tendency to move things in memory over to the swap, speeding up certain things like switching between programs.  This may sound better than it actually is, and you will probably only notice a difference if you are actually using a significant amount of memory in the first place.  You can achieve this by executing this command:

```

sudo echo XX > /proc/sys/vm/swappiness

```^ This one I think changes it temporarily until your next boot.  To make the change permanent add vm.swappiness=XX to:

```

gksu gedit /etc/sysctl.conf

```XX being a number between 0 - 100.

The lower the number, the less swapping.  I think with a swappiness of 0, it wont start swapping until you have used 100% of your memory, so I wouldn't recommend going this low since if you do hit that point, then your system will probably start to crawl instantly.  I like setting it to 10.  The default is 60 incase you wanted it back to how it was before.  If you you don't have very much memory in your computer, then I wouldn't play around with this setting, as swapping can be pretty important for those types of systems.

Thats all I can think of right now.

---

### Post by cascade9 on 2010-11-21
A minimal install then adding gnome, xfce or lxde can help a fair bit. 

I dont know if you'd want to reinstall though.

---

### Post by Artemis3 on 2010-11-21
edit /etc/fstab to use the noatime mount option (instead or relatime/defaults). Ubuntu should seriously default to this.

---


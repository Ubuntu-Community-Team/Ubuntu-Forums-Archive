---
title: "How to run command on start up?"
date: 2011-02-08
forum: General Help
---

### Post by samuelv89 on 2011-02-08
I'm running Ubuntu 10.10, on virtual box from my mac, and in order to normally access my files on my mac I run this command on the terminal:
> sudo mount -t vboxsf users /mnt/users

 (...which mounts my mac "users" folder (that I've previously shared to the Virtual Machine) on the specified folder: "/mnt/users")
...obviously, it ask my password, & then, *voilà*, it works fine...

What I'm trying to do is to run the command on start up.

I've kind of tried  with "System>Preferences>Startup Applications"...  but with no success (basically cause I'm a newbie...) & I've tried reading other threads 'bout it, but, again, can't achieve it...

...also have tried adding the command to the "rc.local" file at "/etc", but it appears I'm making things wrong... so... help! :p

Thanks in advance!!

(appreciate absolute-beginner talk)

---

### Post by aeiah on 2011-02-08
adding to /etc/rc.local before the exit command would be the right way to do this, but in a normal ubuntu install, perhaps you'd need to do something else so ubuntu executes /etc/rc.local

btw, rc.local is ran as root, so you wouldnt need sudo in there.

but really, you should be adding your mount to your fstab file (which controls what is mounted by default). see here: [http://rotwhiler.wordpress.com/2008/10/09/mount-virtualbox-shared-folders-automatically-using-fstab/](http://rotwhiler.wordpress.com/2008/10/09/mount-virtualbox-shared-folders-automatically-using-fstab/)

---

### Post by samuelv89 on 2011-02-08
Thanks aeiah,

I've tried now, adding it to the "fstab" file,
here is a snapshot of how the "fstab" was before restart:

[IMG]https://lh3.googleusercontent.com/_MYbSJt3vF0A/TVF5q8sGVrI/AAAAAAAAARo/7Nu84_3MBVk/s1024/Captura%20de%20pantalla%202011-02-08%20a%20las%2011.05.04.png[/IMG]

it still doesn't work... any ideas?

---


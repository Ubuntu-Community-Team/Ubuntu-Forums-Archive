---
title: "Nvidia driver messed up"
date: 2011-07-27
forum: General Help
---

### Post by Steam. on 2011-07-27
I tried installing it via ctrl alt F1, i managed somehow to install it,i needed to because the old one was conflicting with my card(8800 Ultra), and this showed up when i typed in startx.

Using ubuntu 11.04

[IMG]http://www.imagelodge.net/imgs/xlr8/P10102843yc.jpg

---

### Post by Wayne_V on 2011-07-27
How did you install the first version and then how did you install the second version?

---

### Post by Steam. on 2011-07-27
One with additional drivers thing and the other one via command line.

---

### Post by Wayne_V on 2011-07-27
won't work.  you'll need to uninstall the cmd line version (nvidia-installer --uninstall).   Then uninstall the ubuntu supplied drivers (see dpkg --list | grep -i nvidia).   Then make sure everything is working with the open source nv driver before you try to install the proprietary nvidia drivers again (either via the hardware drivers app -OR- the nvidia supplied cmdline util).

---

### Post by realzippy on 2011-07-27
If you need the newest nvidia-driver,best thing is to add
[xswat ppa]("https://launchpad.net/~ubuntu-x-swat") to your sources,which upgrades the available nvidia-current to the newest version.(i.e. 280.xx in the moment)
So you not need to install manually and do not have to care each kernel update.

---

### Post by Steam. on 2011-07-28
Thank you Wayne for showing me how to remove the driver, and you zippy for the ppa, it is annoying to go to a command line each time to install it.But i didn't uninstall the ubuntu supplied drivers, i thought i was supposed to just delete the new ones i installed then, so i just typed that grep thing and saw the old 270.xx driver that was in, rebooted.added PPA, installed driver, and it worked.Thanks again.

---

### Post by realzippy on 2011-07-28
Fine.So you can set thread as solved?

---

### Post by Steam. on 2011-07-28
Oh right, sure.

EDIT: can't, no prefix option in advanced edit.Mods/admins set to solved please.

---

### Post by realzippy on 2011-07-28
:-)

---

### Post by Steam. on 2011-07-28
Hold it, i messed up another system with this :D

Quadro FX 3400/4400 drivers.Erased drivers completely, trying to stop gdm but when i enter sudo /etc/init.d/gdm stop, it gives me something liek rather invoking etc BUT DOESNT STOP IT.going in to install drivers, typing in sudo./nvidia.run(i renamed it nvidia), it gives out doesn't exist.

---

### Post by Steam. on 2011-07-28
anyone?

---

### Post by realzippy on 2011-07-29
> **Steam. said:**
> Hold it, i messed up another system with this :D

Quadro FX 3400/4400 drivers.Erased drivers completely, trying to stop gdm but when i enter sudo /etc/init.d/gdm stop, it gives me something liek rather invoking etc BUT DOESNT STOP IT.going in to install drivers, typing in sudo./nvidia.run(i renamed it nvidia), it gives out doesn't exist.

Which ubuntu,which nvidia driver?

---

### Post by Steam. on 2011-07-29
11.04, one from nvidia site.Did the same thing as i did with before(uninstalled the additional hardware driver, rebooted, then tried installing the new one.

---

### Post by realzippy on 2011-07-29
Why don't you just use xswat ppa ?
Why installing manually?

---

### Post by zero244 on 2011-07-29
> **Steam. said:**
> Hold it, i messed up another system with this :D

Quadro FX 3400/4400 drivers.Erased drivers completely, trying to stop gdm but when i enter sudo /etc/init.d/gdm stop, it gives me something liek rather invoking etc BUT DOESNT STOP IT.going in to install drivers, typing in sudo./nvidia.run(i renamed it nvidia), it gives out doesn't exist.

1. Make sure you are in the directory where the file is.
2. I believe you have to put a sudo sh in front of the file to you want to launch.
3. The Nvidia .run files are case sensitive.
4. To uninstall one of these you would put sudo sh nvidia.run --uninstall
5. When making these commands if your not in the directory where the file is you have to point to its location to run it.
6. I think your going to have to be in a root terminal outside of Gnome to install this file.
7. Next time you boot select the failsafe version of your kernel and go to Root terminal from the menu.

---

### Post by Steam. on 2011-07-29
I did go there, from recovery mode, root terminal, still said rather than invoking thingy.

---

### Post by Steam. on 2011-07-30
Replaced driver via dpkg in recovery mode.But now I can't get past the boot screen with 5 dots, they are lit up orange which means it's loaded, but it wont move past that.

---

### Post by zero244 on 2011-07-30
Hello: Have you tried booting using the failsafe mode drivers.?
You may want to remove your current drivers and purge all your nvidia stuff and start over.
I put a xswat ppa in my sources which allows me to install them from synaptic.
I am running the latest 275 drivers.
I would first make sure you can boot with the nv video drivers from the failsafe mode menu.
If those dont load then you will have to do your repairs from the very black unfriendly last resort terminal screen.

---


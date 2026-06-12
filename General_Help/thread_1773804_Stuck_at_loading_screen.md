---
title: "Stuck at loading screen"
date: 2011-06-02
forum: General Help
---

### Post by ibrabeicker on 2011-06-02
With today's update gdm failed to update for some reason, after that I couldn't launch any program so I rebooted

Now Ubuntu is stuck at the purple loading screen but the mouse works. I tried going to tty and reinstall xorg and gdm with

apt-get --reinstall install xorg gdm

but the adress to xorg fails to be resolved. I tried loggin in recovery mode with failsafeX to reconfigure video settings but the failsafeX fails (o O) and go immediatly back to the same menu to chose from "resume", "failsafe x", "root terminal" etc


need help

---

### Post by ibrabeicker on 2011-06-02
ok I managed to log in with kde, but now every program that uses gtk or gnome, like firefox, chrome, libreoffice, is not loading

example when trying to run firefox

/usr/lib/firefox-4.0.1/firefox-bin: symbol lookup error: /usr/lib/firefox-4.0.1/libxul.so: undefined symbol: gdk_x11_window_get_drawable_impl

---

### Post by ubudog on 2011-06-02
Open a terminal and try installing ubuntu-desktop.

```
sudo apt-get install ubuntu-desktop
```

---

### Post by ibrabeicker on 2011-06-02
> **ubudog said:**
> Open a terminal and try installing ubuntu-desktop.

```
sudo apt-get install ubuntu-desktop
```

it downloaded about 17 Kb 

still not working

---

### Post by ubudog on 2011-06-02
Did you try logging out and changing the session selection to "GNOME" or "Ubuntu Classic"?

---

### Post by ibrabeicker on 2011-06-02
> **ubudog said:**
> Did you try logging out and changing the session selection to "GNOME" or "Ubuntu Classic"?


I dont have a GNOME session on my menu, but i tried "ubuntu" "ubuntu(safety mode)" "ubuntu classic" "ubuntu classic (no effects)" but neither work

---

### Post by ubudog on 2011-06-02
Hmm... only way I can think to fix this is by going back a kernel.  You can do this, but you have to modify grub to show you the menu.  I recommend installing grub-customizer from here: [https://launchpad.net/grub-customizer](https://launchpad.net/grub-customizer)

Just add the ppa to your software sources, then:
```
sudo apt-get install grub-customizer
```

After you have that installed, start it up (Applications>System Tools>Grub Customizer), and click on Preferences.  Under visibility, check "Show Menu".  You may also want to raise the timeout.  Now, after that is all set, reboot, and after your BIOS message, you should see GRUB.  Use the arrow keys to select the previous kernel (the one you were using before updating).  Then it should start up problem free.  I hope that works for you, let me know.  :-)

---

### Post by ibrabeicker on 2011-06-02
the older kernels are all broken too...


I think it's time for a fresh install


Thanks for the help anyway

---

### Post by ubudog on 2011-06-02
Hmm, that sucks.  :-(

If you're gonna do a reinstall, I suggest 10.04.  It will be supported for a while longer, and it's super stable.

---


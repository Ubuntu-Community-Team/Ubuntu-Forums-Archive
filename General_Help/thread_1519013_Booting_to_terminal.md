---
title: "Booting to terminal"
date: 2010-06-27
forum: General Help
---

### Post by rensell on 2010-06-27
I'm looking for a way to add a menu entry into grub 2 that boots my computer but does not load the GUI, I want it to run the startup scripts and appear at the terminal login screen. I can't seem to get anything that I have found using google to work. It seems that it should be something simple to add to a grub file that shows "Ubuntu, Terminal" on the grub2 menu during system boot that then proceeds to boot ubuntu but does not load any GUI "stuff".

The more I'm using Linux, the more it appears that the simplest of things have been overlooked during development. For example, the boot up (Grub2) stuff depends on multiple files. My windows server(s) I simply edit boot.ini and I'm done, I add a couple letters and I get no GUI at startup, but Linux is a different story. I have to spend days trying "solutions" I find online and none work. Sorry to ramble, I'm just getting frustrated with such simple task that feel nearly impossible to accomplish.

To reiterate, I'd like to know if I can add an entry to my grub2 menu that boots my xubuntu to a terminal login.

TYIA,
Ray

---

### Post by rcayea on 2010-06-27
I think maybe removing the login manager may send you directly to terminal prompt.

---

### Post by stderr on 2010-06-27
NB: You'll probably need to replace gdm with xdm hereafter for Xubuntu.

When your system boots you can naturally just switch to a console TTY with Ctrl+Alt+F1..F6. To complete the effect, you can stop gdb with something like:

```
sudo service gdm stop
``` 

I think if you remove gdm from the startup apps, that'll do the trick for you. Something like this should work:

```
sudo update-rc.d -f gdm remove
```

When you boot up and it hits terminal, you can start an X session with

```
startx
```

Restore the graphical login with:

```
sudo update-rc.d gdm defaults
```

Alternatively, I think if you manually create an /etc/inittab file and configure it to your needs, then Ubuntu will respect the init level you give it.

---

### Post by Jose Catre-Vandis on 2010-06-27
Just press CTRL+ALT+F2 once you have booted up to login prompt.

If you don't want X running then login to your shell and type:
```
sudo /etc/init.d/gdm stop
```
or
```
sudo service gdm stop
```
depending upon which version you are running

---

### Post by rensell on 2010-06-27
st, I've tried those commands using both gdm and xdm. Stopping xdm gives an error saying unknown service, I believe xubuntu still uses gdm - but may be incorrect. However, those commands do not work, I've tried those (found them using google) before posting but to no avail.

I'm shocked that it is such a pain to do such a simple task, I have the same issue when I attempt to boot without a monitor connected. I never would of thought either of these things would cause such a problem.

---

### Post by rensell on 2010-06-27
bump for night time help...

---

### Post by rensell on 2010-06-29
I'm hoping someone online tonight may be of some help, I've finally found some time today to get back to this issue.

I've ctr+alt+f1 and log in and run ```
sudo update-rc.d -f gdm remove
``` and it runs and removes gdm. When I reboot it still loads into the GUI. Now when I ctr+alt+f1 and login and run```
sudo update-rc.d -f gdm remove
``` if says "Removing any system startup links for /etc/init.d/gdm... and is ready for my input, basically saying there are not links.

So, I'm puzzled as to why it continues going to the GUI on startup!

Thanks so much for any help.

---

### Post by oldfred on 2010-06-30
Is not what you want what recovery mode is?

Recovery mode just replaces quiet splash with single  so then you boot to single user mode without the gui.

---

### Post by Serpher on 2010-06-30
Debian distros have their runlevels configured half assed IMO. It's easy to do this on something like Fedora as all the run levels are pre-configured, but with Ubuntu youre going to have to learn how to use chkconfig.

```
sudo -i
apt-get install chkconfig
chkconfig --level 4 xdm off
vi /etc/inittab
logout
```

Change the default runlevel to 4. Ubuntu does this differently than Fedora I think but if not it's just the questionable number at the bottom. This doesn't add an entry in grub, but you can switch between these modes using 'sudo init 5' for GUI mode and 'sudo init 4' for TUI mode. If you don't change your default runlevel, you can still use those 2 commands, you'll just have a GUI on startup.

I personally start in a TUI and use 'startx' to start my GUI with no graphical login. Keeps things save in case my GUI messes up, I can still boot without messing around with GRUB settings or booting from a live disc to fix things.

---

### Post by rensell on 2010-06-30
finally found something to work. I'm not sure why ```
sudo update-rc.d -f gdm remove
``` that doesn't actually keep the GUI from loading. But, I finally found a command for grub the will work for me, edit /etc/default/grub and for GRUB_CMDLINE_LINUX_DEFAULT put text and it will boot to a terminal login and allow startX after login. Hope this will help someone else sometime. Thanks everyone for your input.

-RAY

---


---
title: "Boot to tty1/terminal?"
date: 2010-06-01
forum: General Help
---

### Post by dillandriskell on 2010-06-01
I've stopped using Ubuntu's graphical interface lately and instead stuck with
the terminals. So, since I don't plan on using the x11 for at least a month
I'd like Ubuntu to just boot straight to a tty, but I can't seem to figure out
how. I apologize if this is redundant, but everything I've found through prior 
research didn't work for me.

One source told me to change the name of /etc/rc2.d/S13gdm so Ubuntu wouldn't 
recognize it, but that file doesn't exist on my machine. Another told me the
command "sudo update-rc.d -f gdm remove" would do the trick, and although it
seemed to work judging by the code, when I rebooted it still went to the
graphical log in screen.

So does anybody know the current way to change Ubuntu's default log in to a 
terminal on Ubuntu 10.4? And how to change it back? Any help would be much 
appreciated.

---

### Post by Jeroensum on 2010-06-03
I believe just renaming the .conf file should do the trick.

```
mv /etc/init/gdm.conf /etc/init/gdm.conf.noexec
```

---

### Post by Serpher on 2010-06-03
Easier way to do this, I wouldn't bother with all this manually unless you really know about how init works. Running the following commands will do it much safer and save you a lot of headache in the future.

```
sudo apt-get install chkconfig
sudo chkconfig --level 2345 gdm off
```

When you want to have it run during startup, run this:

```
sudo chkconfig --level 2345 gdm on
```


Also if you want to turn it on or off while the system is running run:

```
sudo service gdm start
```

To turn it on or:

```
sudo service gdm stop
```

To turn it off. I know that works on Fedora, however if it doesn't work on Ubuntu:

```
sudo /etc/init.d/gdm [start/stop]
```

---

### Post by sisco311 on 2010-06-03
> **Jeroensum said:**
> I believe just renaming the .conf file should do the trick.

```
mv /etc/init/gdm.conf /etc/init/gdm.conf.noexec
```

this should work or boot with the **text** kernel parameter.

```
cat /etc/default/grub 
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="**text**"
GRUB_CMDLINE_LINUX=""
...

```

```
sudo update-grub
```

> **Serpher said:**
> Easier way to do this, I wouldn't bother with all this manually unless you really know about how init works. Running the following commands will do it much safer and save you a lot of headache in the future.

```
sudo apt-get install chkconfig
sudo chkconfig --level 2345 gdm off
```

This no longer works, since Karmic gdm's System-V style init script is replaced by an [Upstar]("http://upstart.ubuntu.com/") job.

---


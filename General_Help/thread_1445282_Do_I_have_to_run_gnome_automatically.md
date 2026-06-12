---
title: "Do I have to run gnome automatically?"
date: 2010-04-02
forum: General Help
---

### Post by sparky-steve on 2010-04-02
Hiya,

I have ubuntu servers; I have ubuntu desktops. 

On one particular machine, I'd like both... I do not want gnome to start automatically; I want it to boot to command prompt, and once logged in, if I want gnome, I can start it (startx if I recall).

Gnome is already installed.

Any ideas how to turn it off by default, but be able to start it manually?

Cheers

SS

---

### Post by gemmakaru on 2010-04-02
Theres a little button on the bottom left of the log in screen, it has options including a terminal, try it.

---

### Post by sparky-steve on 2010-04-02
I'm well aware of that button; But it's not the fix I need.

I want to go direct to terminal, without gnome even thinking of starting.

Cheers
SS

---

### Post by sisco311 on 2010-04-02
Boot with the *text* kernel parameter. 

Change the value of GRUB_CMDLINE_LINUX_DEFAULT to text in the /etc/default/grub file:
```
...
GRUB_CMDLINE_LINUX_DEFAULT="text"
...

```
then run 
```
sudo update-grub
```

---

### Post by foldingstock on 2010-04-02
sparky-steve, when your computer boots hold the shift key down to access the grub menu. On the kernel line, at the very end, add the word "text" and then press ctrl+x to boot the system. You should boot into a console. At this point, if you want to start gdm, run "sudo gdm." 

If you like this and want to do it permanently, edit the file '/etc/default/grub' and change the line: ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
``` 

to:

```
GRUB_CMDLINE_LINUX_DEFAULT="text"
```

Once you have done this, save and close the file. Now run:

```
sudo update-grub
```

Reboot and you will boot into a console.

---

### Post by sparky-steve on 2010-04-02
Thanks people... I'll try this out in a while.

SS

---

### Post by Zukero on 2010-04-02
Another solution would be to edit the links present in /etc/rc*.d/ to remove the ones named SXXgdm (XX being a number between 00 and 99 usually). This should remove GDM from the startup list.

---

### Post by sisco311 on 2010-04-02
> **Zukero said:**
> Another solution would be to edit the links present in /etc/rc*.d/ to remove the ones named SXXgdm (XX being a number between 00 and 99 usually). This should remove GDM from the startup list.

That no longer works. Since 9.10 GDM is started by an Upstart job (/etc/init/gdm.conf).

[http://upstart.ubuntu.com/getting-started.html](http://upstart.ubuntu.com/getting-started.html)

---

### Post by Zukero on 2010-04-02
Ooops.... I forgot that...
Been playing with too many different Unixes these days.

---

### Post by haddog on 2010-04-02
> **foldingstock said:**
> sparky-steve, when your computer boots hold the shift key down to access the grub menu. On the kernel line, at the very end, add the word "text" and then press ctrl+x to boot the system. You should boot into a console. At this point, if you want to start gdm, run "sudo gdm." 

If you like this and want to do it permanently, edit the file '/etc/default/grub' and change the line: ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
``` 

to:

```
GRUB_CMDLINE_LINUX_DEFAULT="text"
```

Once you have done this, save and close the file. Now run:

```
sudo update-grub
```

Reboot and you will boot into a console.

Nice howto!

---

### Post by egalvan on 2010-04-02
> **gemmakaru said:**
> Theres a little button on the bottom left of the log in screen, it has options including a terminal, try it.

> **sparky-steve said:**
> I'm well aware of that button; But it's not the fix I need.

I want to go direct to terminal, without gnome even thinking of starting.

On Hardy, using that option button would allow one to choose the session type...
then you could choose "just this time" or "make default"...

pick terminal session, then "make default", will give terminal boot as default.

May not work this way in newer 'buntu's, tho...

Lucid, where are you?

---

### Post by sparky-steve on 2010-04-03
Hi Guys

I dont appear to have a /etc/default/grub

I should have made it clear that this particular server is 9.04 - is dawns on me that people may assume i'm talking about 9.10, given my tagline below :/

Cheers
SS

---

### Post by sisco311 on 2010-04-03
> **sparky-steve said:**
> Hi Guys

I dont appear to have a /etc/default/grub

I should have made it clear that this particular server is 9.04 - is dawns on me that people may assume i'm talking about 9.10, given my tagline below :/

Cheers
SS


Then edit the grub menu entry's *kernel* line in /boot/grub/menu.lst file & replace *quiet splash* with *text*:

```
title Linux
root   (hd0,1)
*kernel* /boot/vmlinuz26 root=/dev/sda2 ro **text**
initrd /boot/kernel26.img

```

Or remove gdm from the init scripts:
```
sudo update-rc.d -f gdm remove
```
To (re-)enable gdm, run:
```
sudo update-rc.d -f gdm defaults
```

---

### Post by sparky-steve on 2010-04-03
Thanks for all your help and pointers.

in the end, I edited /boot/grub/menu.lst manually to boot in text mode (I dont like the splash "hiding" everything... I've been on *nix for too long to like the splash)

I then issued

```
update-rc.d -f gdm remove
```

and that stopped gnome from starting automatically.

Now, I log in as me, and 

```
startx
```

will start a gnome session if/when I need to.  

```
sudo gdm
```

will get you back (until next reboot) with the login manager, but in my case that's not what I wanted.

As of now, it's working exactly as I want it - thanks....

:KS

---

### Post by sisco311 on 2010-04-03
> **sparky-steve said:**
> 

As of now, it's working exactly as I want it - thanks....

:KS

You're welcome!

Please mark this thread as [SOLVED], at the top of the page, click the "[COLOR="Red"]Thread Tools[/COLOR]" Menu and then "Mark this thread as Solved".

Thanks.

---


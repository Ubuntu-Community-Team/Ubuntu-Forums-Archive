---
title: "Ubuntu 10.10 Nvidia driver configuration problem"
date: 2010-10-11
forum: General Help
---

### Post by davidvandoren on 2010-10-11
Hi there
Can someone help me out with the Nvidia driver configuration.
I installed the Nvidia driver via the **additional driver tool **
When I run ```
sudo nvidia-xconfig
```

I get this ```
Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Undefined Device "(null)" referenced by Screen "Default
                  Screen".

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

```

Does anyone know how to fix this?

Thanks

---

### Post by davidvandoren on 2010-10-11
Ok I fixed it already.

For anyone else who might have the same problem.

Use this in the terminal.
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by TeoBigusGeekus on 2010-10-11
Try this
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by davidvandoren on 2010-10-11
We  must have posted at the same time.

Thanks but I found a solution already. The command above worked perfectly.

I don't know what the difference would have been though.

---

### Post by TeoBigusGeekus on 2010-10-11
> **davidvandoren said:**
> We  must have posted at the same time.

Thanks but I found a solution already. The command above worked perfectly.

I don't know what the difference would have been though.

[http://ubuntuforums.org/showthread.php?t=346138]("http://ubuntuforums.org/showthread.php?t=346138")

---

### Post by davidvandoren on 2010-10-11
Thanks that cleared everything up.

---

### Post by firefoxkatan on 2011-02-12
I have a question about this actually, so please forgive that I am posting in a [SOLVED] thread.

I installed Ubuntu 10.10 last night and fallowed the instructions on this website: [http://ubuntuguide.net/how-to-install-nvidia-graphics-driver-in-ubuntu-10-10-maverick-meerkat](http://ubuntuguide.net/how-to-install-nvidia-graphics-driver-in-ubuntu-10-10-maverick-meerkat) to update my Nvidia drivers. I fallowed the steps 1 & 2, and got this:

```
Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'
```then I restarted my computer, my GUI was gone and anytime I attempt to start it, I get a general "Error: no display specified". I attempted the fix mentioned:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```and I still have no GUI and am unable to get one started up. I have googled as much as I can and it has lead me here. Any help would be awesome.

---

### Post by chelusly on 2011-02-13
Remove:
  sudo rm /etc/X11/xorg.conf

Reboot (power off) or restart x.

I'm still having issues with my nvidia drivers as well. I recommend NOT running nvidia-xconfig or that will just screw stuff up. I'm still trying to find the solution but if anyone has any info suggestions I'm up for trying them.

---

### Post by jwcalla on 2011-02-13
I personally prefer to use the nvidia-settings program to define my "X Server Display Configuration".  There is a button there to "Save to X Configuration File".  Then I tweak the xorg.conf file as necessary.

Whenever I use the nvidia-xconfig command it just puts out poopy.

---

### Post by NSim on 2011-03-16
Hi,
this works for me
[http://www.rmic.be/ubuntu-maverick-nvidia-x-problem](http://www.rmic.be/ubuntu-maverick-nvidia-x-problem)

---


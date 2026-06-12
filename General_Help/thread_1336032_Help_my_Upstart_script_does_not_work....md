---
title: "Help: my Upstart script does not work..."
date: 2009-11-24
forum: General Help
---

### Post by bobmel on 2009-11-24
I need my Ubuntu9.10 installation to switch between two xorg.conf files during startup, depending on if if the OS runs directly on hardware or inside VMware Workstation (under Windows 7). 

I've tried to achieve this using a script for Upstart. It basically looks for the string "VMware" in the result from 'lspci' and if found soft links "xorg.conf" to "xorg.conf.AfterVMwareToolsInstall". Otherwise it soft links "xorg.conf" to "xorg.conf.BeforeVMwareToolsInstall". The script (named "choose.conf" and placed in "/etc/init") is shown below:

[FONT=Courier New]description    "Activate correct graphics driver for VMware"

start on (filesystem 
      and started hal)

console output
script
echo `lspci` | grep -q "VMware"  # check for "VMware" in some pci device
if [ $? -eq 0 ]
then
    echo "Changing to VMware xorg settings"
    if [ -f /etc/X11/xorg.conf ]; then rm /etc/X11/xorg.conf; fi
    ln -s /etc/X11/xorg.conf.AfterVMwareToolsInstall /etc/X11/xorg.conf
else
    echo "Changing to other xorg settings"
    if [ -f /etc/X11/xorg.conf ]; then rm /etc/X11/xorg.conf; fi
    ln -s /etc/X11/xorg.conf.BeforeVMwareToolsInstall /etc/X11/xorg.conf
fi
end script
[/FONT]
The problem is that it does not seem to work when Ubuntu runs directly on hardware. Then it does not remove the old xorg.conf and relink it to "xorg.conf.BeforeVMwareToolsInstall".
When Ubuntu runs inside VMware Workstation it works the way I want.

Anyone has any ideas what the problem can be? Or do you have other proposals how to achieve what I want?

Any help appreciated!

---

### Post by woll-e on 2009-11-24
Hi bobmel,

we both had a very similar problem, but luckily I just located the error.

First I have to mention that scripts in upstart will be executed by dash (and not bash) with the "-e" flag. This flag causes dash to exit immediately if the return value of a command is unequal zero.
But that is a big problem if you are using grep, because grep returns one if it doesn't find a match and therefor dash exits.

So after a little bit of searching the Internet I found this side which explains how to deal with that problem:
[http://www.davidpashley.com/articles/writing-robust-shell-scripts.html#id2746019]("http://www.davidpashley.com/articles/writing-robust-shell-scripts.html#id2746019")

Roundup:
It should solve your problem to change the line
```
echo `lspci` | grep -q "VMware"
```
to
```
echo `lspci` | grep -q "VMware" || true
```

I hope this will help you fix your problem

Regards
woll-e

---


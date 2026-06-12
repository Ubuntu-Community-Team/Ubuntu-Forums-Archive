---
title: "Knucklehead me deleted /var/lib by mistake"
date: 2010-08-25
forum: General Help
---

### Post by StretchyBill on 2010-08-25
Environment: Ubuntu 9.10 Karmic, 64 bit

I was doing some maintenance on the machine and tried to delete everything under /var/lib/hudson. By mistake, I deleted everything under /var/lib. ](*,)

I know, I know, I must have taken an extra dose of stupid pills.

Questions:

[LIST]
[*]Is there any way to recover without a full rebuild of the machine?
[*]Could I install Karmic to a VM, install all the same packages, and then copy over the /var/lib directory?
[*]Maybe a better question to start off is, which directories need attention (and what type) and which directories are not needed?
[/LIST]
Very soon before the delete, I did a directory listing in /var/lib. Here is what was in there:
acpi-support      
alsa              
apparmor         
apt               
aptitude          
apt-xapian-index  
aspell            
avahi-autoipd     
belocs            
binfmts
computer-janitor
dbus
defoma 
DeviceKit-disks 
DeviceKit-power 
dhcp3 
dictionaries-common 
doc-base
dpkg
exim4
gconf
gdm
hal
hp
hudson  (no problem here, I copied it before the delete)
initramfs-tools
initscripts
insserv
libuuid
locales
logrotate
misc
mlocate
NetworkManager
openoffice
os-prober
pam
pm-utils
polkit-1
pulseaudio
pycentral
python-support (no problem here, a symbolic link which I recreated)
samba
security
sgml-base
snmp
synaptic
ucf
update-manager
update-notifier
update-rc.d
urandom
ureadahead
vim
x11
xkb
xml-core

---

### Post by quixote on 2010-08-27
Does the system even come up?  Or have you not rebooted since deleting /var/lib?  If it'll run for you, you could try ```
dpkg --configure -a
```That should fix broken packages, and presumably without libraries, they're all broken (:() and that should pull those libraries back in.  ??

Just guessing.

---

### Post by StretchyBill on 2010-08-29
Thanks for the reply quixote.

I have not rebooted the machine. I dare not until I get all the data off of it, which is what I am doing right now.

I tried the dpkg command you suggested. It did not work, here is the result: "dpkg: cannot scan updates directory `/var/lib/dpkg/updates/': No such file or directory"

Once I get all the data off of it, I will reinstall Ubuntu and all my applications and data.

And I will have a much better appreciation of the dangers of rm -rf!  :rolleyes:

Thanks again for the help.

-Bill

---

### Post by quixote on 2010-08-29
Yeah, you're dealing with it the best way possible by not rebooting!  Very smart.  Even if rm -rf in the wrong place was less so :biggrin:  

Get the data backed up and reinstall is probably the best thing to do.  After that, I was thinking you could try booting from a LiveCD, copy its /var/lib/ to the empty one, and seeing what happens when you boot.  It probably won't be pretty, but since you'll be ready to reinstall anyway, it might be interesting to find out what will happen.  In the cause of science. :D

---

### Post by StretchyBill on 2010-08-31
Well, I am happy to have done something right. :P

Data is recovered, Ubuntu 10.04 has been installed and I am in the process of reinstalling other software. I installed Ubuntu before I read your thread below about copying /var/lib from a running LiveCD. That **would** have been an interesting experiment.

I am hoping I will never be in a position again to try that experiment!

Thanks for your help.

-Bill

---

### Post by quixote on 2010-08-31
> I am hoping I will never be in a position again to try that experiment!I've done some stuff where I know just how you feel. :biggrin:

Glad to hear the problem's behind you!

---


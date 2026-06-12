---
title: "Excule /media in disk space check?"
date: 2011-03-10
forum: General Help
---

### Post by tg3793 on 2011-03-10
I think I should have more than 56Gig of free space left. I used df -h to find this out. I also read that there are some situations where mounted drives might show in the disk space usage.

Is there any command line (or gui) that can be used to measure disk space usage 'excluding' the /media folder? I want to avoid unmounting the drives that I have mounted; too many files open.

If there in not an option I might have a to wait a few days. I don't like to reboot to lose my work and there isn't a "save current open tabs" or anything like that in Nautilus :-)

---

### Post by tg3793 on 2011-03-10
I read over the man page and thought I could try something like:

**sudo df -h /bin /boot /cdrom /dev /etc /home /lib /opt /proc /root /sbin /selinux /srv /sys /tmp /usr /var**

but it only gave me:

[COLOR="SeaGreen"]Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             453G  375G   56G  88% /
/dev/sda1             453G  375G   56G  88% /
/dev/sda1             453G  375G   56G  88% /
none                  970M  292K  970M   1% /dev
/dev/sda1             453G  375G   56G  88% /
/dev/sda1             453G  375G   56G  88% /
/dev/sda1             453G  375G   56G  88% /
/dev/sda1             453G  375G   56G  88% /
proc                     0     0     0   -  /proc
/dev/sda1             453G  375G   56G  88% /
/dev/sda1             453G  375G   56G  88% /
/dev/sda1             453G  375G   56G  88% /
/dev/sda1             453G  375G   56G  88% /
none                     0     0     0   -  /sys
/dev/sda1             453G  375G   56G  88% /
/dev/sda1             453G  375G   56G  88% /
/dev/sda1             453G  375G   56G  88% /[/COLOR]

---


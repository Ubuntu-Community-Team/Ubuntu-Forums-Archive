---
title: "ConsoleKit &amp; PolicyKit root privileges through certain programs"
date: 2012-06-29
forum: General Help
---

### Post by Lyfang on 2012-06-29
Hi, I'm trying out Debian Wheezy. I usually use Lubuntu 12.04 LTS but I wanted to see what Debian had to offer. I would like to give a ordinary user root privileges through certain programs, but don't don’t know how to permanently. I want NetworkManager Applet to get become a privileged process using ConsoleKit, PolicyKit & polkit. Does affect Ubuntu Minimal CD installations as well? Please consider that wrong settings can open new vulnerabilities, add new exploits & security issues.

NetworkManager cannot connect to the Internet
"Connection activation failed
(32) Not authorized to control networking."

PCManFM 0.9.10 file manager cannot mount USB flash drives
"Not Authorized"

NetworkManager 0.9.4.1 Network management & Debian 7 "Wheezy" (cat /etc/issue: Debian GNU/Linux wheezy/sid \n \l)

Step-by-step temporary workaround
1. Open Root-terminal & launch NetworkManager as root superuser: nm-applet, nm-connection-editor or pcmanfm
2. Use NetworkManager or PCManFM with escalated privileges

"Most Display Managers will take care of consolekit automatically" - [https://wiki.archlinux.org/index.php/NetworkManager#Command_line](https://wiki.archlinux.org/index.php/NetworkManager#Command_line)

See also: ConsoleKit, PolicyKit, polkit, ck-launch-session & dbus-launch

id -a
uid=1000(USERNAME) gid=1000(USERNAME) groups=1000(USERNAME),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),103(scanner)

What about adding the user USERNAME to the group netdev?

---

### Post by Lyfang on 2012-07-01
Can PAM (Pluggable Authentication Modules) be used to utilize root access/privileges? Where can I find display managers man  pages (documentation) of ConsoleKit support. Is it secure to run applications with the root password instead of the user's password? Can this compromising the security of the system? What about sandboxing applications with a sandboxed root? What about chroot, systrace,  jails or UML (User-mode Linux)? How can I easily control users restrictions?

---

### Post by Lyfang on 2012-07-05
[SOLVED] On Debian 7 "Wheezy" testing with LXDE
> **Lyfang said:**
> 
5. Network management
Open Root-terminal: apt-get install network-manager-gnome

leafpad /etc/X11/Xsession
Add line, save & reboot: exec ck-launch-session dbus-launch wm


---


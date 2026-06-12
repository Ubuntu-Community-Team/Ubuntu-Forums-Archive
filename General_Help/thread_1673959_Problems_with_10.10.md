---
title: "Problems with 10.10"
date: 2011-01-23
forum: General Help
---

### Post by dovael on 2011-01-23
Since installing 10.10
1.The Software Center does not work at all (its activity icon just grinds away endlessly)and even highjacks and prevents me from downloading getdeb files.
2. Update manager receives updates but can not download. All I can do is use Tweak and download from it.
3. In Tweak 5.10 ( I can not upgrade higher) the unlock function in Package Cleaner can not be used, making cleaning impossible.
4.Starting computer the grub
chooses my secondary hard drive and does not let me load. My work around has been to press F11 at startup which gives me menu of drives and I manually choose main drive.
5. Constantly getting bug notices like attached:
System: Linux 2.6.35-25-generic #43-Ubuntu SMP Thu Jan 6 22:25:16 UTC 2011 i686
X Vendor: The X.Org Foundation
X Vendor Release: 10900000
Selinux: No
Accessibility: Disabled
GTK+ Theme: Mist
Icon Theme: Mist
GTK+ Modules: gnomesegvhandler, canberra-gtk-module

Memory status: size: 119869440 vsize: 119869440 resident: 13340672 share: 6758400 rss: 13340672 rss_rlim: 18446744073709551615
CPU usage: start_time: 1295756924 rtime: 4029 utime: 3175 stime: 854 cutime:0 cstime: 0 timeout: 0 it_real_value: 0 frequency: 100



----------- .xsession-errors ---------------------
** (gnome-session:2569): DEBUG: GsmDBusClient: obj_path=/org/gnome/SessionManager interface=org.gnome.SessionManager method=CanShutdown
** (gnome-session:2569): DEBUG: GsmDBusClient: obj_path=/org/gnome/SessionManager interface=org.gnome.SessionManager method=CanShutdown
** (gnome-session:2569): DEBUG: GsmManager: CanShutdown called
** (gnome-session:2569): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:2569): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:2569): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:2569): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:2569): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:2569): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
Could not attach to process.  If your uid matches the uid of the target
process, check the setting of /proc/sys/kernel/yama/ptrace_scope, or try
again as the root user.  For more details, see /etc/sysctl.d/10-ptrace.conf
ptrace: Operation not permitted.
/home/dov/2669: No such file or directory.
No stack.
-----

---


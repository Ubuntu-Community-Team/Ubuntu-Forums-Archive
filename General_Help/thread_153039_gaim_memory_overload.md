---
title: "gaim memory overload"
date: 2006-03-31
forum: General Help
---

### Post by dmizer on 2006-03-31
i've been having problems regularly with my computer locking up and becomming unusable.  windows that are already open seem to work fine, but i cannot open new programs and memory is lost.

i started watching top regularly, and when i start to have the problem, gaim will show hundreds of listings in top, each eating a small portion of my memory.

i can shut down x by ctrl + alt + backspace and boot into safe terminal, but killall gaim does not kill gaim.  the only way i am able to kill gaim is by reboot.

i'm considering compiling gaim from source to see if i can correct the problem this way, but i don't even know what the cause of the problem is because i cannot repeat the problem.

this is the 1.5.0 build that came along with the ubuntu install.  i'm not sure what tools i need to use or look at in order to isolate this problem and solve it. 

thanks for any help.

---

### Post by Barrakketh on 2006-03-31
The next time that happens save the output of "ps -A"...that's extremely odd for Gaim, which I've *never* had a problem with.

---

### Post by dmizer on 2006-04-09
okay ... finally caught it early enough that i could capture the ps -A output. it is as follows:

  PID TTY          TIME CMD
    1 ?        00:00:02 init
    2 ?        00:00:00 ksoftirqd/0
    3 ?        00:00:00 events/0
    4 ?        00:00:00 khelper
    5 ?        00:00:00 kthread
    7 ?        00:00:06 kacpid
   79 ?        00:00:00 kblockd/0
  105 ?        00:00:00 pdflush
  106 ?        00:00:00 pdflush
  108 ?        00:00:00 aio/0
  107 ?        00:00:00 kswapd0
  693 ?        00:00:00 kseriod
 1869 ?        00:00:00 khubd
 2927 ?        00:00:00 kjournald
 3053 ?        00:00:00 udevd
 4226 ?        00:00:00 khpsbpkt
 4986 ?        00:00:00 pccardd
 4996 ?        00:00:00 pccardd
 5835 ?        00:00:00 knodemgrd_0
 6488 ?        00:00:00 dhclient3
 6802 ?        00:00:00 acpid
 6817 ?        00:00:00 syslogd
 6834 ?        00:00:00 dd
 6836 ?        00:00:00 klogd
 6849 ?        00:00:00 dbus-daemon
 6862 ?        00:00:05 hald
 6867 ?        00:00:00 hald-addon-acpi
 6879 ?        00:00:02 hald-addon-stor
 7273 ?        00:00:00 gdm
 7277 ?        00:00:00 gdm
 7341 ?        00:03:44 Xorg
 7344 ?        00:00:05 cupsd
 7373 ?        00:00:00 hpiod
 7386 ?        00:00:00 python
 7485 ?        00:00:00 cardmgr
 7630 tty1     00:00:00 getty
 7631 tty2     00:00:00 getty
 7632 tty3     00:00:00 getty
 7633 tty4     00:00:00 getty
 7634 tty5     00:00:00 getty
 7635 tty6     00:00:00 getty
 7656 ?        00:00:01 gnome-session
 7704 ?        00:00:00 Xsession
 7706 ?        00:00:00 uim-xim
 7707 ?        00:00:00 ssh-agent
 7709 ?        00:00:00 uim-helper-serv
 7712 ?        00:00:00 dbus-launch
 7713 ?        00:00:00 dbus-daemon
 7715 ?        00:00:01 gconfd-2
 7720 ?        00:00:00 gnome-keyring-d
 7724 ?        00:00:06 esd
 7738 ?        00:00:00 bonobo-activati
 7740 ?        00:00:03 gnome-settings-
 7743 ?        00:00:01 gam_server
 7755 ?        00:00:01 xscreensaver
 7782 ?        00:00:51 metacity
 7787 ?        00:00:04 gnome-panel
 7789 ?        00:00:06 nautilus
 7791 ?        00:00:00 gnome-volume-ma
 7797 ?        00:00:01 update-notifier
 7800 ?        00:00:00 gnome-vfs-daemo
 7802 ?        00:00:06 gnome-cups-icon
 7807 ?        00:00:00 notification-da
 7815 ?        00:00:00 mapping-daemon
 7820 ?        00:00:00 notification-ar
 7822 ?        00:00:08 gnome-netstatus
 7824 ?        00:00:00 battstat-applet
 7826 ?        00:00:01 clock-applet
 7832 ?        00:00:00 trashapplet
 7834 ?        00:00:11 wnck-applet
 7843 ?        00:00:00 alltray
 7847 ?        00:00:11 gnome-terminal
 7850 ?        00:00:00 gnome-pty-helpe
 7851 pts/0    00:00:00 bash
 7862 ?        00:02:33 gaim
 7879 ?        00:00:00 thunderbird
 7890 ?        00:00:00 run-mozilla.sh
 7895 ?        00:00:52 thunderbird-bin
 8238 ?        00:00:00 firefox
 8251 ?        00:00:00 run-mozilla.sh
 8256 ?        00:02:37 firefox-bin
 9069 ?        00:00:18 evince
11896 ?        00:00:00 esd
11899 ?        00:00:00 gaim
11946 ?        00:00:00 gaim
11949 ?        00:00:00 gaim
12003 ?        00:00:00 gaim
12032 ?        00:00:00 gaim
12112 ?        00:00:00 gaim
12120 ?        00:00:00 gaim
12139 ?        00:00:00 gaim
12154 ?        00:00:00 gaim
12188 ?        00:00:00 gaim
12197 ?        00:00:00 gaim
12200 ?        00:00:00 gaim
12211 ?        00:00:00 gaim
12222 ?        00:00:00 gaim
12244 ?        00:00:00 gaim
12276 ?        00:00:00 gaim
12309 ?        00:00:00 gaim
12326 ?        00:00:00 gaim
12333 ?        00:00:00 gaim
12350 ?        00:00:00 gaim
12364 ?        00:00:00 gaim
12384 ?        00:00:00 gaim
12409 ?        00:00:00 gaim
12474 ?        00:00:00 gaim
12479 ?        00:00:00 gaim
12506 ?        00:00:00 gaim
12511 ?        00:00:00 gaim
12514 ?        00:00:00 gaim
12540 ?        00:00:00 gaim
12543 ?        00:00:00 gaim
12544 ?        00:00:00 gaim
12551 ?        00:00:00 gaim
12558 ?        00:00:00 gaim
12567 ?        00:00:00 gaim
12580 ?        00:00:00 gaim
12583 ?        00:00:00 gaim
12588 ?        00:00:00 gaim
12591 ?        00:00:00 gaim
12685 pts/0    00:00:00 ps

---

### Post by dmizer on 2006-04-10
a bump for a little help.  i can't seem to figure out what causes this.  some times it goes for days with no problem at all.  some times it does it multiple times in a day.

---

### Post by dmizer on 2006-04-16
okay ... one last try at this.  i can duplicate the problem every time now.

maybe i'm crazy, but i hate tabbed im.  tabbed browsing is cool and i make use of it, but i like to have all my i'ms in different windows.  anyway, if i have more than 2 im windows open in gaim, that is when i experience the problem.

i can talk online all night in gaim and never have a problem as long as i only talk to one person.

edit to add:  i have "solved" this problem by upgrading to gaim2 beta3.

---


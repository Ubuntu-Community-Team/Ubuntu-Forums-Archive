---
title: "kill desktop from terminal"
date: 2010-08-22
forum: General Help
---

### Post by spiky001 on 2010-08-22
Hi I have been looking for the command to kill desktop and leave me at prompt screen any help plz

---

### Post by dougalkerr on 2010-08-22
Why?

---

### Post by spiky001 on 2010-08-22
Because I need to get back to the prompt, if I use logout icon I get a blank screen no prompt, Ctrl Alt F1 etc same again, this is why

---

### Post by surfer on 2010-08-22
did you try

```
$ sudo service gdm restart
```

(or [FONT="Courier New"]kdm [/FONT]if you are on kubuntu)?

---

### Post by spiky001 on 2010-08-22
I tied both those thks still no good, forgot to mention i have backtrack4. I know ask in there forum I,m waiting to get log in, as it is based on ubuntu 8,10 thought I might get problem fixed here

---

### Post by stoneage on 2010-08-22
For 8.10 you want ```
sudo killall gdm
```

Also:-
 ```
sudo /etc/init.d/gdm stop
```

and:-
 ```
sudo /etc/init.d/gdm start
```

I think..... :)

---

### Post by anirudhtomer on 2010-08-22
> **stoneage said:**
> For 8.10 you want ```
sudo killall gdm
```Also:-
 ```
sudo /etc/init.d/gdm stop
```and:-
 ```
sudo /etc/init.d/gdm start
```I think..... :)

no its not working at machine. Nice question by spiky001 by the way.

---

### Post by WorMzy on 2010-08-22
What does it say when you run

```
sudo /etc/init.d/gdm stop
```

---

### Post by spiky001 on 2010-08-22
I get 

# /etc/init.d/gdm stop
bash: /etc/init.d/gdm: No such file or directory

it might be how the distro is designed as Ctrl Alt F--- dos,nt work either or logout, just a blank screen

---

### Post by stoneage on 2010-08-22
Possibly.

Which desktop do you have? Gnome, KDE, xfce?

You could look in /etc/init.d and see what's there :)

---

### Post by anirudhtomer on 2010-08-22
> **spiky001 said:**
> I get 

# /etc/init.d/gdm stop
bash: /etc/init.d/gdm: No such file or directory

it might be how the distro is designed as Ctrl Alt F--- dos,nt work either or logout, just a blank screen

I get the same message. I use 9.10

---

### Post by WorMzy on 2010-08-22
Try
```
sudo /etc/rc.d/gdm stop
```

If that doesn't work then could you post the output of this command:
```
ls -lap /etc | grep '\.d/'
```

---

### Post by spiky001 on 2010-08-22
cant find it in etc/init.d but I think it,s kde so where is it?

---

### Post by WorMzy on 2010-08-22
If you use KDE, then replace gdm with kdm.

So

```
sudo /etc/init.d/kdm stop
```

or

```
sudo /etc/rc.d/kdm stop
```

```
sudo killall kdm
```
Will probably work, but it's not a very elegant solution.

---

### Post by spiky001 on 2010-08-22
output

```
~# ls -lap /etc | grep '\.d/'
drwxr-xr-x   3 root  root      4096 Dec 14  2009 apparmor.d/
drwxr-xr-x   2 root  root      4096 Aug 20 21:05 bash_completion.d/
drwxr-xr-x   2 root  root      4096 Aug 20 21:05 cron.d/
drwxr-xr-x   2 root  root      4096 May 10  2009 depmod.d/
drwxr-xr-x   2 root  root      4096 May 11  2009 discover.conf.d/
drwxr-xr-x   2 root  root      4096 May 30  2009 event.d/
drwxr-xr-x   2 root  root      4096 Dec 14  2009 gre.d/
drwxr-xr-x   2 root  root      4096 May 10  2009 grub.d/
drwxr-xr-x   2 root  root      4096 Aug  1  2008 inetd.d/
drwxr-xr-x   2 root  root      4096 Jan  9  2010 init.d/
drwxr-xr-x   2 root  root      4096 Jan  9  2010 ld.so.conf.d/
drwxr-xr-x   2 root  root      4096 Jun 19  2008 libpaper.d/
drwxr-xr-x   2 root  root      4096 Dec 14  2009 logrotate.d/
drwxr-xr-x   3 root  root      4096 Aug 20 20:59 modprobe.d/
drwxr-xr-x   2 root  root      4096 Dec 14  2009 pam.d/
drwxr-xr-x   2 root  root      4096 Oct 20  2008 profile.d/
drwxr-xr-x   2 root  root      4096 Dec 14  2009 rc0.d/
drwxr-xr-x   2 root  root      4096 Jan  9  2010 rc1.d/
drwxr-xr-x   2 root  root      4096 Jan  9  2010 rc2.d/
drwxr-xr-x   2 root  root      4096 Jan  9  2010 rc3.d/
drwxr-xr-x   2 root  root      4096 Jan  9  2010 rc4.d/
drwxr-xr-x   2 root  root      4096 Jan  9  2010 rc5.d/
drwxr-xr-x   2 root  root      4096 Dec 14  2009 rc6.d/
drwxr-xr-x   2 root  root      4096 May 28  2009 rcS.d/
drwxr-xr-x   2 root  root      4096 May 28  2009 reader.conf.d/
drwxr-xr-x   2 root  root      4096 May 28  2009 sysctl.d/

```

The other commands didn't work

---

### Post by WorMzy on 2010-08-22
Okay, now can you run
```
ls /etc/init.d
```

It seems you're not using gdm or kdm, so hopefully that command will tell us what you *are* using.

EDIT: Post output here.

---

### Post by spiky001 on 2010-08-22
```
root@bt:~# ls /etc/init.d
README                           mountoverflowtmp
acpid                            mtab.sh
alsa-utils                       mysql
apache2                          mysql-ndb
arpalert                         mysql-ndb-mgm
atd                              networking
atftpd                           nstxcd
avahi-daemon                     nstxd
binfmt-support                   ntop
bluetooth                        openvpn
bootlogd                         pcscd
bootmisc.sh                      policykit
casper                           postgresql-8.3
checkfs.sh                       pppd-dns
checkroot.sh                     procps
clamav-freshclam                 rc
console-screen.kbd.sh            rc.local
console-setup                    rcS
cpufrequtils                     reboot
cron                             rinetd
cryptdisks                       rmnologin
cryptdisks-early                 rsync
cups                             screen-cleanup
dbus                             sendmail
dhcp3-server                     sendsigs
dns-clean                        single
dns2tcp                          skeleton
glibc.sh                         snort
gpsd                             splashy
hal                              ssh
halt                             stop-bootlogd
hostname.sh                      stop-bootlogd-single
hwclock.sh                       stunnel4
hwclockfirst.sh                  sysklogd
inetutils-inetd                  system-tools-backends
keyboard-setup                   tinyproxy
killprocs                        ubiquity
klogd                            udev
linux-restricted-modules-common  udev-finish
loadcpufreq                      ufw
loopback                         umountfs
miredo                           umountnfs.sh
miredo-server                    umountroot
module-init-tools                urandom
mountall-bootclean.sh            wicd
mountall.sh                      winbind
mountdevsubfs.sh                 wpa-ifupdown
mountkernfs.sh                   x11-common
mountnfs-bootclean.sh            xserver-xorg-input-wacom
mountnfs.sh

```

I have got into Btrack forum and posted but they not as quick as here

---

### Post by WorMzy on 2010-08-22
Strange, I can't see any Window managers that I recognise. Maybe someone else will be able to spot one. 

For now, you could try running this to kill X server: ```
sudo kill `cat /tmp/.X0-lock`
```

---

### Post by spiky001 on 2010-08-22
Yep that killed it but just get blank screen

---

### Post by stoneage on 2010-08-22
....which is the problem you actually have. :)

---

### Post by spiky001 on 2010-08-22
I need to be able to logout? My theory was kill desktop end up at a prompt, logout gets blank screen so dose ctrl alt, as bt4 is run at root I created an account with less privlages as ubuntu but you need root to do nearly all things, hope you can see my way of thinking

---

### Post by WorMzy on 2010-08-22
That's where sudo comes in. Install sudo if you don't already have it installed, and add the unprivileged user to the sudoers file with ```
# visudo
```
Or, if you don't like/know how to use vi:
```
# EDITOR=nano visudo
```

Add something like this:
```
USERNAME    ALL=(ALL) ALL
```

Save the file and exit.

From then on, you can log in as your normal user, and still "pretend" to be root by prepending "sudo" to the start of your commands. If you want to run graphical applications as root, then install gksu; then add "gksudo" to the start of your GUI launching commands (e.g. "gksudo nautilus").

---

### Post by spiky001 on 2010-08-23
The problem is not being root because when i,m logged in as root same thing, got a reply from BT4 had suggestion of Ctrl+Alt+Backspace that kills desktop but end up at blank screen, A thought that when I try Ctrl+Alt+F1-2 etc I get a blank screen not Prompt as with Ubuntu or even Open suse,

---

### Post by spiky001 on 2010-08-24
Ok been googling alot about this have found a few probs mostly vga settings,they mention adjusting vga to something 762ish ok now if I want to try this where do I set it? pc boots grub2, sdb where BT4 is uses Grub so am I right in thinking adjust menu1st on sdb instead of grub2 on sda

have just checked Grub.cfg vga is set to 771
menu1st is set to 0x317

---

### Post by Chris1274 on 2010-08-24
> **spiky001 said:**
> Hi I have been looking for the command to kill desktop and leave me at prompt screen any help plz

Have you tried
```
killall Xorg
```?

---

### Post by JKyleOKC on 2010-08-24
> **spiky001 said:**
> have just checked Grub.cfg vga is set to 771
menu1st is set to 0x317Try setting vga=257 and menulst=0x101 (those are actually the same value, one in decimal and the other in hex). That should give you a 640x480x8 resolution on the consoles, which will be huge characters but if you get a prompt at all you'll be able to work...

However if your copy of grub2 is version 1.98, the vga settings may not have any effect at all. They did in 1.97, but were apparently disabled in the next point release...

---

### Post by spiky001 on 2010-08-25
hi thks for advice if I adjust grub.cfg will this not upset the karmic version I only have probs with BT4 on sdb, or should both be reset, grub.cfg has no settings for BT$ vga in it

Karmic all works fine

---

### Post by JKyleOKC on 2010-08-25
I don't know the exact version of grub that you have with Karmic; I only install the LTS versions so went straight from Hardy to Lucid. I believe that Karmic used 1.97, which was grub2 but which did respond to the "vga=" settings. Lucid has 1.98; the vga= setting has no effect on my ATI box but makes the consoles unreadable on my two nvidia boxes. All three are using the proprietary video drivers...

---

### Post by spiky001 on 2010-08-25
OK so I have more progress tty works on BT4 BUT I cant see what i,m typing if I go into Ctrl Alt F1 I can reboot the machine ok, but I cant see what i,m typing, so I need to bring up the font so it,s visible, is this adjusted by VGA setting in menu1st as this is the grub for BT4? Or is there another place I need to be looking?

---

### Post by VanillaMozilla on 2010-08-25
Have you tried just opening a terminal and saving yourself a huge amount of trouble?  You just run a terminal in a window like any other program.  It's in your Applications menu.  I can't think of anything you can't do from there.

And if you use sudo, you should never have to log in as root, as far as I know.  Giving yourself a root password is considered a bad idea on Ubuntu.

Even if you do have to log in as root for some crazy reason, you can switch users right on the spot, in your terminal window.  I forget the command name, but it's certainly well-known to *nix users.

If you actually have a valid reason, I think I can give you an incantation to use, but you need a note from your mother.

---

### Post by spiky001 on 2010-08-25
Ok I take your point Vanilla I have taken it on board
```
sudo user
password
```
But I think that by curing the problem it will solve the logout problem (which is a blank screen) and i would like to learn on fixing probs instead of that'll do!

---

### Post by VanillaMozilla on 2010-08-25
As I understand it, your actual problem is that Ubuntu hangs on logout?  Maybe you should start a new thread, describe that problem, and use a descriptive title.

If your system is functioning, you can usually edit configuration files and install or uninstall programs from a terminal.  Plus, you have all the desktop resources.  If you really need just a bare Linux command line, you can start Ubuntu in recovery mode from Grub.  Or you can exit the X Windows system somehow, as someone has probably mentioned by now.

You can also get a command line from <Ctrl><Alt><F1> (the first 6 function keys each give you a command line), but I think the desktop is still running behind all that, so I don't know if it's really the right thing.  Then I _think_ you can get back to the desktop with <Ctrl><Alt><F7>.  It's either that or the power button, so don't leave anything important on the burner.

Good luck.

By the way, the command is
sudo <command>
.  If the command starts a program that uses a gui instead of a command line, you're supposed to use the command
gksudo <command>
instead of sudo, or else you'll be infested with frogs or something.

---

### Post by mensfort on 2011-06-24
You may try:

ctrl + alt + F2

type name + password;

ps aux

then you get a list.

kill -9 <number>      to kill whatever you don't like.

if you want to go back;
 
ctrl + alt + F7

---


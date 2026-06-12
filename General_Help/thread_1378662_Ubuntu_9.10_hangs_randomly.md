---
title: "Ubuntu 9.10 hangs randomly"
date: 2010-01-11
forum: General Help
---

### Post by tombaugh on 2010-01-11
Hi,

My Ubuntu 9.10 hangs quite frequently. This often happens right after booting (desktop visible but before I can even enter my default keyring password) but also later on, usually when I'm browsing. The system then becomes completely non responsive.

Are there any logs I should check? Any thoughts? 
Thanks

---

### Post by tombaugh on 2010-01-18
I'm getting a bit frustrated now. Today it happened four times before I was able to use my system properly...

---

### Post by mörgæs on 2010-01-18
Do you get the same problem with a 9.04 Live CD? 

[http://releases.ubuntu.com/9.04/](http://releases.ubuntu.com/9.04/)

---

### Post by Portmanteaufu on 2010-01-18
> **tombaugh said:**
> I'm getting a bit frustrated now. Today it happened four times before I was able to use my system properly...

Yeah, that sounds pretty aggravating.

Is this a clean Ubuntu install? Have you added any software, particularly drivers or background services that weren't part of the distribution? Applets? When you run 'top' in the command line, do you see anything that appears to be bogarting your resources?

---

### Post by tombaugh on 2010-01-18
I haven't tried the live CD, but I have another drive with Ubuntu 9.10 and that one runs fine. The system giving problems is not a new install, the other one is. 

@Portmanteaufu I have installed lots of things, but resource usage appears to be normal.

---

### Post by Portmanteaufu on 2010-01-18
> **tombaugh said:**
> 
@Portmanteaufu I have installed lots of things, but resource usage appears to be normal.

Could you list some of the things which are always running in the background? Are you using Nvidia drivers, have you installed an applet to check the weather every minute, etc? 

Have you set up any cron jobs?

The more we know about what's running when the problem happens, the better the odds of our being able to help.

---

### Post by tombaugh on 2010-01-18
Yes, I have NVIDIA drivers (185), no desktop applets though. Things that start up automatically: skype, gmail-notify, pidgin, tomboy.

According to webmin:

cron jobs

> Active?        Command        Move   
Yes     /etc/cron.daily/samba
    /etc/cron.daily/man-db
    /etc/cron.daily/apache2
    /etc/cron.daily/apt
    /etc/cron.daily/0anacron
    /etc/cron.daily/mlocate
    /etc/cron.daily/bsdmainutils
    /etc/cron.daily/sysklogd
    /etc/cron.daily/aptitude
    /etc/cron.daily/logrotate
    /etc/cron.daily/apport
    /etc/cron.daily/dpkg
    /etc/cron.daily/webalizer
    /etc/cron.daily/jetty
    /etc/cron.daily/standard
    /etc/cron.daily/popularity-contest     
Yes     /etc/cron.weekly/man-db
    /etc/cron.weekly/0anacron
    /etc/cron.weekly/apt-xapian-index
    /etc/cron.weekly/sysklogd
    /etc/cron.weekly/cvs     
Yes     /etc/cron.monthly/0anacron
    /etc/cron.monthly/standard     
No     test -x /etc/init.d/anacron && /usr/sbin/invoke-rc.d anacron start >/dev/null     
Yes     start -q anacron || :     
Yes     [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ ...     
Yes     /etc/webmin/cron/tempdelete.pl 

boot

> Action        At boot?       Description   
acpi-support     Yes     INIT script to check whether we're on batteries, and so start with laptop mode etc enabled. BUGS: unless we start *really* late, we have no way of throttling xscreensaver, since it won't be there to command.
apache2     Yes     Start/stop apache2 web server
binfmt-support     Yes     Enable support for extra binary formats using the Linux
bluetooth     Yes     Start bluetoothd
cups     Yes     CUPS Printing spooler and server
dkms_autoinstaller     Yes     A service to automatically install DKMS modules for new kernels.
dns-clean     Yes     0dns-up often leaves behind some cruft. This Script is meant
grub-common     Yes     GRUB displays the boot menu at the next boot if it
hotkey-setup     Yes     Set up laptop keys to generate keycodes.
jackd     Yes     init-Script for system wide fetchmail daemon
jetty     Yes     Start Jetty HTTP server and servlet container.
kerneloops     Yes     A tool that collects and submits kernel crash
klogd     Yes     Kernel logger
laptop-mode     Yes     Enable laptop-mode-tools power management functions
minidlna     Yes     chkconfig: 345 99 10 description: Startup/shutdown script for MiniDLNA daemon
mysql     Yes     Controls the main MySQL database server daemon "mysqld"
odccm     Yes     Start odccm daemon
ondemand     Yes     Set the CPU Frequency Scaling governor to "ondemand"
policykit     Yes     Create directories which PolicyKit needs at runtime,
pppd-dns     Yes     Restore resolv.conf if the system crashed.
pulseaudio     Yes     System mode startup script for
rc.local     Yes     Run /etc/rc.local if it exist
rsync     Yes     rsync is a program that allows files to be copied to and
samba     Yes     start Samba daemons (nmbd and smbd)
saned     Yes     saned makes local scanners available over the
speech-dispatcher     Yes     Common interface to speech synthesizers
ssh     Yes     OpenBSD Secure Shell server
stop-readahead     Yes     init script for stopping readahead profiling
sysklogd     Yes     System logger
virtualbox-ose     Yes     VirtualBox Linux kernel module
vsftpd     Yes     Very secure FTP server
webmin     Yes     Start/stop Webmin
winbind     Yes     start Winbind daemon
xinetd     Yes     Start or stop the xinetd daemon.

---

### Post by dodderer on 2010-01-23
same problem I thought it was firefox at fault but today it happened also in Abiword.
How does one check for causes? not a programmer been using ubuntu kubuntufor a while

---

### Post by ephman on 2010-01-23
are you running a nvidia video card?  that's been causing some issues.  

ephman

---

### Post by tombaugh on 2010-01-23
> **ephman said:**
> are you running a nvidia video card?  that's been causing some issues.

Yes, it's a MSI N9600GT. Do you have any references about that?

---

### Post by ephman on 2010-01-23
where did you get the driver from the repository or from nvidia's website?  and what version driver are you using?  

try this open up the nvidia x server settings in preferences, and you'll see a powermizer option.  set that to maximum.  then give it a whirl.  for some people that works for some others it doesn't.  i'm in a bit of rush to head out.  but if you search these forums for nvidia crashing or hanging you'll see a lot of references.  this issue took me a long to figure out.  but it doesn't seem to fix it for everybody.  btw i have the nvidia 9650m gt, and i'm currently running the lastest driver from their site. 

[http://ubuntuforums.org/showthread.php?t=1300938&highlight=ephman](http://ubuntuforums.org/showthread.php?t=1300938&highlight=ephman)

---

### Post by tombaugh on 2010-01-23
I'm using version 185. That's the proprietary one, so I guess I got it from the website? I found the powermizer thing, but I can't change anything on that tab...

---

### Post by ephman on 2010-01-24
i don't believe in 185 you are able to change the option.  in 190 and the beta 195 i know you can.

ephman

---

### Post by elle_stone on 2010-01-30
I think the problem might be mlocate. See this bug report: [https://bugs.launchpad.net/ubuntu/+source/findutils/+bug/332790](https://bugs.launchpad.net/ubuntu/+source/findutils/+bug/332790).

I'm having the same problem. Ubuntu 9.10 on amd 64-bit computer. I did a fresh install in November, 2009, using the minimal install CD, using icewm, not a full gnome or kde environment. I've added a lot of packages since the initial install. But I don't think the problem is related to any packages that I personally added since the initial setup, as the problem has been happening several times a day since the initial install.

I've been running htop, trying to catch the offending process in the act. This morning, shortly after turning the computer on, running htop with no threads etc hidden, sorted by cpu usage, mlocate popped to the top as the cpu went up and the computer slowed to a halt. Which is how I found this thread.

I don't have a solution. I hope this potential lead might be useful in tracking down this annoying behavior. If I do come up with a solution I'll post it.

Is there a downside to just uninstalling mlocate? It is only listed in cron.daily, but if it is the same process that ties up the computer several times a day, it gets triggered more than once a day.

Elle

---

### Post by elle_stone on 2010-01-31
The problem isn't mlocate. Yesterday I ran the computer several hours, not using Firefox, and the only time it froze was shortly after startup. Today I've been using the computer for only an hour, with Firefox open, and the computer has frozen three times, in addition to the startup freeze.

---


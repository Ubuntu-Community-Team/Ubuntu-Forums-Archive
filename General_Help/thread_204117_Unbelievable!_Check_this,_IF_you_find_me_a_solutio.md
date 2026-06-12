---
title: "Unbelievable! Check this, IF you find me a solution you ROCK! (Mail apps thread)"
date: 2006-06-26
forum: General Help
---

### Post by turbojugend_gr on 2006-06-26
Hi everyone, I closed my previous thread on that, as now it has gone into another dimesion!

Check this out.

It all started 10 days ago, evolution (mail application) kept starting with no Reason, every 45 mins approximately it poped up, no new mail situation!

I tried several things to make go away, as you may guess none worked. Therefore I completely removed that along with many other packages I thought it was related (along with the ones Synaptic removed by itself). I installed thunderbird (mail application), I lost an hour to recreate my contacts, I did, I closed it, and in about 45-90 mins it POPED up again! Excactly as evolution!

Well I find my self wondering here??? Anyway if you have a clue: 1st I will give a great congrats, 2nd you will become a legend of mine, as I never heard, read or found anything similar yet!

Thanx in advance for your trouble to go through this Post anyway.

---

### Post by chadk on 2006-06-26
Wow, while I can't help you, I wanted to tell you that I really like your enthusiasm!  :-D

---

### Post by ejos on 2006-06-26
Well since it clearly is a problem with only mail apps, it must be some externel program calling your default email client. Try shutting down things that might do that.

---

### Post by turbojugend_gr on 2006-06-26
[QUOTE=chadk]Wow, while I can't help you, I wanted to tell you that I really like your enthusiasm!  :-D[/QUOTE]

Well I like to keep this problem as a challenge to me and others, First of all it is not so annoying to me, and secondly I 'd like to stop wiining about ubuntu problems, because I found almost all of mine solved easily, or unexpectedly, or even better with an update... 

So I decided I will try to enjoy this one as a challenge, I hope others will do so also!

---

### Post by turbojugend_gr on 2006-06-26
[QUOTE=ejos]Well since it clearly is a problem with only mail apps, it must be some externel program calling your default email client. Try shutting down things that might do that.[/QUOTE]

Like what? Imagine, though I removed evolution data serverit is shown in the system-monitor as sleeping! Give a hint though if you are refering to sth specificly.

---

### Post by maxol on 2006-06-26
Do you have any  system monitors such as GKrellM running? These could cause something like this.

---

### Post by turbojugend_gr on 2006-06-26
[QUOTE=maxol]Do you have any  system monitors such as GKrellM running? These could cause something like this.[/QUOTE]

First of all, Thanx for your interest in that!

No I don't though, I only use the system-monitor (ubuntu's native one), or top command in a terminal, from time to time, when I need to check something.

I use a desklet though for checking my account, but I don't believe that's to blame as I use it with no alteration for about 6 months now, I actually moved my gDesklets config from Suse to Breezy and from Breezy to Dapper, never had an Isuue. Anyway I mention it in case it is usefull to someone.

---

### Post by viciouslime on 2006-06-26
Do you have a keyboard with multimedia keys? I've seen a key get something sticky underneath it before and start programs at random intervals.

---

### Post by turbojugend_gr on 2006-06-26
[QUOTE=viciouslime]Do you have a keyboard with multimedia keys? I've seen a key get something sticky underneath it before and start programs at random intervals.[/QUOTE]

I suppose you answered yes! Well (since I do own such a keyboard) this could be the case given the fact I didn't change the application, you see now the "problematic" key would just fail to start evolution. Very nice idea though.

---

### Post by ronb on 2006-06-26
Can cron do something like this?

---

### Post by turbojugend_gr on 2006-06-26
[QUOTE=ronb]Can cron do something like this?[/QUOTE]
 What is cron?

---

### Post by cotcot on 2006-06-26
And what if you try with another email account (you could install Opera and make an operamail account and see if you still have the holy 45 minutes) ? Or the same account but on a different computer if you have the possibility ?

---

### Post by turbojugend_gr on 2006-06-26
[QUOTE=cotcot]And what if you try with another email account (you could install Opera and make an operamail account and see if you still have the holy 45 minutes) ? Or the same account but on a different computer if you have the possibility ?[/QUOTE]


Yet another good idea! Though it is not the one, as I have this account in another machine allread (as you say) and there's no problem.... So changing the client shouldn't be the case also, as evolution in my older machine I use in my beach house works gracefully! Thank you for troubling though. Wow, boy we have a nice community don't we?

---

### Post by scxtt on 2006-06-26
[QUOTE=ronb]Can cron do something like this?[/QUOTE]sure - but it'd have to be set up to ... and i doubt turbojugend_gr "messed" w/ any crons considering he's not heard of them ...

crons are automated tasks that you can specify to run at a given interval - similar to MS's "task scheduler", but better - cause it's not windows 8) ...

type "man anacron" and read up on anacron if you want - crons are great - :-D

hey turbojugend_gr, do a "ps -ef" and post the output in here, after it happens next time ...

---

### Post by turbojugend_gr on 2006-06-26
[QUOTE=scxtt]sure - but it'd have to be set up to ... and i doubt turbojugend_gr "messed" w/ any crons considering he's not heard of them ...

crons are automated tasks that you can specify to run at a given interval - similar to MS's "task scheduler", but better - cause it's not windows 8) ...

type "man anacron" and read up on anacron if you want - crons are great - :-D

hey turbojugend_gr, do a "ps -ef" and post the output in here, after it happens next time ...[/QUOTE]

I will do that, I love this community everybody is so eager to provide help!

But as my signature says I like knowing what I do... So what this command provide me with?

---

### Post by scxtt on 2006-06-26
it will list the current running processes (do a "man ps", the "-ef" are flags that are passed to ps) ... maybe someone can notice some program that might be opening Evol./Thunderbird ...

---

### Post by maka on 2006-06-26
[QUOTE=ronb]Can cron do something like this?[/QUOTE]

yeah it can, go to a terminal and type crontab -l

see if it lists anything that runs evolution

---

### Post by Hairy_Palms on 2006-06-26
the moment it pops up you should open a terminal and type 
top
to see what programs are running and in particular any mail backends such as fetchmail.

---

### Post by turbojugend_gr on 2006-06-27
Here it is, output for ps-ef, I don't see anything though, maybe some more "fit" eyes will...:

```
turbojugend@TurboPC:~$ ps -ef
UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 16:44 ?        00:00:01 init [2]
root         2     1  0 16:44 ?        00:00:00 [migration/0]
root         3     1  0 16:44 ?        00:00:00 [ksoftirqd/0]
root         4     1  0 16:44 ?        00:00:00 [watchdog/0]
root         5     1  0 16:44 ?        00:00:00 [migration/1]
root         6     1  0 16:44 ?        00:00:00 [ksoftirqd/1]
root         7     1  0 16:44 ?        00:00:00 [watchdog/1]
root         8     1  0 16:44 ?        00:00:00 [events/0]
root         9     1  0 16:44 ?        00:00:00 [events/1]
root        10     1  0 16:44 ?        00:00:00 [khelper]
root        11     1  0 16:44 ?        00:00:00 [kthread]
root        14    11  0 16:44 ?        00:00:00 [kblockd/0]
root        15    11  0 16:44 ?        00:00:00 [kblockd/1]
root        16    11  0 16:44 ?        00:00:00 [kacpid]
root       177    11  0 16:44 ?        00:00:00 [pdflush]
root       178    11  0 16:44 ?        00:00:00 [pdflush]
root       180    11  0 16:44 ?        00:00:00 [aio/0]
root       181    11  0 16:44 ?        00:00:00 [aio/1]
root       179     1  0 16:44 ?        00:00:00 [kswapd0]
root       777    11  0 16:44 ?        00:00:00 [kseriod]
root       861     1  0 16:44 ?        00:00:00 [kirqd]
root      1821    11  0 16:44 ?        00:00:00 [ata/0]
root      1822    11  0 16:44 ?        00:00:00 [ata/1]
root      1823    11  0 16:44 ?        00:00:00 [ata_hotplug/0]
root      1824    11  0 16:44 ?        00:00:00 [ata_hotplug/1]
root      1829    11  0 16:44 ?        00:00:00 [scsi_eh_0]
root      1830    11  0 16:44 ?        00:00:00 [scsi_eh_1]
root      1834    11  0 16:44 ?        00:00:00 [scsi_eh_2]
root      1835    11  0 16:44 ?        00:00:00 [scsi_eh_3]
root      2024    11  0 16:44 ?        00:00:00 [khubd]
root      2036     1  0 16:44 ?        00:00:00 [khpsbpkt]
root      2055     1  0 16:44 ?        00:00:00 [knodemgrd_0]
root      2143     1  0 16:44 ?        00:00:00 [kjournald]
root      2385     1  0 16:44 ?        00:00:00 /sbin/udevd --daemon
root      3317     1  0 16:44 ?        00:00:00 [shpchpd_event]
root      3376    11  0 16:44 ?        00:00:00 [kgameportd]
root      3815     1  0 16:45 ?        00:00:00 [kjournald]
root      4275     1  0 16:45 ?        00:00:00 /usr/sbin/acpid -c /etc/acpi/everoot      4411     1  0 16:45 ?        00:00:00 /bin/dd bs 1 if /proc/kmsg of /vklog      4413     1  0 16:45 ?        00:00:00 /sbin/klogd -P /var/run/klogd/kmroot      4732     1  0 16:45 ?        00:00:00 /usr/sbin/gdm
root      4743  4732  0 16:45 ?        00:00:00 /usr/sbin/gdm
root      4762  4743  1 16:45 ?        00:00:11 /usr/bin/Xgl :0 :0 -fullscreen -hplip     4771     1  0 16:45 ?        00:00:00 /usr/sbin/hpiod
root      4773  4762  0 16:45 tty7     00:00:01 /usr/bin/Xorg vt7 -auth /tmp/.Xghplip     4775     1  0 16:45 ?        00:00:00 python /usr/sbin/hpssd
104       4855     1  0 16:45 ?        00:00:00 /usr/bin/dbus-daemon --system
108       4870     1  0 16:45 ?        00:00:00 /usr/sbin/hald
root      4871  4870  0 16:45 ?        00:00:00 hald-runner
108       4876  4871  0 16:45 ?        00:00:00 /usr/lib/hal/hald-addon-acpi
108       4926  4871  0 16:45 ?        00:00:00 /usr/lib/hal/hald-addon-keyboard108       4936  4871  0 16:45 ?        00:00:00 /usr/lib/hal/hald-addon-storage
108       4937  4871  0 16:45 ?        00:00:00 /usr/lib/hal/hald-addon-storage
108       4939  4871  0 16:45 ?        00:00:00 /usr/lib/hal/hald-addon-storage
108       4940  4871  0 16:45 ?        00:00:00 /usr/lib/hal/hald-addon-storage
root      5024     1  0 16:45 ?        00:00:00 hcid: processing events
root      5028     1  0 16:45 ?        00:00:00 /usr/sbin/sdpd
root      5048     1  0 16:45 ?        00:00:00 [krfcommd]
root      5062     1  0 16:45 ?        00:00:00 /sbin/mdadm -F -i /var/run/mdadmdaemon    5096     1  0 16:45 ?        00:00:00 /usr/sbin/atd
root      5109     1  0 16:45 ?        00:00:00 /usr/sbin/cron
root      5204     1  0 16:45 tty1     00:00:00 /sbin/getty 38400 tty1
root      5206     1  0 16:45 tty2     00:00:00 /sbin/getty 38400 tty2
root      5207     1  0 16:45 tty3     00:00:00 /sbin/getty 38400 tty3
root      5208     1  0 16:45 tty4     00:00:00 /sbin/getty 38400 tty4
root      5209     1  0 16:45 tty5     00:00:00 /sbin/getty 38400 tty5
root      5210     1  0 16:45 tty6     00:00:00 /sbin/getty 38400 tty6
1000      5221  4743  0 16:49 ?        00:00:00 /usr/bin/gnome-session
1000      5264  5221  0 16:49 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/dbus1000      5267     1  0 16:49 ?        00:00:00 /usr/bin/dbus-launch --exit-with1000      5268     1  0 16:49 ?        00:00:00 dbus-daemon --fork --print-pid 81000      5270     1  0 16:49 ?        00:00:00 /usr/lib/libgconf2-4/gconfd-2 5
1000      5273     1  0 16:49 ?        00:00:00 /usr/bin/gnome-keyring-daemon
1000      5275     1  0 16:49 ?        00:00:00 /usr/lib/bonobo-activation/bonob1000      5277     1  0 16:49 ?        00:00:00 /usr/lib/control-center/gnome-se1000      5279     1  0 16:49 ?        00:00:00 /usr/bin/esd -terminate -nobeeps1000      5286     1  0 16:49 ?        00:00:00 /usr/bin/metacity --sm-client-id1000      5297     1  0 16:49 ?        00:00:02 gnome-panel --sm-client-id defau1000      5299     1  0 16:49 ?        00:00:00 nautilus --no-default-window --s1000      5302     1  0 16:49 ?        00:00:00 gnome-volume-manager --sm-client1000      5308     1  0 16:49 ?        00:00:01 gaim
1000      5310     1  0 16:49 ?        00:00:00 update-notifier
1000      5313     1  0 16:49 ?        00:00:00 /usr/lib/gnome-vfs-2.0/gnome-vfs1000      5315     1  0 16:49 ?        00:00:00 mono /usr/lib/tomboy/Tomboy.exe
1000      5329     1  0 16:49 ?        00:00:00 beagled --debug /usr/lib/beagle/1000      5335     1  0 16:49 ?        00:00:00 gnome-cups-icon --sm-client-id d1000      5348     1  0 16:49 ?        00:00:00 /usr/lib/gamin/gam_server
1000      5352     1  3 16:49 ?        00:00:22 python /usr/lib/gdesklets/gdeskl1000      5353     1  0 16:49 ?        00:00:00 gnome-power-manager
1000      5361     1  0 16:49 ?        00:00:00 /usr/lib/nautilus-cd-burner/mapp1000      5375     1  0 16:49 ?        00:00:00 /usr/lib/gnome-applets/gnome-key1000      5377     1  0 16:49 ?        00:00:00 /usr/lib/gnome-applets/mixer_app1000      5401     1  0 16:49 ?        00:00:00 gnome-screensaver
cupsys    5581     1  0 16:50 ?        00:00:00 /usr/sbin/cupsd
syslog    5715     1  0 16:52 ?        00:00:00 /sbin/syslogd -u syslog
1000      5732     1  0 16:52 ?        00:00:00 /usr/lib/notification-daemon/not1000      5957  5329  0 16:59 ?        00:00:00 beagled-helper --debug /usr/lib/1000      5967     1  4 16:59 ?        00:00:04 /usr/lib/firefox/firefox-bin -a
1000      6046     1  5 17:01 ?        00:00:00 gnome-terminal
1000      6047  6046  0 17:01 ?        00:00:00 gnome-pty-helper
1000      6048  6046  0 17:01 pts/0    00:00:00 bash
1000      6070  6048  0 17:01 pts/0    00:00:00 ps -ef

```

---

### Post by turbojugend_gr on 2006-06-27
[QUOTE=maka]yeah it can, go to a terminal and type crontab -l

see if it lists anything that runs evolution[/QUOTE]

Well i seem to lack this app... since I get this:

```
turbojugend@TurboPC:~$ crontab -l
no crontab for turbojugend

```

---

### Post by turbojugend_gr on 2006-06-27
[QUOTE=Hairy_Palms]the moment it pops up you should open a terminal and type 
top
to see what programs are running and in particular any mail backends such as fetchmail.[/QUOTE]

I do this everytime, but never found something that looked a "suspect" for me, I will post the output though so you will see yourself, you might "sniff" something out:

```
top - 17:07:44 up 23 min,  2 users,  load average: 0.05, 0.13, 0.13
Tasks: 102 total,   1 running, 101 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.5% us,  0.3% sy,  0.0% ni, 98.2% id,  0.0% wa,  0.0% hi,  0.0% si
Mem:   1034660k total,   794388k used,   240272k free,    90284k buffers
Swap:  2104504k total,        0k used,  2104504k free,   390816k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 6046 turbojug  15   0 42340  16m  10m S    1  1.6   0:04.65 gnome-terminal
 4762 root      15   0 84560  69m  15m S    1  6.8   0:20.99 Xgl
 5352 turbojug  15   0 86164  38m  11m S    1  3.8   0:26.24 python
 5302 turbojug  17   0 18688 6396 4896 S    0  0.6   0:00.46 gnome-volume-ma
 5967 turbojug  15   0  102m  36m  19m S    0  3.6   0:11.74 firefox-bin
 6213 turbojug  16   0  2196 1112  856 R    0  0.1   0:00.05 top
    1 root      16   0  1568  532  460 S    0  0.1   0:01.14 init
    2 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0
    3 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0
    4 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1
    6 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1
    7 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1
    8 root      10  -5     0    0    0 S    0  0.0   0:00.04 events/0
    9 root      10  -5     0    0    0 S    0  0.0   0:00.02 events/1
   10 root      11  -5     0    0    0 S    0  0.0   0:00.00 khelper
   11 root      10  -5     0    0    0 S    0  0.0   0:00.00 kthread
   14 root      10  -5     0    0    0 S    0  0.0   0:00.30 kblockd/0
   15 root      10  -5     0    0    0 S    0  0.0   0:00.00 kblockd/1
   16 root      20  -5     0    0    0 S    0  0.0   0:00.00 kacpid
  177 root      20   0     0    0    0 S    0  0.0   0:00.00 pdflush
  178 root      15   0     0    0    0 S    0  0.0   0:00.00 pdflush
  180 root      11  -5     0    0    0 S    0  0.0   0:00.00 aio/0
  181 root      11  -5     0    0    0 S    0  0.0   0:00.00 aio/1
  179 root      25   0     0    0    0 S    0  0.0   0:00.00 kswapd0
  777 root      10  -5     0    0    0 S    0  0.0   0:00.01 kseriod
  861 root      15   0     0    0    0 S    0  0.0   0:00.00 kirqd
 1821 root      13  -5     0    0    0 S    0  0.0   0:00.00 ata/0
 1822 root      10  -5     0    0    0 S    0  0.0   0:00.00 ata/1
 1823 root      13  -5     0    0    0 S    0  0.0   0:00.00 ata_hotplug/0
 1824 root      13  -5     0    0    0 S    0  0.0   0:00.00 ata_hotplug/1
 1829 root      14  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_0
 1830 root      14  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_1
 1834 root      11  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_2
 1835 root      11  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_3
 2024 root      10  -5     0    0    0 S    0  0.0   0:00.00 khubd
 2036 root      15   0     0    0    0 S    0  0.0   0:00.00 khpsbpkt
 2055 root      15   0     0    0    0 S    0  0.0   0:00.00 knodemgrd_0
 2143 root      15   0     0    0    0 S    0  0.0   0:00.03 kjournald
 2385 root      13  -4  2432  900  344 S    0  0.1   0:00.18 udevd
 3317 root      20   0     0    0    0 S    0  0.0   0:00.00 shpchpd_event
 3376 root      10  -5     0    0    0 S    0  0.0   0:00.00 kgameportd
 3815 root      15   0     0    0    0 S    0  0.0   0:00.00 kjournald
 4275 root      16   0  2152 1196  644 S    0  0.1   0:00.00 acpid


```

Note that I had to pause that (CTRL-Z) in order to copy it... So it is a little late picture of my sys, anyway you might still find it usefull.

Thank you all for your response, I see some of you are challenged too, nice!

---

### Post by turbojugend_gr on 2006-06-27
I repeated ps=ef as thunderbird poped up in about 15 mis ths time.Here is the output:

```
turbojugend@TurboPC:~$ ps -ef
UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 16:44 ?        00:00:01 init [2]
root         2     1  0 16:44 ?        00:00:00 [migration/0]
root         3     1  0 16:44 ?        00:00:00 [ksoftirqd/0]
root         4     1  0 16:44 ?        00:00:00 [watchdog/0]
root         5     1  0 16:44 ?        00:00:00 [migration/1]
root         6     1  0 16:44 ?        00:00:00 [ksoftirqd/1]
root         7     1  0 16:44 ?        00:00:00 [watchdog/1]
root         8     1  0 16:44 ?        00:00:00 [events/0]
root         9     1  0 16:44 ?        00:00:00 [events/1]
root        10     1  0 16:44 ?        00:00:00 [khelper]
root        11     1  0 16:44 ?        00:00:00 [kthread]
root        14    11  0 16:44 ?        00:00:00 [kblockd/0]
root        15    11  0 16:44 ?        00:00:00 [kblockd/1]
root        16    11  0 16:44 ?        00:00:00 [kacpid]
root       177    11  0 16:44 ?        00:00:00 [pdflush]
root       178    11  0 16:44 ?        00:00:00 [pdflush]
root       180    11  0 16:44 ?        00:00:00 [aio/0]
root       181    11  0 16:44 ?        00:00:00 [aio/1]
root       179     1  0 16:44 ?        00:00:00 [kswapd0]
root       777    11  0 16:44 ?        00:00:00 [kseriod]
root       861     1  0 16:44 ?        00:00:00 [kirqd]
root      1821    11  0 16:44 ?        00:00:00 [ata/0]
root      1822    11  0 16:44 ?        00:00:00 [ata/1]
root      1823    11  0 16:44 ?        00:00:00 [ata_hotplug/0]
root      1824    11  0 16:44 ?        00:00:00 [ata_hotplug/1]
root      1829    11  0 16:44 ?        00:00:00 [scsi_eh_0]
root      1830    11  0 16:44 ?        00:00:00 [scsi_eh_1]
root      1834    11  0 16:44 ?        00:00:00 [scsi_eh_2]
root      1835    11  0 16:44 ?        00:00:00 [scsi_eh_3]
root      2024    11  0 16:44 ?        00:00:00 [khubd]
root      2036     1  0 16:44 ?        00:00:00 [khpsbpkt]
root      2055     1  0 16:44 ?        00:00:00 [knodemgrd_0]
root      2143     1  0 16:44 ?        00:00:00 [kjournald]
root      2385     1  0 16:44 ?        00:00:00 /sbin/udevd --daemon
root      3317     1  0 16:44 ?        00:00:00 [shpchpd_event]
root      3376    11  0 16:44 ?        00:00:00 [kgameportd]
root      3815     1  0 16:45 ?        00:00:00 [kjournald]
root      4275     1  0 16:45 ?        00:00:00 /usr/sbin/acpid -c /etc/acpi/everoot      4411     1  0 16:45 ?        00:00:00 /bin/dd bs 1 if /proc/kmsg of /vklog      4413     1  0 16:45 ?        00:00:00 /sbin/klogd -P /var/run/klogd/kmroot      4732     1  0 16:45 ?        00:00:00 /usr/sbin/gdm
root      4743  4732  0 16:45 ?        00:00:00 /usr/sbin/gdm
root      4762  4743  1 16:45 ?        00:00:49 /usr/bin/Xgl :0 :0 -fullscreen -hplip     4771     1  0 16:45 ?        00:00:00 /usr/sbin/hpiod
root      4773  4762  0 16:45 tty7     00:00:02 /usr/bin/Xorg vt7 -auth /tmp/.Xghplip     4775     1  0 16:45 ?        00:00:00 python /usr/sbin/hpssd
104       4855     1  0 16:45 ?        00:00:00 /usr/bin/dbus-daemon --system
108       4870     1  0 16:45 ?        00:00:00 /usr/sbin/hald
root      4871  4870  0 16:45 ?        00:00:00 hald-runner
108       4876  4871  0 16:45 ?        00:00:00 /usr/lib/hal/hald-addon-acpi
108       4926  4871  0 16:45 ?        00:00:00 /usr/lib/hal/hald-addon-keyboard108       4936  4871  0 16:45 ?        00:00:00 /usr/lib/hal/hald-addon-storage
108       4937  4871  0 16:45 ?        00:00:00 /usr/lib/hal/hald-addon-storage
108       4939  4871  0 16:45 ?        00:00:00 /usr/lib/hal/hald-addon-storage
108       4940  4871  0 16:45 ?        00:00:00 /usr/lib/hal/hald-addon-storage
root      5024     1  0 16:45 ?        00:00:00 hcid: processing events
root      5028     1  0 16:45 ?        00:00:00 /usr/sbin/sdpd
root      5048     1  0 16:45 ?        00:00:00 [krfcommd]
root      5062     1  0 16:45 ?        00:00:00 /sbin/mdadm -F -i /var/run/mdadmdaemon    5096     1  0 16:45 ?        00:00:00 /usr/sbin/atd
root      5109     1  0 16:45 ?        00:00:00 /usr/sbin/cron
root      5204     1  0 16:45 tty1     00:00:00 /sbin/getty 38400 tty1
root      5206     1  0 16:45 tty2     00:00:00 /sbin/getty 38400 tty2
root      5207     1  0 16:45 tty3     00:00:00 /sbin/getty 38400 tty3
root      5208     1  0 16:45 tty4     00:00:00 /sbin/getty 38400 tty4
root      5209     1  0 16:45 tty5     00:00:00 /sbin/getty 38400 tty5
root      5210     1  0 16:45 tty6     00:00:00 /sbin/getty 38400 tty6
1000      5221  4743  0 16:49 ?        00:00:00 /usr/bin/gnome-session
1000      5264  5221  0 16:49 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/dbus1000      5267     1  0 16:49 ?        00:00:00 /usr/bin/dbus-launch --exit-with1000      5268     1  0 16:49 ?        00:00:00 dbus-daemon --fork --print-pid 81000      5270     1  0 16:49 ?        00:00:00 /usr/lib/libgconf2-4/gconfd-2 5
1000      5273     1  0 16:49 ?        00:00:00 /usr/bin/gnome-keyring-daemon
1000      5275     1  0 16:49 ?        00:00:00 /usr/lib/bonobo-activation/bonob1000      5277     1  0 16:49 ?        00:00:00 /usr/lib/control-center/gnome-se1000      5279     1  0 16:49 ?        00:00:00 /usr/bin/esd -terminate -nobeeps1000      5297     1  0 16:49 ?        00:00:04 gnome-panel --sm-client-id defau1000      5299     1  0 16:49 ?        00:00:01 nautilus --no-default-window --s1000      5302     1  0 16:49 ?        00:00:00 gnome-volume-manager --sm-client1000      5308     1  0 16:49 ?        00:00:01 gaim
1000      5310     1  0 16:49 ?        00:00:00 update-notifier
1000      5313     1  0 16:49 ?        00:00:00 /usr/lib/gnome-vfs-2.0/gnome-vfs1000      5315     1  0 16:49 ?        00:00:00 mono /usr/lib/tomboy/Tomboy.exe
1000      5329     1  0 16:49 ?        00:00:00 beagled --debug /usr/lib/beagle/1000      5335     1  0 16:49 ?        00:00:02 gnome-cups-icon --sm-client-id d1000      5348     1  0 16:49 ?        00:00:00 /usr/lib/gamin/gam_server
1000      5352     1  2 16:49 ?        00:00:51 python /usr/lib/gdesklets/gdeskl1000      5353     1  0 16:49 ?        00:00:00 gnome-power-manager
1000      5361     1  0 16:49 ?        00:00:00 /usr/lib/nautilus-cd-burner/mapp1000      5375     1  0 16:49 ?        00:00:00 /usr/lib/gnome-applets/gnome-key1000      5377     1  0 16:49 ?        00:00:00 /usr/lib/gnome-applets/mixer_app1000      5401     1  0 16:49 ?        00:00:00 gnome-screensaver
cupsys    5581     1  0 16:50 ?        00:00:00 /usr/sbin/cupsd
syslog    5715     1  0 16:52 ?        00:00:00 /sbin/syslogd -u syslog
1000      5732     1  0 16:52 ?        00:00:00 /usr/lib/notification-daemon/not1000      5957  5329  0 16:59 ?        00:00:00 beagled-helper --debug /usr/lib/1000      6046     1  0 17:01 ?        00:00:05 gnome-terminal
1000      6047  6046  0 17:01 ?        00:00:00 gnome-pty-helper
1000      6048  6046  0 17:01 pts/0    00:00:00 bash
1000      6689     1  0 17:24 ?        00:00:00 gnome-window-decorator
1000      6691     1  0 17:24 ?        00:00:01 compiz.real --replace gconf
1000      6715     1 17 17:25 ?        00:00:52 /usr/lib/firefox/firefox-bin -a
1000      6864     1  0 17:29 ?        00:00:00 /bin/sh /usr/bin/mozilla-thunder1000      6868  6864  0 17:29 ?        00:00:00 /bin/sh /usr/lib/mozilla-thunder1000      6873  6868  7 17:29 ?        00:00:01 /usr/lib/mozilla-thunderbird/moz1000      6887  6048  0 17:30 pts/0    00:00:00 ps -ef

```

---

### Post by turbojugend_gr on 2006-06-27
For the same reason here is a nearly "real time" output for top:

```
turbojugend@TurboPC:~$ top

top - 17:32:07 up 47 min,  2 users,  load average: 0.66, 0.38, 0.19
Tasks: 106 total,   1 running, 105 sleeping,   0 stopped,   0 zombie
Cpu(s):  6.8% us,  0.2% sy,  0.0% ni, 92.8% id,  0.0% wa,  0.2% hi,  0.0% si
Mem:   1034660k total,   921996k used,   112664k free,    93204k buffers
Swap:  2104504k total,        0k used,  2104504k free,   411152k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 6715 turbojug  15   0  121m  56m  21m S    9  5.6   1:11.81 firefox-bin
 6046 turbojug  15   0 42556  16m  10m S    3  1.7   0:07.20 gnome-terminal
 4762 root      15   0  147m 134m  17m S    1 13.3   0:56.87 Xgl
 5352 turbojug  15   0 86272  38m  12m S    1  3.8   0:52.76 python
    1 root      16   0  1568  532  460 S    0  0.1   0:01.14 init
    2 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0
    3 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0
    4 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1
    6 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1
    7 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1
    8 root      10  -5     0    0    0 S    0  0.0   0:00.04 events/0
    9 root      10  -5     0    0    0 S    0  0.0   0:00.02 events/1
   10 root      11  -5     0    0    0 S    0  0.0   0:00.00 khelper
   11 root      10  -5     0    0    0 S    0  0.0   0:00.00 kthread
   14 root      10  -5     0    0    0 S    0  0.0   0:00.30 kblockd/0
   15 root      10  -5     0    0    0 S    0  0.0   0:00.00 kblockd/1
   16 root      20  -5     0    0    0 S    0  0.0   0:00.00 kacpid
  177 root      20   0     0    0    0 S    0  0.0   0:00.00 pdflush
  178 root      15   0     0    0    0 S    0  0.0   0:00.00 pdflush
  180 root      11  -5     0    0    0 S    0  0.0   0:00.00 aio/0
  181 root      11  -5     0    0    0 S    0  0.0   0:00.00 aio/1
  179 root      25   0     0    0    0 S    0  0.0   0:00.00 kswapd0
  777 root      10  -5     0    0    0 S    0  0.0   0:00.01 kseriod
  861 root      15   0     0    0    0 S    0  0.0   0:00.00 kirqd
 1821 root      13  -5     0    0    0 S    0  0.0   0:00.00 ata/0
 1822 root      10  -5     0    0    0 S    0  0.0   0:00.00 ata/1
 1823 root      13  -5     0    0    0 S    0  0.0   0:00.00 ata_hotplug/0
 1824 root      13  -5     0    0    0 S    0  0.0   0:00.00 ata_hotplug/1
 1829 root      14  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_0
 1830 root      14  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_1
 1834 root      11  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_2
 1835 root      11  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_3
 2024 root      10  -5     0    0    0 S    0  0.0   0:00.00 khubd
 2036 root      15   0     0    0    0 S    0  0.0   0:00.00 khpsbpkt
 2055 root      15   0     0    0    0 S    0  0.0   0:00.00 knodemgrd_0
 2143 root      15   0     0    0    0 S    0  0.0   0:00.03 kjournald
 2385 root      13  -4  2432  900  344 S    0  0.1   0:00.18 udevd
 3317 root      20   0     0    0    0 S    0  0.0   0:00.00 shpchpd_event
 3376 root      10  -5     0    0    0 S    0  0.0   0:00.00 kgameportd
 3815 root      15   0     0    0    0 S    0  0.0   0:00.01 kjournald
 4275 root      16   0  2152 1196  644 S    0  0.1   0:00.00 acpid
 4411 root      16   0  1680  496  412 S    0  0.0   0:00.02 dd
 4413 klog      18   0  2388 1312  388 S    0  0.1   0:00.04 klogd

[1]+  Stopped                 top

```

---

### Post by marwal on 2006-06-27
How about making a script that gets the processID of the caller and set this script as your mailclient.

edit :
1000      5732     1  0 16:52 ?        00:00:00 /usr/lib/notification-daemon/not1000      5957  5329  0 16:59 ?        00:00:00 beagled-helper --debug /usr/lib/1000      5967     1  4 16:59 ?        00:00:04 /usr/lib/firefox/firefox-bin -a

looks like beagle's got something to do with it...

---

### Post by turbojugend_gr on 2006-06-27
How have you reached that conclusion? Notice the second outputs for ps -ef and for top are just a second or two after thunderbird poped up. I can't see why beagle may be responsible, please help me to clear this in my mind. Again thank you for troubling.

---

### Post by marwal on 2006-06-27
ok, 

couldn't you - as i proposed - make a catch-file :

```
touch ppid
chmod +x ppid
vim ppid
```

write

```
#!/bin/bash
echo  $PPID>>stored_ppids
```

and in System->Programs (or whatever it is in english versions) set the file ppid as the deafault mailclient?

---

### Post by turbojugend_gr on 2006-06-27
[QUOTE=marwal]ok, 

couldn't you - as i proposed - make a catch-file :

```
touch ppid
chmod +x ppid
vim ppid
```

write

```
#!/bin/bash
echo  $PPID>>stored_ppids
```

and in System->Programs (or whatever it is in english versions) set the file ppid as the deafault mailclient?[/QUOTE]


Ok, I hope you are not yelling at me...lol, I just didn't get what you suggested there.

Anyhow this would provide me with the app that is starting the mail clients, (acually the id of it I suppose)??
If so I should first write the script then chmod it?I mean I am still confused due to the order of your instructions.

Well, as I see it I should ceate a file (echo script), then I  should make it executable with chmod +x "name of the script". Then I should update the IDs in it and then make this script my default client??? I admit I am confused on that guidelines. Could you plz repost your instructions based on the above ? By that I mean use a similar way of describing things so as I can make out what you want me to do.

Anyway, if I get you plan it seems very clever and should provide me with the ID of the "guilty" app that creates this situation. Forgive me for beeing somewaht of a green user on that , but I can't make out excactly what you suggest me.
Again thank you for contributing help on this.

---

### Post by jonesy on 2006-06-27
I agree that I don't know why this would be happening but it *should* be caused by something that is running with your user id.  That being the case, I would start shutting down apps and seeing which one causes this not to happen within an hour.  I would start by disabling Beagle since it's the one I know the least about.  You can find options for it under System --> Preferences --> Search and Indexing.  Or kill it at the command line by typing: pkill beagled.  It's POSSIBLE that beagle is trying to index your email and is checking every 45 minutes for new email to index, but again, I don't know anything about beagle.

FYI: pkill sends the KILL command (signal 9) to a process with the name that you specify, in this case, beagled.  The KILL command causes a process to terminate without performing any further functions (i.e., if you have a document open it will quit without saving, etc).

If that doesn't work, then I would try turning of gDesklets for a little while, some upgrade somewhere may have introduced a new "feature" that checks for email and this may be causing your email client to get launched to check for this situation.

---

### Post by marwal on 2006-06-28
[QUOTE=turbojugend_gr]
Well, as I see it I should ceate a file (echo script), then I  should make it executable with chmod +x "name of the script". Then I should update the IDs in it and then make this script my default client??? I admit I am confused on that guidelines. Could you plz repost your instructions based on the above ? By that I mean use a similar way of describing things so as I can make out what you want me to do.
[/QUOTE]

alright, it might have been a bit confusing with the "touch" and "chmod"... it's just the way i do things - create it, make it exe, add content. But you could just aswell...

1. create a file and give it the contents from the post above (the 2 lines starting with the bash shbang
!#/bin/bash
echo $PPID>>~/stored_ppids

2. save and make it executable with chmod +x your_filename
3. make it the default e-mail program

remember i havent tried this - it's just an idea that might work.
The script should pipe parent IDs into the file "stored_ppids" in your home directory

---

### Post by turbojugend_gr on 2006-07-08
Hi everybody forgive my absence, as i was in paradise (Call me Santorini- Greek Island). As you may guess I wasn't watcing at this post. Thank you all for your interest, you may as well, from now on, consider this an active post, again.

So as for the suggestion coming from my friend "marwal"- lol I ain't that green marwal- it seems very nice, though I cant gat gnome to change the default e-mail client to this script...  :-( Anyway I am thinking of creating another script that actually runs this and thunderbird, so I can see if it actually has the desired output. As you may guess, I believe the reason for not accepting this script as an email client, has to do with the actual lack of such one.... Maybe the above trick should do it. I will infrom you.

---


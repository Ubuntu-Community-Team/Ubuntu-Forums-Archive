---
title: "Freezes after switching hard drive from another computer"
date: 2012-10-07
forum: General Help
---

### Post by pottzie on 2012-10-07
I had a computer go dead, but I had Ubuntu on it, and decided to install the hard drive in another computer. I also upgraded the system using -u dist upgrade after updating, so I'm probably using 12.10 beta. I now have a blue splash screen, if that verifies 12.10

 The screen freezes. I saw someone with a similar problem on this thread:[http://ubuntuforums.org/showthread.php?t=2065772&highlight=computer+freezes](http://ubuntuforums.org/showthread.php?t=2065772&highlight=computer+freezes)

 And I've done  sudo apt-get purge nvidia* 
 sudo dpkg-reconfigure xserver-xorg 

  without changing anything, so I went to  

sudo apt-get update
sudo apt-get purge nvidia-*
sudo apt-get install nvidia-current

sudo apt-get purge nvidia-common
#Install nouveau and remove the xorg.conf
sudo apt-get install xserver-xorg-video-nouveau
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

 And I'm still freezing. I also found something saying to use 
sudo dpkg-reconfigure -phigh xserver-xorg
  and did that. Still freezes. I'm posting this from another computer, so I can't copy directly from the terminal to show what I get, but I can at least open a terminal by using <ctrl><alt>F1, so I can run commands that way.

 I did have it work long enough to see what the Nvidea applet showed, and it shows as using an Nvidea Gforce 6000.  lspci also shows that I have Nvidea GE Force 6000 rev a2.  And This is a 64 bit system.

---

### Post by TheFu on 2012-10-07
Is it just the X/Server that locks up or the entire kernel?  
Can you ssh into the machine from the alternate computer?  Then you could post and see the exact error messages from dmesg and /var/log/syslog and /var/log/Xorg.0.log

I though nvidia changed from unified drivers recently. Now you need to use specific drivers based on the actual card installed.

---

### Post by pottzie on 2012-10-07
Don't know, good question. I'll start looking into what I have to do to ssh into Ubuntu. Seems like I remember having to run some authentication on the computer I'm going to ssh into to let it know to accept the ssh shell. It's been a while, and I've only done it a few times, and not recently.

Edit: Got ssh working, now to make it freeze and see what happens next!

---

### Post by pottzie on 2012-10-07
Good call! The system froze, I tried running a command from the client, and nothing, no letters in the terminal as I was typing from the client. Locked up tighter than the parson's daughter.

---

### Post by TheFu on 2012-10-07
> **TheFu said:**
> Then you could post and see the exact error messages from dmesg and /var/log/syslog and /var/log/Xorg.0.log

Without that data, you are on your own.

---

### Post by pottzie on 2012-10-07
Well, that's the kicker. When it freezes, all I can do is shut the computer off and reboot. There's nothing I can do via the terminal once it locks up. I can get dmesg after the restart, but I think that just shows what went on during the restart, and nothing from the lock-up.

 Here's a pastebin of dmesg, as it's huge.
[http://pastebin.com/ArAwYZHc](http://pastebin.com/ArAwYZHc)

 I'm trying to get /var/log/syslog and /var/log/Xorg.0.log, but when I enter those terms (I just put "/var/,"etc in the terminal, maybe it expects another command) it says "permission denied." I'm doing this from the ssh session, maybe it would work from the computer I'm having the problem with.

---

### Post by pottzie on 2012-10-07
Just came across a bug report about kernel freezing system. 
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/993187](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/993187)

 Says that installing kernel 3.3.6 solves it. How can I install the newer kernel?

---

### Post by TheFu on 2012-10-07
> **pottzie said:**
> Well, that's the kicker. When it freezes, all I can do is shut the computer off and reboot. There's nothing I can do via the terminal once it locks up. I can get dmesg after the restart, but I think that just shows what went on during the restart, and nothing from the lock-up.

 Here's a pastebin of dmesg, as it's huge.
[http://pastebin.com/ArAwYZHc](http://pastebin.com/ArAwYZHc)

 I'm trying to get /var/log/syslog and /var/log/Xorg.0.log, but when I enter those terms (I just put "/var/,"etc in the terminal, maybe it expects another command) it says "permission denied." I'm doing this from the ssh session, maybe it would work from the computer I'm having the problem with.

Permissions do not change between ssh and other login methods. This isn't Windows.

ssh into the machine, then watch all the log files in different terminals.  The log directories are protected, so you'll need to either use root or sudo.
$ sudo tail -f  /var/log/syslog 
and 
$ sudo tail -f  /var/log/Xorg.0.log
and
$ sudo tail -f  /var/log/messages

When the machine locks up, the last few lines in those files will be helpful.

---

### Post by pottzie on 2012-10-07
(a) "ssh into the machine"- got that all ready and it's set to go.

(b)"then watch all the log files in different terminals." - Huh? Whaa? How do I get different terminals set up under ssh?

 And did you see the question on getting the newer kernel?

---

### Post by pottzie on 2012-10-07
I see that I can open separate tabs in the host computer, and I've opened three. I've also ssh'd into the host. But when the system freezes, how am I supposed to get the log files? It seems from your post that I can somehow start the log files, then somehow after the system freezes, go back and view them. But from what I've seen, when the computer locks up, there's no way to do anything on the host, even though I'm ssh'd into it. That's the "freeze," there's nothing that works, including any input from the remote client. I can't type into the frozen terminal to change screens or check logs.

---

### Post by pottzie on 2012-10-07
I just grabbed the log files, and here's a pastebin-but these are probably logs from the rebooted, still working system. I don't think there is anything that helps show what's happening when it freezes.
[http://pastebin.com/6RY5ttCG](http://pastebin.com/6RY5ttCG)

---

### Post by TheFu on 2012-10-08
You need to use 3 different terminals - not tabs.
You need to have all 3 seen **before** the remote system locks up.

The **tail -f** command shows the last log entries as they happen. You should see the last things happening on the remote machine, just before it locks up.

I don't have a clue about the kernel. I'm much more inclined to think it is a buggy GPU driver causing the lockup than anything else, though weird hardware or hardware issues could also be causing it.  Without the data from those log files, you and I are just guessing. Guess are like .... ... well, they are worthless.

To get the latest, tested software, which is a good idea for almost everyone, I run 2 commands every week (usually on Saturday mornings).
[B]$ sudo apt-get update
$ sudo apt-get dist-upgrade
[/B]
Don't worry - the dist-upgrade won't upgrade the distro, but it will update the kernel and any packages dependent on the newer kernel, if one exists.  This is the same as whatever GUI method exists ... most of my systems don't have a GUI installed (or a monitor or keyboard or mouse), so ssh is the only interface available that isn't a hassle.  BTW, using ssh is how all the remote Linux servers around the world are managed.  When you have 1 machine, point-n-click seems easier, but when you have 5 or 100 or 10,000, there isn't enough time in the day to point-n-click. ssh can be scripted, automated, reproducible.

It is probably a bad idea to install any software that isn't part of the normal Ubuntu distro repositories for 99.9999% of us.  There are a number of reasons for this.  I used to build my own kernels, install them, fight dependency issues with lots of other programs, and deal with many other hassles. Eventually - sometimes immediately, the package manager would stop being able to do what it needed to keep everything working together. Dependencies would be totally screwed. The only answer was to install the OS from scratch.  

**The short answer is to always use the package manager for software installs, updates, and removal.**

---

### Post by pottzie on 2012-10-08
Finally figured out that I needed to open multiple terminals in the client computer and ssh in with each one. Sorry, new teritory for me. tail -f /var/log/messages wasn't there, according to bash. I intended to use Pastebin to post the code, os as not to clog up Ubuntu's servers, but Pastebin is down now, so I'm afraid I'll have to post the code here. Sorry.

I think this is  tail -f /var/log/syslog 

```

Stage 4 of 5 (IPv6 Configure Timeout) complete.
Oct  8 21:52:53 larry-Dell-DXP051 anacron[1047]: Job `cron.daily' started
Oct  8 21:52:54 larry-Dell-DXP051 anacron[3007]: Updated timestamp for job `cron.daily' to 2012-10-08
Oct  8 21:52:57 larry-Dell-DXP051 anacron[1047]: Job `cron.daily' terminated (exit status: 1) (mailing output)
Oct  8 21:52:57 larry-Dell-DXP051 anacron[1047]: Tried to mail output of job `cron.daily', but mailer process (/usr/sbin/sendmail) exited with ststus 255
Oct  8 21:52:57 larry-Dell-DXP051 anacron[1047]: Normal exit (1 job run)
Oct  8 21:56:21 larry-Dell-DXP051 acpid: client 1089[0:0] has disconnected
Oct  8 21:56:21 larry-Dell-DXP051 acpid: client 1089[0:0] has disconnected
Oct  8 21:56:21 larry-Dell-DXP051 acpid: client connected from 1089[0:0]
Oct  8 21:56:21 larry-Dell-DXP051 acpid: 1 client rule loaded
Oct  8 21:56:22 larry-Dell-DXP051 acpid: client connected from 1089[0:0]
Oct  8 21:56:22 larry-Dell-DXP051 acpid: 1 client rule loaded
Oct  8 21:56:41 larry-Dell-DXP051 kernel: [  553.970807] audit_printk_skb: 36 callbacks suppressed
Oct  8 21:56:41 larry-Dell-DXP051 kernel: [  553.970818] type=1701 audit(1349747801.109:24): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=3403 comm="chrome" reason="seccomp" sig=0 syscall=39 compat=0 ip=0x7f4535a9ffd9 code=0x50001
Oct  8 21:57:39 larry-Dell-DXP051 kernel: [  612.390773] type=1701 audit(1349747859.528:25): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=3506 comm="chrome" reason="seccomp" sig=0 syscall=39 compat=0 ip=0x7f0c69081fd9 code=0x50001


```

 And this is tail -f /var/log/Xorg.0.log
```

[    29.859] (**) ImPS/2 Logitech Wheel Mouse: (accel) keeping acceleration scheme 1
[    29.859] (**) ImPS/2 Logitech Wheel Mouse: (accel) acceleration profile 0
[    29.859] (**) ImPS/2 Logitech Wheel Mouse: (accel) acceleration factor: 2.000
[    29.859] (**) ImPS/2 Logitech Wheel Mouse: (accel) acceleration threshold: 4
[    29.859] (II) config/udev: Adding input device ImPS/2 Logitech Wheel Mouse (/dev/input/mouse0)
[    29.859] (II) No input driver specified, ignoring this device.
[    29.859] (II) This device may have been added with another device file.
[    33.512] (II) NVIDIA(0): Setting mode "1280x1024_75"
[    34.704] (II) XKB: reuse xkmfile /var/lib/xkb/server-03AF3717FF3AB439A4BAABA686CCB40771CDF520.xkm
[    45.848] (II) XKB: reuse xkmfile /var/lib/xkb/server-03AF3717FF3AB439A4BAABA686CCB40771CDF520.xkm
[   534.300] (II) Open ACPI successful (/var/run/acpid.socket)
[   534.883] (II) NVIDIA(0): Setting mode "1280x1024_75"


```

---


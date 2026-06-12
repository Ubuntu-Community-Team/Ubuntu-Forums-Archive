---
title: "TFTP will not start (command returns a &quot;rejected send message&quot;)"
date: 2010-05-14
forum: General Help
---

### Post by Caislean on 2010-05-14
I've setup DHCP and a DRBL server on my box running Lucid, and everything is working fine except TFTP.

TFTP is configured, but when I try to start it with:
> service tftpd-hpa start

The following is returned:
> start: Rejected send message, 1 matched rules; type="method_call", sender=":1.96" (uid=1000 pid=24555" comm="start") interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart (uid=0 pid=1 comm="/sbin/init"))

Any ideas of what might be causing this or where I should start looking?

netstat -a | grep tftp returns nothing at the moment.

Thanks in advance.

---

### Post by Caislean on 2010-05-17
Anyone have ideas about this? I would really like to get this to work, and thus far I can't turn up any solid information on it.

---

### Post by Caislean on 2010-05-18
Alright, I'll update this for other people learning their way through DRBL and 10.04.

First, the stable version of DRBL at the moment doesn't work for 10.04, so you need to use the unstable version. However, I had success using the stable version, but I had to tweak some things.

1.) The error I originally posted here comes from not putting "sudo" before the command. I can't believe I missed that earlier.

2.) If you're really intent on getting tftp-hpa to work, use the synaptic package manager and search for tftp. If tftp or tftpd are installed, mark them for COMPLETE uninstallation. Do this for tftpd-hpa and tftp-hpa as well.

3.) After completely uninstalling tftpd-hpa in step 2, have synaptic package manager add them back in.

4.) Also, make a backup copy of the /etc/default/tftpd-hpa file, as DRBL is going to slaughter this file later. By slaughter, I mean mess it up and tftpd-hpa won't launch. After setting up DRBL, just put the original file back in place, and restart tftp-hpa.

5.) Install DRBL - I'll write about this some other time. But most HOW-TOs I've found are pretty accurate on this topic.

6.) Replace /etc/default/tftpd-hpa with the copy you made eariler.

7.) In /etc/default/tftpd-hpa, you'll need to change the tftp path to match DRBL. By default it places things in /tftpboot/, and you need to modify some settings in the file anyway...

In the end, your tftpd-hpa file should look similar to this:

> # /etc/default/tftpd-hpa
RUN_DAEMON="yes"
OPTIONS="-l -s -c /tftpboot/nbi_img"
TFTP_USERNAME="root"
TFTP_DIRECTORY="/tftpboot/nbi_img"
TFTP_ADDRESS="0.0.0.0:69"
TFTP_OPTIONS="--secutre"

Note: Research the options you want. For me, I needed -l, -s, and -c.
Note: I set TFTP to be root, and I also made the /tftpboot folder owned by root:root. Some guides will say to set these to nobody, but that seems to be incorrect (in my experience).

This should get you 90% of the way there. I'll post a detailed guide later that will cover using 2 nics, virtual nics, etc... but this is just a quick guide before I forget everything I've done.

---

### Post by tech603 on 2010-06-01
Thanks for the post, currently planning to set up DRBL on 10.04. Will check back for updates!

---

### Post by Mostafatherock on 2012-03-02
>  1.) The error I originally posted here comes from not putting "sudo" before the command. I can't believe I missed that earlier.

Thanks alot !! but this time thr problem was eith my smbd :)

---

### Post by nothingspecial on 2012-03-02
[IMG]http://img696.imageshack.us/img696/7058/necrov.png[/IMG]

---


---
title: "sysctl.conf is not applied at boot"
date: 2012-04-02
forum: General Help
---

### Post by Poma on 2012-04-02
What script is responsible for applying sysctl.conf at boot time? Looks like I've broken something and now have to start 'sysctl -p' manually. I have ubuntu 10.04.

---

### Post by matt_symes on 2012-04-02
Hi

> **Poma said:**
> What script is responsible for applying sysctl.conf at boot time? Looks like I've broken something and now have to start 'sysctl -p' manually. I have ubuntu 10.04.

It's the procps scripts that handle this.

```
matthew@matthew-Aspire-7540:~$ ls -l /etc/init/procps.conf
-rw-r--r-- 1 root root 363 Dec  5 11:45 /etc/init/procps.conf
matthew@matthew-Aspire-7540:~$
```

This uses the new(ish) upstart method to pass the contents to sysctrl

```
matthew@matthew-Aspire-7540:~$ cat /etc/init/procps.conf
# procps - set sysctls from /etc/sysctl.conf
#
# This task sets kernel sysctl variables from /etc/sysctl.conf and
# /etc/sysctl.d

description     "set sysctls from /etc/sysctl.conf"

instance $UPSTART_EVENTS
env UPSTART_EVENTS=

start on virtual-filesystems or static-network-up

task
script
    cat /etc/sysctl.d/*.conf /etc/sysctl.conf | sysctl -e -p -
end script
matthew@matthew-Aspire-7540:~$
```

The old systemV way just calls the upstart functionalty now.

Take a look at..

```
matthew@matthew-Aspire-7540:~$ ls -l /etc/init.d/procps
lrwxrwxrwx 1 root root 21 Jan  5 16:44 /etc/init.d/procps -> /lib/init/upstart-job
matthew@matthew-Aspire-7540:~$
```

That should give you a starting point to debug your system.

Kind regards

---

### Post by Poma on 2012-04-02
I have everything like you said, everything seems fine. Except procps link is not present in /etc/rc2.d. Does it need to be here?

---

### Post by matt_symes on 2012-04-02
Hi

> Except procps link is not present in /etc/rc2.d. Does it need to be here?

It appears not

```
matthew@matthew-Aspire-7540:~$ ls /etc/rc?.d/
/etc/rc0.d/:
K01timidity             K20atop  K20postfix            K20vnstat  S20sendsigs  S31umountnfs.sh  S40umountfs    S59cryptdisks-early  S90halt
K10unattended-upgrades  K20ntop  K20speech-dispatcher  README     S30urandom   S35networking    S48cryptdisks  S60umountroot

/etc/rc1.d/:
K01timidity    K20acpi-support  K20kerneloops  K20postfix  K20smartmontools      K20vnstat  S30killprocs  S70pppd-dns
K15pulseaudio  K20atop          K20ntop        K20saned    K20speech-dispatcher  README     S70dns-clean  S90single

/etc/rc2.d/:
README   S20kerneloops  S20postfix        S20speech-dispatcher  S20vnstat      S50rsync  S70dns-clean  S75sudo          S99grub-common  S99rc.local
S20atop  S20ntop        S20smartmontools  S20sysstat            S50pulseaudio  S50saned  S70pppd-dns   S99acpi-support  S99ondemand     S99timidity

/etc/rc3.d/:
README   S20kerneloops  S20postfix        S20speech-dispatcher  S20vnstat      S50rsync  S70dns-clean  S75sudo          S99grub-common  S99rc.local
S20atop  S20ntop        S20smartmontools  S20sysstat            S50pulseaudio  S50saned  S70pppd-dns   S99acpi-support  S99ondemand     S99timidity

/etc/rc4.d/:
README   S20kerneloops  S20postfix        S20speech-dispatcher  S20vnstat      S50rsync  S70dns-clean  S75sudo          S99grub-common  S99rc.local
S20atop  S20ntop        S20smartmontools  S20sysstat            S50pulseaudio  S50saned  S70pppd-dns   S99acpi-support  S99ondemand     S99timidity

/etc/rc5.d/:
README   S20kerneloops  S20postfix        S20speech-dispatcher  S20vnstat      S50rsync  S70dns-clean  S75sudo          S99grub-common  S99rc.local
S20atop  S20ntop        S20smartmontools  S20sysstat            S50pulseaudio  S50saned  S70pppd-dns   S99acpi-support  S99ondemand     S99timidity

/etc/rc6.d/:
K01timidity             K20atop  K20postfix            K20vnstat  S20sendsigs  S31umountnfs.sh  S40umountfs    S59cryptdisks-early  S90reboot
K10unattended-upgrades  K20ntop  K20speech-dispatcher  README     S30urandom   S35networking    S48cryptdisks  S60umountroot

/etc/rcS.d/:
README  S25brltty  S37apparmor  S47lm-sensors  S55urandom  S70x11-common  S75schroot
matthew@matthew-Aspire-7540:~$ 
```

Have you checked the permissions and ownership of the init script in /etc/init ?

Open a terminal and run this command

```
cat /etc/sysctl.d/*.conf /etc/sysctl.conf | sysctl -e -p -
```

Are there any errors ? 

What do you have in the folder /etc/sysctl.d/ ?

```
matthew@matthew-Aspire-7540:~$ ls /etc/sysctl.d/ -l
total 28
-rw-r--r-- 1 root root   77 Dec 12 17:42 10-console-messages.conf
-rw-r--r-- 1 root root  490 Dec 12 17:42 10-ipv6-privacy.conf
-rw-r--r-- 1 root root  726 Dec 12 17:42 10-kernel-hardening.conf
-rw-r--r-- 1 root root  509 Dec 12 17:42 10-network-security.conf
-rw-r--r-- 1 root root 1292 Dec 12 17:42 10-ptrace.conf
-rw-r--r-- 1 root root  506 Dec 12 17:42 10-zeropage.conf
-rw-r--r-- 1 root root  519 Dec 12 17:42 README
matthew@matthew-Aspire-7540:~$
```

Kind regards

---


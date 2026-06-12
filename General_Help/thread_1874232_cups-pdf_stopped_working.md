---
title: "cups-pdf stopped working"
date: 2011-11-02
forum: General Help
---

### Post by calande on 2011-11-02
Hello,

I upgraded to 11.10 and now when I want to print to PDF (ie. from MS Word), nothing happens. I reinstalled cups-pdf, but it still doesn't work. Nothing happens, even after setting ~/PDF to 777 for all users. Any idea?
Thanks,

---

### Post by searchfgold6789 on 2011-11-02
MS Word???? You mean on WINE, right?
First of all, that's going to have it's own .pdf export feature depending on which version you get. Secondly, correct me if I'm wrong, but I think WINE does not support printing yet.

Try doing it from a linux program.

---

### Post by calande on 2011-11-03
Yes, it used to work. WINE does print properly, actually until the latest upgrade to 11.10. If I try from gedit, it doesn't work either. Any idea? Thanks.

---

### Post by lykwydchykyn on 2011-11-03
Does the PDF printer appear in your list of printers, or is it missing entirely?

Debugging cups can get tricky, but here's a good place to start:

- edit /etc/cups/cupsd.conf as root
- find the "loglevel" directive and set it to "debug"
- restart cups (sudo service cupsd restart)
- try to print a pdf
- post /var/log/cups/error_log here

---

### Post by calande on 2011-11-05
Hello, thank you! Here's the output: ```
sudo service cupsd restart
[sudo] password for calande: 
cupsd: unrecognized service
```
Yes, I have a "PDF" printer in my list of printers installed. Any idea what is wrong with CUPS? Thanks,

---

### Post by lykwydchykyn on 2011-11-05
Try "sudo service cups restart" then.  It's different between debian and ubuntu, sometimes I get them mixed up.

---

### Post by calande on 2011-11-05
Thanks, this worked and didn't return any error. However, when I try to print a test page from cups-pdf, nothing happens, no error message, but no pdf file... Any idea?

---

### Post by lykwydchykyn on 2011-11-05
> **calande said:**
> Thanks, this worked and didn't return any error. However, when I try to print a test page from cups-pdf, nothing happens, no error message, but no pdf file... Any idea?

What I posted was not suggested as a fix, but as a way to enable more robust debugging messages.  

You need to examine the error log I mentioned, and see if you can identify where things are going wrong.  If you're not sure, post it here, using code tags.

---

### Post by calande on 2011-11-06
Thanks. I had a look at the log file but didn't understand very well. I simulated a print test page and here's the attached latest version. Do you know what is wrong with my CUPS? Thanks.

---

### Post by lykwydchykyn on 2011-11-06
Looking through the error I found this:

```

cups-pdf cannot be called without root privileges!

```

This seems to be the source of the problem, I'm guessing.  If you do:
```

ps -aux |grep cups

```

Does it show that cups is running as root?

It could also be that apparmor is interfering.  Can you post /etc/apparmor.d/usr.sbin.cupsd?

---

### Post by calande on 2011-11-06
It seems it's run as root:

```
$ ps aux | grep cups
root      1181  0.0  0.1   7528  3064 ?        Ss   08:33   0:00 /usr/sbin/cupsd -F
lp        3768  0.0  0.0   5672  1332 ?        S    14:40   0:00 /usr/lib/cups/notifier/dbus dbus:// 
charles   4991  0.0  0.0   4192   784 pts/0    S+   22:26   0:00 grep --color=auto cups
$
```
What else can you think of? Thanks,

---

### Post by lykwydchykyn on 2011-11-06
> **calande said:**
> It seems it's run as root:

```
$ ps aux | grep cups
root      1181  0.0  0.1   7528  3064 ?        Ss   08:33   0:00 /usr/sbin/cupsd -F
lp        3768  0.0  0.0   5672  1332 ?        S    14:40   0:00 /usr/lib/cups/notifier/dbus dbus:// 
charles   4991  0.0  0.0   4192   784 pts/0    S+   22:26   0:00 grep --color=auto cups
$
```
What else can you think of? Thanks,

Did you see my note about apparmor?

---

### Post by calande on 2011-11-06
Sorry, I missed that one, there you go:

```
# vim:syntax=apparmor
# Last Modified: Thu Aug  2 12:54:46 2007
# Author: Martin Pitt <martin.pitt@ubuntu.com>

#include <tunables/global>

/usr/sbin/cupsd flags=(complain) {
  #include <abstractions/base>
  #include <abstractions/bash>
  #include <abstractions/authentication>
  #include <abstractions/dbus>
  #include <abstractions/fonts>
  #include <abstractions/nameservice>
  #include <abstractions/perl>
  #include <abstractions/user-tmp>

  capability chown,
  capability fowner,
  capability fsetid,
  capability kill,
  capability net_bind_service,
  capability setgid,
  capability setuid,

  # nasty, but we limit file access pretty tightly, and cups chowns a
  # lot of files to 'lp' which it cannot read/write afterwards any
  # more
  capability dac_override,

  # the bluetooth backend needs this
  network bluetooth,

  # the dnssd backend uses those
  network x25 seqpacket,
  network ax25 dgram,
  network netrom seqpacket,
  network rose dgram,
  network ipx dgram,
  network appletalk dgram,
  network econet dgram,
  network ash dgram,

  /bin/bash ixr,
  /bin/dash ixr,
  /bin/hostname ixr,
  /dev/lp* rw,
  deny /dev/tty rw,  # silence noise
  /dev/ttyS* rw,
  /dev/ttyUSB* rw,
  /dev/usb/lp* rw,
  /dev/bus/usb/ r,
  /dev/bus/usb/** rw,
  /dev/parport* rw,
  /etc/cups/ rw,
  /etc/cups/** rw,
  /etc/foomatic/* r,
  /etc/gai.conf r,
  /etc/papersize r,
  /etc/pnm2ppa.conf r,
  /etc/printcap rwl,
  /etc/ssl/** r,
  @{PROC}/net/ r,
  @{PROC}/net/* r,
  @{PROC}/sys/dev/parport/** r,
  @{PROC}/*/net/ r,
  @{PROC}/*/net/** r,
  @{PROC}/sys/crypto/** r,
  /sys/** r,
  /usr/bin/* ixr,
  /usr/sbin/* ixr,
  /bin/* ixr,
  /sbin/* ixr,
  /usr/lib/** rm,

  # backends which come with CUPS can be confined
  /usr/lib/cups/backend/bluetooth ixr,
  /usr/lib/cups/backend/dnssd ixr,
  /usr/lib/cups/backend/http ixr,
  /usr/lib/cups/backend/ipp ixr,
  /usr/lib/cups/backend/lpd ixr,
  /usr/lib/cups/backend/parallel ixr,
  /usr/lib/cups/backend/serial ixr,
  /usr/lib/cups/backend/snmp ixr,
  /usr/lib/cups/backend/socket ixr,
  /usr/lib/cups/backend/usb ixr,
  # we treat cups-pdf specially, since it needs to write into /home
  # and thus needs extra paranoia
  /usr/lib/cups/backend/cups-pdf Px,
  # third party backends get no restrictions as they often need high
  # privileges and this is beyond our control
  /usr/lib/cups/backend/* Ux,

  /usr/lib/cups/cgi-bin/* ixr,
  /usr/lib/cups/daemon/* ixr,
  /usr/lib/cups/monitor/* ixr,
  /usr/lib/cups/notifier/* ixr,
  # filters and drivers (PPD generators) are always run as non-root,
  # and there are a lot of third-party drivers which we cannot predict
  /usr/lib/cups/filter/** Uxr, 
  /usr/lib/cups/driver/* Uxr,
  /usr/local/** rm,
  /usr/local/lib/cups/** rix,
  /usr/share/** r,
  /{,var/}run/** rm,
  /{,var/}run/avahi-daemon/socket rw,
  deny /{,var/}run/samba/ rw,
  /{,var/}run/samba/** rw,
  /{,var/}run/cups/ rw,
  /{,var/}run/cups/** rw,
  /var/cache/cups/ rw,
  /var/cache/cups/** rwk,
  /var/log/cups/ rw,
  /var/log/cups/* rw,
  /var/spool/cups/ rw,
  /var/spool/cups/** rw,

  # third-party printer drivers; no known structure here
  /opt/** rix,

  # FIXME: no policy ATM for hplip and Brother drivers
  /usr/bin/hpijs Ux,
  /usr/Brother/** Ux,

  # Kerberos authentication
  /etc/krb5.conf r,
  deny /etc/krb5.conf w,
  /etc/krb5.keytab rk,
  /etc/cups/krb5.keytab rwk,
  /tmp/krb5cc* k,

  # likewise authentication
  /etc/likewise r,
  /etc/likewise/* r,

  # Site-specific additions and overrides. See local/README for details.
  #include <local/usr.sbin.cupsd>
}

# separate profile since this needs to write into /home
/usr/lib/cups/backend/cups-pdf flags=(complain) {
  #include <abstractions/base>
  #include <abstractions/fonts>
  #include <abstractions/nameservice>
  #include <abstractions/user-tmp>

  capability chown,
  capability fowner,
  capability fsetid,
  capability setgid,
  capability setuid,

  # unfortunate, but required for when $HOME is 700
  capability dac_override,
  capability dac_read_search,

  /bin/dash ixr,
  /bin/bash ixr,
  /bin/cp ixr,
  /etc/papersize r,
  /etc/cups/cups-pdf.conf r,
  @{HOME}/PDF/ rw,
  @{HOME}/PDF/* rw,
  /usr/bin/gs ixr,
  /usr/lib/cups/backend/cups-pdf mr,
  /usr/lib/ghostscript/** mr,
  /usr/share/** r,
  /var/log/cups/cups-pdf_log w,
  /var/spool/cups-pdf/** rw,
}
```
Hope we can spot the problem. Thanks again,

---

### Post by lykwydchykyn on 2011-11-06
I don't see a problem off-hand, but if you'll move that file into the /etc/apparmor.d/disable/  folder, then restart the system, that would at least tell you if apparmor is the actual problem or not.

---

### Post by calande on 2011-11-11
Thanks, I put that file into the disable folder, but after rebooting, I'm still unable to print to PDF :(
Any other idea?

---

### Post by calande on 2011-11-13
For some reason, it's working again after the update :)
Thanks again.

---


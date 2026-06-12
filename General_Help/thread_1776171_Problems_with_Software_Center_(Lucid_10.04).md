---
title: "Problems with Software Center (Lucid 10.04)"
date: 2011-06-05
forum: General Help
---

### Post by ummwat on 2011-06-05
Hello, I'm fairly new to Linux. I just installed Ubuntu recently. I've  recently been having problems with the Ubuntu Software Center. It will  not start up and I cannot start it from the Terminal. This is the  message it gives me (with nothing left out):
```
(process:3451): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.
Traceback (most recent call last):
  File "/usr/bin/software-center", line 78, in <module>
    from softwarecenter.app import SoftwareCenterApp
  File "/usr/share/software-center/softwarecenter/app.py", line 42, in <module>
    from view.viewswitcher import ViewSwitcher, ViewSwitcherList
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 34, in <module>
    from softwarecenter.backend.channel import SoftwareChannel
  File "/usr/share/software-center/softwarecenter/backend/__init__.py", line 19, in <module>
    from aptd import AptdaemonBackend
  File "/usr/share/software-center/softwarecenter/backend/aptd.py", line 27, in <module>
    from aptdaemon.gtkwidgets import AptMediumRequiredDialog, \
  File "/usr/lib/python2.6/dist-packages/aptdaemon/gtkwidgets.py", line 45, in <module>
    import vte
ImportError:  /usr/lib/pymodules/python2.6/gtk-2.0/vtemodule.so: undefined symbol:  vte_terminal_set_alternate_screen_scroll
```I'm running Ubuntu  10.04 (Lucid Lynx) on a PowerPC machine. I've already tried reinstalling  the software center with no luck. This all started happening after I  updated in the Update Manager. Synaptic seems to be working though.
Any help will be appreciated.

---

### Post by ummwat on 2011-06-05
Okay everytime I do something with "apt-get" in Terminal I get like fifty of these messages:
```
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "en_CA.utf8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").

```
This may or may not have something to do with it.
So... any help?

---

### Post by ummwat on 2011-06-11
Help? I really need some help here...

---

### Post by linuxinstalledfromhdd on 2011-06-11
Hmmm.. Do you remember what you were doing prior to this happening that might have made changes to your system? Did you enable something in Synaptic Package Manager? Did you add something?

---

### Post by VOT Productions on 2011-06-11
In a terminal, type sudo dpkg-reconfigure locales

---

### Post by livetobefree on 2011-06-11
hello I am also having some problems, not being able to update from synaptic,    

[B]sudo dpkg-reconfigure locales
dpkg-query: parse error, in file '/var/lib/dpkg/status' near line 7893 package 'python-egenix-mxdatetime':
 field name `bdates' must be followed by colon
/usr/sbin/dpkg-reconfigure: locales is not installed
empty@empty-zen:~$ [/B]
  


any idea what that means?

---

### Post by linuxinstalledfromhdd on 2011-06-11
> **livetobefree said:**
> hello I am also having some problems, not being able to update from synaptic,    

[B]sudo dpkg-reconfigure locales
dpkg-query: parse error, in file '/var/lib/dpkg/status' near line 7893 package 'python-egenix-mxdatetime':
 field name `bdates' must be followed by colon
/usr/sbin/dpkg-reconfigure: locales is not installed
empty@empty-zen:~$ [/B]
  


any idea what that means?

I would repost that as a "new" thread. No idea though.

---

### Post by ummwat on 2011-06-12
Yeah, before I updated some updates in the Update Manager, everything was fine.
I already tried reconfiguring locales too.

---

### Post by ummwat on 2011-06-12
Every time I run apt-get update this happens:

```
W: GPG error: http://packages.medibuntu.org lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: GPG error: http://ftp.de.debian.org squeeze Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY AED4B06F473041FA
W: Failed to fetch http://deb.opera.com/opera/dists/stable/Release.gpg  Could not resolve 'deb.opera.com'

W: Failed to fetch http://ubuntu.mirror.cambrium.nl/ubuntu/dists/lucid/main/binary-powerpc/Packages.gz  404  Not Found [IP: 217.19.16.188 80]

W: Failed to fetch http://packages.medibuntu.org/dists/lucid/free/binary-powerpc/Packages.gz  404  Not Found

W: Failed to fetch http://packages.medibuntu.org/dists/lucid/non-free/binary-powerpc/Packages.gz  404  Not Found

W: Some index files failed to download, they have been ignored, or old ones used instead.
```

And when I install using apt-get install it can't fetch any archives apparently.

---


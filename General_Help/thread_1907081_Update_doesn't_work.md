---
title: "Update doesn't work"
date: 2012-01-10
forum: General Help
---

### Post by AmadeusOK on 2012-01-10
I've been unable to update the system for several. When I run "sudo apt-get update" I get this:

```
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/

```

The system is acting so weird. And of course I cannot upgrade, I always get some kind of error message. Any suggestions? Thanks for your help.

---

### Post by spacecheck on 2012-01-10
> **AmadeusOK said:**
> I've been unable to update the system for several. When I run "sudo apt-get update" I get this:

```
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/

```The system is acting so weird. And of course I cannot upgrade, I always get some kind of error message. Any suggestions? Thanks for your help.
From the error you received, it appears you already have a package manager open. Make sure all of them are closed, then try again.

Good luck!

---

### Post by AmadeusOK on 2012-01-10
> **spacecheck said:**
> From the error you received, it appears you already have a package manager open. Make sure all of them are closed, then try again.

Good luck!

Thank you for the quick reply! Unfortunately, I closed the package manager but I still got the same error message. :(

---

### Post by pr3zident on 2012-01-10
> **AmadeusOK said:**
> Thank you for the quick reply! Unfortunately, I closed the package manager but I still got the same error message. :(

make sure its closed ```
ps -e
``` if that doesn't work log out and log back in ...

---

### Post by AmadeusOK on 2012-01-10
> **pr3zident said:**
> make sure its closed ```
ps -e
``` if that doesn't work log out and log back in ...

I did as you told me and at the end I get this:

```
 'Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)'
in the drive '/cdrom/' and press enter

```

---

### Post by spacecheck on 2012-01-10
> **AmadeusOK said:**
> I did as you told me and at the end I get this:

```
 'Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)'
in the drive '/cdrom/' and press enter

```
Looks like an update process is still active, but is seeking the cd for 9.10 in order to finish. As suggested earlier, you could log out and back in, which should close/stop the process. Then use "Software Sources"  to unmark the check boxes for that cdrom under the "Other Software" tab and close the Software Sources window. Then call up your terminal and try sudo apt-get update again.

Good luck!

---

### Post by AmadeusOK on 2012-01-10
> **spacecheck said:**
> Looks like an update process is still active, but is seeking the cd for 9.10 in order to finish. As suggested earlier, you could log out and back in, which should close/stop the process. Then use "Software Sources"  to unmark the check boxes for that cdrom under the "Other Software" tab and close the Software Sources window. Then call up your terminal and try sudo apt-get update again.

Good luck!

Thanks! :) I did the update and then I tried to upgrade using 'sudo apt-get upgrade" but after compiling for a few minutes I get this message at the end:

```
Errors were encountered while processing:
 linux-headers-2.6.35-30-generic
 linux-headers-2.6.35-31-generic
 linux-headers-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by spacecheck on 2012-01-10
It isn't clear what kernel you should be using for your version, but it seems you've upgraded your distro from 9.10 (the cited cdrom source) to 10.04. I usually kept one old kernel for a couple of weeks until sure the new one had caused no problems, then I would completely uninstall the older one.
You might want to try sudo update clean to see if the problems remain but you might also want to simply upgrade from 10.04 to 10.10, if possible.

---

### Post by AmadeusOK on 2012-01-11
Update is working. The problem is upgrade now. When I run "sudo apt-get upgrade" I get this error message

```
Setting up linux-headers-2.6.35-30-generic (2.6.35-30.61) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.35-30-generic /boot/vmlinuz-2.6.35-30-generic
 * dkms: running auto installation service for kernel 2.6.35-30-generic                                                                                                                               
 *       fglrx (8.780)...                                                                                                                                                                      [ OK ] 
run-parts: executing /etc/kernel/header_postinst.d/jme 2.6.35-30-generic /boot/vmlinuz-2.6.35-30-generic
make: Entering directory `/opt/system76/system76-driver/src/jme-1.0.5'
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-32-generic'
  CC [M]  /opt/system76/system76-driver/src/jme-1.0.5/jme.o
/opt/system76/system76-driver/src/jme-1.0.5/jme.c: In function ‘jme_set_multi’:
/opt/system76/system76-driver/src/jme-1.0.5/jme.c:2060: error: ‘struct net_device’ has no member named ‘mc_list’
/opt/system76/system76-driver/src/jme-1.0.5/jme.c:2061: error: ‘struct net_device’ has no member named ‘mc_count’
/opt/system76/system76-driver/src/jme-1.0.5/jme.c:2062: error: dereferencing pointer to incomplete type
/opt/system76/system76-driver/src/jme-1.0.5/jme.c:2064: error: dereferencing pointer to incomplete type
make[2]: *** [/opt/system76/system76-driver/src/jme-1.0.5/jme.o] Error 1
make[1]: *** [_module_/opt/system76/system76-driver/src/jme-1.0.5] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-32-generic'
make: *** [all] Error 2
make: Leaving directory `/opt/system76/system76-driver/src/jme-1.0.5'
run-parts: /etc/kernel/header_postinst.d/jme exited with return code 2
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.35-30-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.35-30-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-headers-2.6.35-31-generic (2.6.35-31.63) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.35-31-generic /boot/vmlinuz-2.6.35-31-generic
 * dkms: running auto installation service for kernel 2.6.35-31-generic                                                                                                                               
 *       fglrx (8.780)...                                                                                                                                                                      [ OK ] 
run-parts: executing /etc/kernel/header_postinst.d/jme 2.6.35-31-generic /boot/vmlinuz-2.6.35-31-generic
make: Entering directory `/opt/system76/system76-driver/src/jme-1.0.5'
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-32-generic'
  CC [M]  /opt/system76/system76-driver/src/jme-1.0.5/jme.o
/opt/system76/system76-driver/src/jme-1.0.5/jme.c: In function ‘jme_set_multi’:
/opt/system76/system76-driver/src/jme-1.0.5/jme.c:2060: error: ‘struct net_device’ has no member named ‘mc_list’
/opt/system76/system76-driver/src/jme-1.0.5/jme.c:2061: error: ‘struct net_device’ has no member named ‘mc_count’
/opt/system76/system76-driver/src/jme-1.0.5/jme.c:2062: error: dereferencing pointer to incomplete type
/opt/system76/system76-driver/src/jme-1.0.5/jme.c:2064: error: dereferencing pointer to incomplete type
make[2]: *** [/opt/system76/system76-driver/src/jme-1.0.5/jme.o] Error 1
make[1]: *** [_module_/opt/system76/system76-driver/src/jme-1.0.5] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-32-generic'
make: *** [all] Error 2
make: Leaving directory `/opt/system76/system76-driver/src/jme-1.0.5'
run-parts: /etc/kernel/header_postinst.d/jme exited with return code 2
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.35-31-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.35-31-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-headers-2.6.35-32-generic (2.6.35-32.64) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.35-32-generic /boot/vmlinuz-2.6.35-32-generic
 * dkms: running auto installation service for kernel 2.6.35-32-generic                                                                                                                               
 *       fglrx (8.780)...                                                                                                                                                                      [ OK ] 
run-parts: executing /etc/kernel/header_postinst.d/jme 2.6.35-32-generic /boot/vmlinuz-2.6.35-32-generic
make: Entering directory `/opt/system76/system76-driver/src/jme-1.0.5'
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-32-generic'
  CC [M]  /opt/system76/system76-driver/src/jme-1.0.5/jme.o
/opt/system76/system76-driver/src/jme-1.0.5/jme.c: In function ‘jme_set_multi’:
/opt/system76/system76-driver/src/jme-1.0.5/jme.c:2060: error: ‘struct net_device’ has no member named ‘mc_list’
/opt/system76/system76-driver/src/jme-1.0.5/jme.c:2061: error: ‘struct net_device’ has no member named ‘mc_count’
/opt/system76/system76-driver/src/jme-1.0.5/jme.c:2062: error: dereferencing pointer to incomplete type
/opt/system76/system76-driver/src/jme-1.0.5/jme.c:2064: error: dereferencing pointer to incomplete type
make[2]: *** [/opt/system76/system76-driver/src/jme-1.0.5/jme.o] Error 1
make[1]: *** [_module_/opt/system76/system76-driver/src/jme-1.0.5] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-32-generic'
make: *** [all] Error 2
make: Leaving directory `/opt/system76/system76-driver/src/jme-1.0.5'
run-parts: /etc/kernel/header_postinst.d/jme exited with return code 2
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.35-32-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.35-32-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.35-32-generic; however:
  Package linux-headers-2.6.35-32-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-headers-2.6.35-30-generic
 linux-headers-2.6.35-31-generic
 linux-headers-2.6.35-32-generic
 linux-headers-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

What should I do?

---

### Post by bluexrider on 2012-01-11
If you are trying to update 9.10 I doubt seriously its going to happen because it has reached its END OF LIFE as of April 2011.

If you have confusing issues its due to the fact of no support.

Time to upgrade.

---

### Post by AmadeusOK on 2012-01-11
> **bluexrider said:**
> If you are trying to update 9.10 I doubt seriously its going to happen because it has reached its END OF LIFE as of April 2011.

If you have confusing issues its due to the fact of no support.

Time to upgrade.

You're right. I think the time to upgrade has arrived. I'll do so within the next few days. Thanks.

---

### Post by bluexrider on 2012-01-11
Please make a note that UPDATES and UPGRADES are different than fresh INSTALLS. 

I would recommend a fresh install. Please make sure you back up all important data then proceed with a new install.

If you have any questions before proceeding please let us know.

---


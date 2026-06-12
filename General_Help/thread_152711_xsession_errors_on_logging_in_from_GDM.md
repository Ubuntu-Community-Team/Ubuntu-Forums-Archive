---
title: "xsession errors on logging in from GDM"
date: 2006-03-30
forum: General Help
---

### Post by Jeff Eklund on 2006-03-30
Hi!
I tried my best at compiling some kernels on my own and everything went fine. I compiled a 2.6.14 kernel first and then tried to compile a 2.6.16 kernel. I also patched the kernels with the corresponding ck patch. When I compiled the 2.6.16 kernel and applied the ck2 patch, things started to go wrong. The 2.6.14 kernel with the ck parch worked fine for me. Everything except my touchpad scroll-buttons worked. However, when I tried using the 2.6.16-kernel, I got into gdm and tried to login. X started to throw error messages at me, saying either
```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "jeff"
/etc/gdm/Xsession: Beginning session setup...
mkdtemp: private socket dir: No space left on device

``` or ```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "jeff"
/etc/gdm/Xsession: Beginning session setup...
mkdtemp: private socket dir: Permission denied
```.
The first error has to do with the /tmp-folder. It was filled with garbage (albeit the only two directories in the drive were .ICE-unix and .x11-unix). I rm:ed everything and did a reboot. This led to problem number two: the second error message. The permissions on /tmp had become drwxr-xr-x root root instead of drwxrwxrwxt. So I did a chmod 777 /tmp and a chmod o+t /tmp which set the permissions right. Rebbot again and exciited to see what would happen.
X now gives me the first error again! After som reboots, I noticed that the errors alternate, following set schedule. Whenever I had cleared the tmp-folder and rebboted, the permissions would be messed up. Whenever I set the permissions right and rebooted, the dir would be filled with garbage.
I'm getting nowhere. Could this be beacuse i broke some startup or shutdownscript when I compiled the last kernel?
BTW, trying to use another kernel doesn't work. I'm getting the same errors with all of the kernels I have installed.

I am in dire need of assistance. Any tips appreciated.
Thanks for your time!
Jeff

---


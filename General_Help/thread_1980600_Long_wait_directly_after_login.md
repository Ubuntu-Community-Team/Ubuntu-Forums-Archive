---
title: "Long wait directly after login"
date: 2012-05-15
forum: General Help
---

### Post by Blue-Tiger on 2012-05-15
Hi!

I'm running Xubuntu 12.04. I have a weird problem when logging in:

After I enter my password and hit enter, the computer does nothing, and just stands still for ~30 seconds. After that it begins loading my settings (xfce4-panel appears, the wallpaper changes to what I've set it to, icons etc.)

If I switch to a console using ALT+F2 before logging in through lightDM, and log in there, there is no delay. If i then switch back to LightDM and log in, there will be no delay.

Someone suggested this was due to the nVidia driver slowdown bug, but I've updated my drivers to a more recent version and the problem persists.

This is the syslog-outtake of a recent login:

```

May 15 19:43:45 335b avahi-daemon[1089]: New relevant interface eth0.IPv6 for mDNS.
May 15 19:43:45 335b avahi-daemon[1089]: Registering new address record for fe80::ca60:ff:fe87:aca7 on eth0.*.
May 15 19:43:51 335b ntpdate[2108]: step time server 91.189.94.4 offset -0.686556 sec
May 15 19:43:53 335b kernel: [   24.752009] eth0: no IPv6 routers present
May 15 19:43:54 335b lightdm: pam_ecryptfs: Passphrase file wrapped
May 15 19:44:02 335b NetworkManager[1061]: <info> (eth0): IP6 addrconf timed out or failed.
May 15 19:44:02 335b NetworkManager[1061]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
May 15 19:44:02 335b NetworkManager[1061]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
May 15 19:44:02 335b NetworkManager[1061]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
May 15 19:44:46 335b avahi-daemon[1089]: Invalid response packet from host fe80::ca2a:14ff:fe30:2b3f.
May 15 19:44:46 335b avahi-daemon[1089]: Invalid response packet from host 193.171.40.45.
May 15 19:45:11 335b kernel: [  102.083080] EXT4-fs (dm-0): mounted filesystem with ordered data mode. Opts: (null)
May 15 19:45:12 335b kernel: [  103.138289] EXT4-fs (dm-1): mounted filesystem with ordered data mode. Opts: (null)
May 15 19:45:12 335b dbus[1030]: [system] Activating service name='org.freedesktop.UDisks' (using servicehelper)
May 15 19:45:12 335b dbus[1030]: [system] Successfully activated service 'org.freedesktop.UDisks'
May 15 19:45:12 335b dbus[1030]: [system] Activating service name='org.freedesktop.RealtimeKit1' (using servicehelper)
May 15 19:45:12 335b dbus[1030]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
May 15 19:45:12 335b rtkit-daemon[2351]: Successfully called chroot.
May 15 19:45:12 335b rtkit-daemon[2351]: Successfully dropped privileges.
May 15 19:45:12 335b rtkit-daemon[2351]: Successfully limited resources.

```


If you have any idea what could cause this, please help :)

---

### Post by rai4shu2 on 2012-05-15
Could you post the output of:

```
sudo cat /var/log/lightdm/lightdm.log
```

That would be a bit more helpful, I suspect.

---

### Post by Toz on 2012-05-16
Have a look at [this]("http://ubuntuforums.org/showthread.php?t=1970326") thread. Workaround in post #15. Bug report created.

---

### Post by Blue-Tiger on 2012-05-17
@Toz: thanks, I'll look into it.

For completeness, the lightdm-log:


```

$ sudo cat /var/log/lightdm/lightdm.log
[+0.00s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.00s] DEBUG: Starting Light Display Manager 1.2.1, UID=0 PID=1228
[+0.00s] DEBUG: Loaded configuration from /etc/lightdm/lightdm.conf
[+0.00s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.00s] DEBUG: Registered seat module xlocal
[+0.00s] DEBUG: Registered seat module xremote
[+0.00s] DEBUG: Adding default seat
[+0.00s] DEBUG: Starting seat
[+0.00s] DEBUG: Starting new display for greeter
[+0.00s] DEBUG: Starting local X display
[+0.00s] DEBUG: X server :0 will replace Plymouth
[+0.03s] DEBUG: Using VT 7
[+0.03s] DEBUG: Activating VT 7
[+0.03s] DEBUG: Logging to /var/log/lightdm/x-0.log
[+0.03s] DEBUG: Writing X server authority to /var/run/lightdm/root/:0
[+0.03s] DEBUG: Launching X Server
[+0.03s] DEBUG: Launching process 1312: /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch -background none
[+0.03s] DEBUG: Waiting for ready signal from X server :0
[+0.03s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.03s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+2.02s] DEBUG: Got signal 10 from process 1312
[+2.02s] DEBUG: Got signal from X server :0
[+2.02s] DEBUG: Stopping Plymouth, X server is ready
[+2.04s] DEBUG: Connecting to XServer :0
[+2.04s] DEBUG: Starting greeter
[+2.04s] DEBUG: Started session 1731 with service 'lightdm', username 'lightdm'
[+2.09s] DEBUG: Session 1731 authentication complete with return value 0: Success
[+2.09s] DEBUG: Greeter authorized
[+2.09s] DEBUG: Logging to /var/log/lightdm/x-0-greeter.log
[+2.09s] DEBUG: Session 1731 running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/lightdm-gtk-greeter
[+2.47s] DEBUG: Greeter connected version=1.2.1
[+2.47s] DEBUG: Greeter connected, display is ready
[+2.47s] DEBUG: New display ready, switching to it
[+2.47s] DEBUG: Activating VT 7
[+2.91s] DEBUG: Greeter start authentication for tom
[+2.91s] DEBUG: Started session 2090 with service 'lightdm', username 'tom'
[+2.92s] DEBUG: Session 2090 got 1 message(s) from PAM
[+2.92s] DEBUG: Prompt greeter with 1 message(s)
[+55.38s] DEBUG: Continue authentication
[+56.29s] DEBUG: Session 2090 authentication complete with return value 0: Success
[+56.29s] DEBUG: Authenticate result for user tom: Success
[+56.30s] DEBUG: User tom authorized
[+56.30s] DEBUG: Greeter sets language en_US
[+56.32s] WARNING: Could not call SetLanguage: GDBus.Error:org.freedesktop.Accounts.Error.Failed: not access to HOME yet so language not saved
[+56.32s] DEBUG: Greeter requests session xubuntu
[+56.32s] DEBUG: Using session xubuntu
[+56.32s] DEBUG: Stopping greeter
[+56.32s] DEBUG: Session 1731: Sending SIGTERM
[+56.36s] DEBUG: Session 1731 exited with return value 0
[+56.36s] DEBUG: Greeter quit
[+81.38s] WARNING: Could not call SetXSession: Timeout was reached
[+106.41s] WARNING: Could not call FindUserByName: Timeout was reached
[+106.41s] DEBUG: Dropping privileges to uid 1000
[+106.41s] DEBUG: Restoring privileges
[+131.43s] WARNING: Could not call FindUserByName: Timeout was reached
[+131.43s] DEBUG: Dropping privileges to uid 1000
[+131.43s] DEBUG: Writing /home/tom/.dmrc
[+131.43s] DEBUG: Restoring privileges
[+131.44s] DEBUG: Starting session xubuntu as user tom
[+131.44s] DEBUG: Session 2090 running command /usr/sbin/lightdm-session startxfce4
[+133.56s] DEBUG: Registering session with bus path /org/freedesktop/DisplayManager/Session0
[+133.57s] DEBUG: Greeter closed communication channel

```

---


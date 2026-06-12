---
title: "ports closed; tried everything"
date: 2009-07-11
forum: General Help
---

### Post by gavoby on 2009-07-11
Hi I've been trying to open my ports for downloading but have not succeeded. I've tried port fowarding and changing my bit client but still no different.
The one I was using was Transmission then I tried Deluge but both were the same.
Then I tried to check what ports my Comp. was listening to, this is what I got.

gav@gav-desktop:~$ netstat -an | grep "LISTEN "
tcp 0 0 0.0.0.0:9091 0.0.0.0:* LISTEN
tcp 0 0 0.0.0.0:51532 0.0.0.0:* LISTEN
tcp 0 0 127.0.0.1:631 0.0.0.0:* LISTEN
tcp 0 0 0.0.0.0:3736 0.0.0.0:* LISTEN
tcp6 0 0 :::51532 :::* LISTEN
tcp6 0 0 ::1:631 :::* LISTEN 

Does anyone know what this means?

---

### Post by t0p on 2009-07-11
> **gavoby said:**
> Hi I've been trying to open my ports for downloading but have not succeeded. I've tried port fowarding and changing my bit client but still no different.
The one I was using was Transmission then I tried Deluge but both were the same.
Then I tried to check what ports my Comp. was listening to, this is what I got.

gav@gav-desktop:~$ netstat -an | grep "LISTEN "
tcp 0 0 0.0.0.0:9091 0.0.0.0:* LISTEN
tcp 0 0 0.0.0.0:51532 0.0.0.0:* LISTEN
tcp 0 0 127.0.0.1:631 0.0.0.0:* LISTEN
tcp 0 0 0.0.0.0:3736 0.0.0.0:* LISTEN
tcp6 0 0 :::51532 :::* LISTEN
tcp6 0 0 ::1:631 :::* LISTEN 

Does anyone know what this means?

What happens when you try to use transmission?

---

### Post by Herstjori on 2009-07-11
I am actually wanting to do the same thing Gavoboy - I don't suppose that you are a Dodo customer by any chance. I have no idea what it means at all but I tried the same thing and got:

portal@portal-desktop:~$ netstat -an|grep "LISTEN"
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
unix  2      [ ACC ]     STREAM     LISTENING     20548    /tmp/.winbindd/pipe
unix  2      [ ACC ]     STREAM     LISTENING     36304    /tmp/orbit-portal/linc-3097-0-3a9f54a62e0dc
unix  2      [ ACC ]     STREAM     LISTENING     36593    /tmp/orbit-portal/linc-3092-0-2629705737770
unix  2      [ ACC ]     STREAM     LISTENING     35103    /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     21511    /var/run/gdm_socket
unix  2      [ ACC ]     STREAM     LISTENING     36603    /tmp/.esd-1000/socket
unix  2      [ ACC ]     STREAM     LISTENING     35242    /tmp/keyring-fAayFY/socket
unix  2      [ ACC ]     STREAM     LISTENING     36646    /tmp/seahorse-UU2qXZ/S.gpg-agent
unix  2      [ ACC ]     STREAM     LISTENING     36701    /tmp/orbit-portal/linc-30a7-0-8b941799e511
unix  2      [ ACC ]     STREAM     LISTENING     35926    /tmp/ssh-XJQqv12261/agent.12261
unix  2      [ ACC ]     STREAM     LISTENING     36752    /tmp/orbit-portal/linc-30a5-0-234d4d0ba842d
unix  2      [ ACC ]     STREAM     LISTENING     36921    /tmp/orbit-portal/linc-2fd9-0-10e050095ddf3
unix  2      [ ACC ]     STREAM     LISTENING     36938    /tmp/orbit-portal/linc-30b9-0-20f1a14260822
unix  2      [ ACC ]     STREAM     LISTENING     37002    /tmp/orbit-portal/linc-30bf-0-f248a5596d49
unix  2      [ ACC ]     STREAM     LISTENING     37006    /tmp/orbit-portal/linc-30bd-0-3f05852e97052
unix  2      [ ACC ]     STREAM     LISTENING     37135    /tmp/orbit-portal/linc-30c7-0-dbddced2cbfb
unix  2      [ ACC ]     STREAM     LISTENING     37209    /tmp/orbit-portal/linc-30c8-0-1d27003255e6a
unix  2      [ ACC ]     STREAM     LISTENING     37310    /tmp/orbit-portal/linc-30c9-0-6e458c1f9e503
unix  2      [ ACC ]     STREAM     LISTENING     37378    /tmp/orbit-portal/linc-30ce-0-6465998aa9a61
unix  2      [ ACC ]     STREAM     LISTENING     36677    /tmp/.ICE-unix/12455
unix  2      [ ACC ]     STREAM     LISTENING     39355    /tmp/orbit-portal/linc-314a-0-4666849c2cd35
unix  2      [ ACC ]     STREAM     LISTENING     36606    /home/portal/.pulse/eebe770f779cbb707faa0bb6493a4e1f:runtime/native
unix  2      [ ACC ]     STREAM     LISTENING     36925    /tmp/keyring-fAayFY/socket.ssh
unix  2      [ ACC ]     STREAM     LISTENING     37635    /tmp/orbit-portal/linc-30d4-0-41b6410bc1d21
unix  2      [ ACC ]     STREAM     LISTENING     36927    /tmp/keyring-fAayFY/socket.pkcs11
unix  2      [ ACC ]     STREAM     LISTENING     37788    /tmp/orbit-portal/linc-30e0-0-d69f736d596c
unix  2      [ ACC ]     STREAM     LISTENING     38043    /tmp/orbit-portal/linc-30e6-0-199592bde20
unix  2      [ ACC ]     STREAM     LISTENING     38068    /tmp/orbit-portal/linc-30ea-0-1ad071e64d2e
unix  2      [ ACC ]     STREAM     LISTENING     38323    /tmp/orbit-portal/linc-3106-0-42d14eea57848
unix  2      [ ACC ]     STREAM     LISTENING     38348    /tmp/orbit-portal/linc-30ec-0-7377359386d40
unix  2      [ ACC ]     STREAM     LISTENING     38425    /tmp/orbit-portal/linc-3114-0-202057583914b
unix  2      [ ACC ]     STREAM     LISTENING     38553    /tmp/orbit-portal/linc-3122-0-15730e01e2dcd
unix  2      [ ACC ]     STREAM     LISTENING     38626    /tmp/orbit-portal/linc-3125-0-5c84241b58f8
unix  2      [ ACC ]     STREAM     LISTENING     38637    /tmp/orbit-portal/linc-3128-0-463df59579df
unix  2      [ ACC ]     STREAM     LISTENING     39382    /tmp/orbit-portal/linc-30db-0-21b44a7ae7133
unix  2      [ ACC ]     STREAM     LISTENING     39409    /tmp/orbit-portal/linc-30e2-0-422d3a4ebb60
unix  2      [ ACC ]     STREAM     LISTENING     39491    /tmp/orbit-portal/linc-3153-0-74f6da733efc
unix  2      [ ACC ]     STREAM     LISTENING     20550    /var/run/samba/winbindd_privileged/pipe
unix  2      [ ACC ]     STREAM     LISTENING     345411   /tmp/orbit-portal/linc-285e-0-76a5992ea9f1
unix  2      [ ACC ]     STREAM     LISTENING     21490    @/org/bluez/audio
unix  2      [ ACC ]     STREAM     LISTENING     918356   /var/run/cups/cups.sock
unix  2      [ ACC ]     STREAM     LISTENING     35102    @/tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     20341    /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     689456   /tmp/ksocket-portal/kdeinit4__0
unix  2      [ ACC ]     STREAM     LISTENING     20566    @/var/run/hald/dbus-k0OHZgd8NX
unix  2      [ ACC ]     STREAM     LISTENING     689475   /tmp/ksocket-portal/klauncherT16233.slave-socket
unix  2      [ ACC ]     STREAM     LISTENING     689504   /tmp/orbit-portal/linc-3f6b-0-4151f0f962ec
unix  2      [ ACC ]     STREAM     LISTENING     997270   /tmp/orbit-portal/linc-4098-0-2dbb447321373
unix  2      [ ACC ]     STREAM     LISTENING     690545   /tmp/orbit-portal/linc-3f8e-0-51aacfd59c89d
unix  2      [ ACC ]     STREAM     LISTENING     691010   /tmp/orbit-portal/linc-3f93-0-5da1f9b99e30f
unix  2      [ ACC ]     STREAM     LISTENING     20128    /var/run/acpid.socket
unix  2      [ ACC ]     STREAM     LISTENING     1324938  /tmp/orbit-portal/linc-4e8f-0-72b3552a6867
unix  2      [ ACC ]     STREAM     LISTENING     21428    /var/run/sdp
unix  2      [ ACC ]     STREAM     LISTENING     1318825  /tmp/orbit-portal/linc-4c38-0-9e7a64f71059
unix  2      [ ACC ]     STREAM     LISTENING     35955    @/tmp/dbus-KIeHUlepia
unix  2      [ ACC ]     STREAM     LISTENING     21724    /var/run/avahi-daemon/socket
unix  2      [ ACC ]     STREAM     LISTENING     20588    @/var/run/hald/dbus-3nWop7UNRq

---

### Post by gavoby on 2009-07-12
ok guys i've just reinstalled ubuntu and now ports are open, so i didn't really fix the problem but it's gone. sorry Herstjori not a Dodo customer.

---


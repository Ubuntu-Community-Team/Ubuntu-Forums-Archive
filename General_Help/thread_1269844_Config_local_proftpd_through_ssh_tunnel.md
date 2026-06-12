---
title: "Config local proftpd through ssh tunnel"
date: 2009-09-18
forum: General Help
---

### Post by reversed on 2009-09-18
I need some help configuring proftpd. I will be connecting to the machine with ssh and putty and thus only need it to be accessible locally on the network. Also I need to make it start on startup.

I know that changing the server type would make it start on boot, however it seems most recommend using standalone. I will be the only one connecting and will be dling/uling 500mb+ sized files if that matters on which type to use.

The only thing I have changed is User and Group to my login. As I will be the only one connecting it didn't seem like I needed to make a new user/group, or do I?

Also, I can connect directly (user@staticip) but not through the ssh tunnel. The tunnel works with vnc, but so far not ftp. I am using putty/filezilla on the client side (xp). With the tunnel running I am trying to connect to localhost. I connect and it accepts the pw. The log says 227 entering passive mode, then "Command: List" where it hangs and times out. 

```

Include /etc/proftpd/modules.conf

UseIPv6                on
IdentLookups            off

ServerName            "Debian"
ServerType            standalone
DeferWelcome            off

MultilineRFC2228        on
DefaultServer            on
ShowSymlinks            on

TimeoutNoTransfer        600
TimeoutStalled            600
TimeoutIdle            1200

DisplayLogin                    welcome.msg
DisplayChdir                   .message true
ListOptions                    "-l"

DenyFilter            \*.*/

Port                21

<IfModule mod_dynmasq.c>
</IfModule>

MaxInstances            30

User                user
Group                user

Umask                022  022
AllowOverwrite            on

TransferLog /var/log/proftpd/xferlog
SystemLog   /var/log/proftpd/proftpd.log

<IfModule mod_quotatab.c>
QuotaEngine off
</IfModule>

<IfModule mod_ratio.c>
Ratios off
</IfModule>


<IfModule mod_delay.c>
DelayEngine on
</IfModule>

<IfModule mod_ctrls.c>
ControlsEngine        off
ControlsMaxClients    2
ControlsLog           /var/log/proftpd/controls.log
ControlsInterval      5
ControlsSocket        /var/run/proftpd/proftpd.sock
</IfModule>

<IfModule mod_ctrls_admin.c>
AdminControlsEngine off
</IfModule>

```

---

### Post by reversed on 2009-09-19
Realized I needed to add passive ports to the config, but otherwise still not working.

---


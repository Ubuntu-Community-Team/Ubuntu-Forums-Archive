---
title: "likewise-open"
date: 2010-11-05
forum: General Help
---

### Post by Keamas on 2010-11-05
Hi I have a Ubuntu 10.10 System and want to join a Active Directory (Windows 2008 R2) 

But I get this error:

> [B]Error: Lsass Error [code 0x00080047]

40286 (0x9D5E) LW_ERROR_LDAP_SERVER_DOWN - Unknown error
20101105085433:ERROR:Lsass Error [CENTERROR_DOMAINJOIN_LSASS_ERROR]

40286 (0x9D5E) LW_ERROR_LDAP_SERVER_DOWN - Unknown error
[/B]

```
# domainjoin-cli --loglevel info --log . join planet-express.local Administrator
20101105085419:INFO:Domainjoin invoked with the join command (remaining arguments will be printed later):
20101105085419:INFO:    [domainjoin-cli]
20101105085419:INFO:    [--loglevel]
20101105085419:INFO:    [info]
20101105085419:INFO:    [--log]
20101105085419:INFO:    [.]
20101105085419:INFO:    [join]
20101105085419:INFO:Checking status of daemon [/etc/init.d/lwsmd]
20101105085419:INFO:Daemon [/etc/init.d/lwsmd]: status [0]
20101105085419:INFO:Checking status of daemon [/etc/init.d/lwsmd]
20101105085419:INFO:Daemon [/etc/init.d/lwsmd]: status [0]
20101105085419:INFO:Checking status of daemon [/etc/init.d/lwregd]
20101105085419:INFO:Daemon [/etc/init.d/lwregd]: status [0]
20101105085419:INFO:Checking status of daemon [/etc/init.d/lwregd]
20101105085419:INFO:Daemon [/etc/init.d/lwregd]: status [0]
20101105085419:INFO:Checking status of daemon [/etc/init.d/netlogond]
20101105085419:INFO:Daemon [/etc/init.d/netlogond]: status [0]
20101105085419:INFO:Checking status of daemon [/etc/init.d/netlogond]
20101105085419:INFO:Daemon [/etc/init.d/netlogond]: status [0]
20101105085419:INFO:Checking status of daemon [/etc/init.d/lwiod]
20101105085419:INFO:Daemon [/etc/init.d/lwiod]: status [0]
20101105085419:INFO:Checking status of daemon [/etc/init.d/lwiod]
20101105085419:INFO:Daemon [/etc/init.d/lwiod]: status [0]
20101105085419:INFO:Checking status of daemon [/etc/init.d/dcerpcd]
20101105085419:INFO:Daemon [/etc/init.d/dcerpcd]: status [0]
20101105085419:INFO:Checking status of daemon [/etc/init.d/dcerpcd]
20101105085419:INFO:Daemon [/etc/init.d/dcerpcd]: status [0]
20101105085419:INFO:Checking status of daemon [/etc/init.d/eventlogd]
20101105085419:INFO:Daemon [/etc/init.d/eventlogd]: status [0]
20101105085419:INFO:Checking status of daemon [/etc/init.d/eventlogd]
20101105085419:INFO:Daemon [/etc/init.d/eventlogd]: status [0]
20101105085419:INFO:Checking status of daemon [/etc/init.d/lsassd]
20101105085419:INFO:Daemon [/etc/init.d/lsassd]: status [0]
20101105085419:INFO:Checking status of daemon [/etc/init.d/lsassd]
20101105085419:INFO:Daemon [/etc/init.d/lsassd]: status [0]
20101105085419:INFO:Domainjoin invoked with 2 arg(s) to the join command:
20101105085419:INFO:    [planet-express.local]
20101105085419:INFO:    [Administrator]
20101105085419:INFO:Adding leela (fqdn leela.planet-express.local) to /etc/hosts ip 192.168.0.20, removing leela, leela.planet-express.local, leela, leela.planet-express.local
20101105085419:INFO:Adding leela (fqdn leela.planet-express.local) to /etc/hosts ip ::1, removing leela, leela.planet-express.local, leela, leela.planet-express.local
20101105085419:INFO:Adding leela (fqdn leela.planet-express.local) to /etc/hosts ip 127.0.1.1, removing leela, leela.planet-express.local, leela, leela.planet-express.local
20101105085419:INFO:Reading krb5 file /tmp/likewisetmpQ2zvsp/etc/krb5.conf
20101105085419:INFO:Reading nsswitch file /etc/nsswitch.conf
20101105085420:INFO:Reading krb5 file /tmp/likewisetmpfXoAku/etc/krb5.conf
20101105085420:INFO:Starting krb5.conf configuration (enabling)
20101105085420:INFO:Reading krb5 file /tmp/likewisetmpfXoAku/etc/krb5.conf
20101105085420:INFO:Creating krb5 stanza 'appdefaults'
20101105085420:INFO:Writing krb5 file /tmp/likewisetmpfXoAku/etc/krb5.conf
20101105085420:INFO:File /tmp/likewisetmpfXoAku/etc/krb5.conf modified
20101105085420:INFO:Finishing krb5.conf configuration
20101105085420:INFO:Found config file /etc/ssh/sshd_config
20101105085420:INFO:Found binary /usr/sbin/sshd
20101105085420:INFO:Reading ssh file /etc/ssh/sshd_config
20101105085420:INFO:Found open sshd version 5.5.-1p1
20101105085420:INFO:Testing option ChallengeResponseAuthentication
20101105085420:INFO:Option ChallengeResponseAuthentication supported
20101105085420:INFO:Testing option UsePAM
20101105085420:INFO:Testing option PAMAuthenticationViaKBDInt
20101105085420:INFO:Option PAMAuthenticationViaKBDInt not supported
20101105085420:INFO:Testing option KbdInteractiveAuthentication
20101105085420:INFO:Option KbdInteractiveAuthentication supported
20101105085420:INFO:Testing option GSSAPIAuthentication
20101105085420:INFO:Option GSSAPIAuthentication supported
20101105085420:INFO:Testing option GSSAPICleanupCredentials
20101105085420:INFO:Option GSSAPICleanupCredentials supported
20101105085420:INFO:Found config file /etc/ssh/ssh_config
20101105085420:INFO:Found binary /usr/bin/ssh
20101105085420:INFO:Reading ssh file /etc/ssh/ssh_config
20101105085420:INFO:Testing option GSSAPIAuthentication
20101105085420:INFO:Testing option GSSAPIDelegateCredentials
20101105085420:INFO:Option GSSAPIDelegateCredentials supported
Joining to AD Domain:   planet-express.local
With Computer DNS Name: leela.planet-express.local

Administrator@PLANET-EXPRESS.LOCAL's password: 
20101105085423:INFO:Running module join
20101105085423:INFO:Starting krb5.conf configuration (enabling)
20101105085423:INFO:Reading krb5 file /tmp/likewisetmptTlcEH/etc/krb5.conf
20101105085423:WARNING:Short domain name not specified. Defaulting to 'planet-express'
20101105085423:INFO:Creating krb5 stanza 'appdefaults'
20101105085423:INFO:Writing krb5 file /tmp/likewisetmptTlcEH/etc/krb5.conf
20101105085423:INFO:File /tmp/likewisetmptTlcEH/etc/krb5.conf modified
20101105085423:INFO:Finishing krb5.conf configuration

[B]Error: Lsass Error [code 0x00080047]

40286 (0x9D5E) LW_ERROR_LDAP_SERVER_DOWN - Unknown error
20101105085433:ERROR:Lsass Error [CENTERROR_DOMAINJOIN_LSASS_ERROR]

40286 (0x9D5E) LW_ERROR_LDAP_SERVER_DOWN - Unknown error
[/B]
Stack Trace:
main.c:938
main.c:479
djmodule.c:323
djauthinfo.c:843
djauthinfo.c:1187

```

Then I added this into the /etc/hosts

```
# cat /etc/hosts
192.168.0.20 leela.planet-express.local leela # Added by NetworkManager
127.0.0.1 localhost.localdomain localhost
::1 leela.planet-express.local leela localhost6
127.0.1.1 leela.planet-express.local leela
**192.168.0.10 ZOIDBERG.planet-express.local ZOIDBERG** *_//This is the Domain Controler //_*
# The following lines are desirable for IPv6 capable hosts
::1 localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhost
```

and I get this message:

```
# domainjoin-cli --loglevel info --log . join planet-express.local Administrator
20101105085344:INFO:Domainjoin invoked with the join command (remaining arguments will be printed later):
20101105085344:INFO:    [domainjoin-cli]
20101105085344:INFO:    [--loglevel]
20101105085344:INFO:    [info]
20101105085344:INFO:    [--log]
20101105085344:INFO:    [.]
20101105085344:INFO:    [join]
20101105085344:INFO:Checking status of daemon [/etc/init.d/lwsmd]
20101105085344:INFO:Daemon [/etc/init.d/lwsmd]: status [0]
20101105085344:INFO:Checking status of daemon [/etc/init.d/lwsmd]
20101105085344:INFO:Daemon [/etc/init.d/lwsmd]: status [0]
20101105085344:INFO:Checking status of daemon [/etc/init.d/lwregd]
20101105085345:INFO:Daemon [/etc/init.d/lwregd]: status [0]
20101105085345:INFO:Checking status of daemon [/etc/init.d/lwregd]
20101105085345:INFO:Daemon [/etc/init.d/lwregd]: status [0]
20101105085345:INFO:Checking status of daemon [/etc/init.d/netlogond]
20101105085345:INFO:Daemon [/etc/init.d/netlogond]: status [0]
20101105085345:INFO:Checking status of daemon [/etc/init.d/netlogond]
20101105085345:INFO:Daemon [/etc/init.d/netlogond]: status [0]
20101105085345:INFO:Checking status of daemon [/etc/init.d/lwiod]
20101105085345:INFO:Daemon [/etc/init.d/lwiod]: status [0]
20101105085345:INFO:Checking status of daemon [/etc/init.d/lwiod]
20101105085345:INFO:Daemon [/etc/init.d/lwiod]: status [0]
20101105085345:INFO:Checking status of daemon [/etc/init.d/dcerpcd]
20101105085345:INFO:Daemon [/etc/init.d/dcerpcd]: status [0]
20101105085345:INFO:Checking status of daemon [/etc/init.d/dcerpcd]
20101105085345:INFO:Daemon [/etc/init.d/dcerpcd]: status [0]
20101105085345:INFO:Checking status of daemon [/etc/init.d/eventlogd]
20101105085345:INFO:Daemon [/etc/init.d/eventlogd]: status [0]
20101105085345:INFO:Checking status of daemon [/etc/init.d/eventlogd]
20101105085345:INFO:Daemon [/etc/init.d/eventlogd]: status [0]
20101105085345:INFO:Checking status of daemon [/etc/init.d/lsassd]
20101105085345:INFO:Daemon [/etc/init.d/lsassd]: status [0]
20101105085345:INFO:Checking status of daemon [/etc/init.d/lsassd]
20101105085345:INFO:Daemon [/etc/init.d/lsassd]: status [0]
20101105085345:INFO:Domainjoin invoked with 2 arg(s) to the join command:
20101105085345:INFO:    [planet-express.local]
20101105085345:INFO:    [Administrator]
20101105085345:INFO:Adding leela (fqdn leela.planet-express.local) to /etc/hosts ip ::1, removing leela, leela.planet-express.local, leela, leela.planet-express.local
20101105085345:INFO:Adding leela (fqdn leela.planet-express.local) to /etc/hosts ip 127.0.1.1, removing leela, leela.planet-express.local, leela, leela.planet-express.local
20101105085345:INFO:Reading krb5 file /tmp/likewisetmpvgMLW8/etc/krb5.conf
20101105085345:INFO:Reading nsswitch file /etc/nsswitch.conf
20101105085345:INFO:Reading krb5 file /tmp/likewisetmpqzPUUK/etc/krb5.conf
20101105085345:INFO:Starting krb5.conf configuration (enabling)
20101105085345:INFO:Reading krb5 file /tmp/likewisetmpqzPUUK/etc/krb5.conf
20101105085345:INFO:Creating krb5 stanza 'appdefaults'
20101105085345:INFO:Writing krb5 file /tmp/likewisetmpqzPUUK/etc/krb5.conf
20101105085345:INFO:File /tmp/likewisetmpqzPUUK/etc/krb5.conf modified
20101105085345:INFO:Finishing krb5.conf configuration
20101105085345:INFO:Found config file /etc/ssh/sshd_config
20101105085345:INFO:Found binary /usr/sbin/sshd
20101105085345:INFO:Reading ssh file /etc/ssh/sshd_config
20101105085345:INFO:Found open sshd version 5.5.-1p1
20101105085345:INFO:Testing option ChallengeResponseAuthentication
20101105085345:INFO:Option ChallengeResponseAuthentication supported
20101105085345:INFO:Testing option UsePAM
20101105085345:INFO:Testing option PAMAuthenticationViaKBDInt
20101105085345:INFO:Option PAMAuthenticationViaKBDInt not supported
20101105085345:INFO:Testing option KbdInteractiveAuthentication
20101105085345:INFO:Option KbdInteractiveAuthentication supported
20101105085345:INFO:Testing option GSSAPIAuthentication
20101105085345:INFO:Option GSSAPIAuthentication supported
20101105085345:INFO:Testing option GSSAPICleanupCredentials
20101105085345:INFO:Option GSSAPICleanupCredentials supported
20101105085345:INFO:Found config file /etc/ssh/ssh_config
20101105085345:INFO:Found binary /usr/bin/ssh
20101105085345:INFO:Reading ssh file /etc/ssh/ssh_config
20101105085345:INFO:Testing option GSSAPIAuthentication
20101105085345:INFO:Testing option GSSAPIDelegateCredentials
20101105085345:INFO:Option GSSAPIDelegateCredentials supported
Joining to AD Domain:   planet-express.local
With Computer DNS Name: leela.planet-express.local

Administrator@PLANET-EXPRESS.LOCAL's password: 
20101105085348:INFO:Running module join
20101105085349:INFO:Starting krb5.conf configuration (enabling)
20101105085349:INFO:Reading krb5 file /tmp/likewisetmp68tdSw/etc/krb5.conf
20101105085349:WARNING:Short domain name not specified. Defaulting to 'planet-express'
20101105085349:INFO:Creating krb5 stanza 'appdefaults'
20101105085349:INFO:Writing krb5 file /tmp/likewisetmp68tdSw/etc/krb5.conf
20101105085349:INFO:File /tmp/likewisetmp68tdSw/etc/krb5.conf modified
20101105085349:INFO:Finishing krb5.conf configuration

[B]Error: Lsass Error [code 0x00080047]

31 (0x1F) ERROR_GEN_FAILURE - Unknown error
20101105085350:ERROR:Lsass Error [CENTERROR_DOMAINJOIN_LSASS_ERROR]

31 (0x1F) ERROR_GEN_FAILURE - Unknown error[/B]

Stack Trace:
main.c:938
main.c:479
djmodule.c:323
djauthinfo.c:843
djauthinfo.c:1187

```

> [B]Error: Lsass Error [code 0x00080047]

31 (0x1F) ERROR_GEN_FAILURE - Unknown error
20101105085350:ERROR:Lsass Error [CENTERROR_DOMAINJOIN_LSASS_ERROR]

31 (0x1F) ERROR_GEN_FAILURE - Unknown error[/B]

Whats wrong ? can anyone help me ?

---

### Post by bmw-uf on 2010-11-08
it is new bug introduced in openldap in ubuntu 10.10.

some useful links:
bug in likewise-open package
[https://bugs.launchpad.net/ubuntu/+source/likewise-open/+bug/640558](https://bugs.launchpad.net/ubuntu/+source/likewise-open/+bug/640558)
bug in openldap
[https://bugs.launchpad.net/ubuntu/+source/openldap/+bug/661547](https://bugs.launchpad.net/ubuntu/+source/openldap/+bug/661547)

With patch(for openldap) from second link likewise-open work fine. If you do not know how to patch and build deb packages -- just add this ppa and apt-get update && apt-get upgrade. 

[https://launchpad.net/~ssalley/+archive/ppa](https://launchpad.net/~ssalley/+archive/ppa)

```
sudo -i
apt-add-repository ppa:ssalley/ppa
apt-get update
apt-get -y upgrade
apt-get install likewise-open-gui

```

and just connect to you active directory without any troubles.

---


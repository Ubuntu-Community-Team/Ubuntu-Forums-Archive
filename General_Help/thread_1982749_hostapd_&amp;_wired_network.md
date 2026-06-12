---
title: "hostapd &amp; wired network ?"
date: 2012-05-19
forum: General Help
---

### Post by hashemifard on 2012-05-19
hi
im using the following network with hostapd on the authenticator :

Authentication server <---wired---> Authenticator(hostapd<----wired--->
 User (win XP with WinRadius)
1.100 -------- 1.200 , 0.13 ----- 0.12

and this is my configurations for hostapd :

interface=eth1
driver=wired
dump_file=/tmp/hostapd.dump

ctrl_interface=/var/run/hostapd
ctrl_interface_group=0

logger_syslog=-1
logger_syslog_level=2
logger_stdout=-1
logger_stdout_level=2

ieee8021x=1
eapol_key_index_workaround=0
eapol_version=1

own_ip_addr=192.168.1.200
auth_server_addr=192.168.1.100
auth_server_port=1812
auth_server_shared_secret=secret
acct_server_addr=192.168.1.100
acct_server_port=1813
acct_server_shared_secret=secret

there is a problem : the EAPOL_start is sent to the authenticator by
the user (win XP) but the authenticator doesn't reply to user. and also  the radius messages transmit between server and authenticator. what is
the solution ? please help me
another question is : can hostapd used in a wired network at all ?

thanks a lot ...

---


---
title: "smpts smarthost in exim4"
date: 2011-10-10
forum: General Help
---

### Post by Nessined on 2011-10-10
I try to configure a smtps smarthost in exim4. I see that the TCP connection is set up but no mails are transferred.

Does someone know what I'm doing wrong or which configuration is missing ?

The smtp configuration in thunderbird is:
```
port=443
Normal password
SSL/TLS
```In exim4 I have following configuration:

update-exim4.conf.conf contains:
```
dc_eximconfig_configtype='smarthost'
dc_smarthost='smtps.kuleuven.be::443'
```passwd.client contains:
```
smtps.kuleuven.be:username:password
```I have experimented by adding the text in bold to the exim4 config file, but no success:
```
remote_smtp:
  **hosts_require_tls 'smtps.kuleuven.be::443**'
```or 

```
remote_smtp:
  **hosts_require_tls 'smtps.kuleuven.be'**
```

---

### Post by Nessined on 2011-10-21
I have found the solution (tried out on Lucid)

You must install stunnel4.

Replace in /etc/default/stunnel4: **ENABLED=0** by **ENABLED=1**
Add to /etc/stunnel/stunnel.conf:
[B]client = yes
[smtp-kul]
accept = 443
connect = smtps.kuleuven.be:443[/B]

Note: any free port number is ok for the **accept** parameter

Start stunnel: sudo /etc/init.d/stunnel4 start

Add following statements to the exim4 config: /etc/exim4/conf.d/*:
[B]# allow plain passwords
# split file: main/01_exim4-config_listmacrosdefs
# below "MAIN CONFIGURATION SETTINGS"
AUTH_CLIENT_ALLOW_NOTLS_PASSWORDS = true
# allow to send to localhost
# split file: router/200_exim4-config_primary
# below "smarthost:"
  self = send
# specify the local port (same as accept parameter in stunnel.conf)
# enforce password authentication
# split file: transport/30_exim4-config_remote_smtp_smarthost
# below "remote_smtp_smarthost:"
  port = 443
  hosts_require_auth = localhost[/B]

Add username and password in /etc/exim4/passwd.client:
**localhost:*username*:*password***

Make sure /etc/email-addresses is properly filled in.

Execute "sudo dpkg-reconfigure exim4-config" and enter **localhost** as smarthost

---


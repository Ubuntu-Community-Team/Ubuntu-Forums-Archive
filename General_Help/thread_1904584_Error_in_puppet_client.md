---
title: "Error in puppet client"
date: 2012-01-05
forum: General Help
---

### Post by karthick87 on 2012-01-05
I am getting the following error in puppet client, when i run 

```
puppetd  --test
```
```
root@TME25:~# puppetd --test
err: Could not run Puppet configuration client: Could not retrieve local facts: bad URI(is not URI?): http://169.254.169.254/2008-02-01/meta-data/<HTML><HEAD><TITLE>HTTP access denied</TITLE></HEAD><BODY><img src/

```

How do i resolve this error?
  **[SIZE=2][SIZE=1]Output of[/SIZE] [/SIZE]```
puppetd --test --debug
```**


```
root@TME25:~# puppetd --test --debug
debug: Failed to load library 'rubygems' for feature 'rubygems'
debug: Failed to load library 'selinux' for feature 'selinux'
debug: Puppet::Type::User::ProviderUser_role_add: file rolemod does not exist
debug: Puppet::Type::User::ProviderLdap: true value when expecting false
debug: Puppet::Type::User::ProviderPw: file pw does not exist
debug: Puppet::Type::User::ProviderDirectoryservice: file /usr/bin/dscl does not exist
debug: Puppet::Type::File::ProviderMicrosoft_windows: feature microsoft_windows is missing
debug: Failed to load library 'ldap' for feature 'ldap'
debug: /File[/var/lib/puppet/ssl/private]: Autorequiring File[/var/lib/puppet/ssl]
debug: /File[/var/run/puppet/agent.pid]: Autorequiring File[/var/run/puppet]
debug: /File[/var/lib/puppet/clientbucket]: Autorequiring File[/var/lib/puppet]
debug: /File[/var/lib/puppet/ssl/certificate_requests]: Autorequiring File[/var/lib/puppet/ssl]
debug: /File[/var/lib/puppet/ssl]: Autorequiring File[/var/lib/puppet]
debug: /File[/var/lib/puppet/ssl/certs/ca.pem]: Autorequiring File[/var/lib/puppet/ssl/certs]
debug: /File[/var/lib/puppet/ssl/certs/tme25.chn.jd.com.pem]: Autorequiring File[/var/lib/puppet/ssl/certs]
debug: /File[/var/lib/puppet/ssl/public_keys]: Autorequiring File[/var/lib/puppet/ssl]
debug: /File[/var/lib/puppet/client_data]: Autorequiring File[/var/lib/puppet]
debug: /File[/var/lib/puppet/ssl/private_keys]: Autorequiring File[/var/lib/puppet/ssl]
debug: /File[/var/lib/puppet/ssl/private_keys/tme25.chn.jd.com.pem]: Autorequiring File[/var/lib/puppet/ssl/private_keys]
debug: /File[/var/lib/puppet/ssl/certs]: Autorequiring File[/var/lib/puppet/ssl]
debug: /File[/var/lib/puppet/state/graphs]: Autorequiring File[/var/lib/puppet/state]
debug: /File[/var/lib/puppet/ssl/public_keys/tme25.chn.jd.com.pem]: Autorequiring File[/var/lib/puppet/ssl/public_keys]
debug: /File[/var/lib/puppet/state]: Autorequiring File[/var/lib/puppet]
debug: /File[/etc/puppet/puppet.conf]: Autorequiring File[/etc/puppet]
debug: /File[/var/lib/puppet/lib]: Autorequiring File[/var/lib/puppet]
debug: /File[/var/lib/puppet/client_yaml]: Autorequiring File[/var/lib/puppet]
debug: /File[/var/lib/puppet/facts]: Autorequiring File[/var/lib/puppet]
debug: Finishing transaction -611387488
debug: /File[/var/lib/puppet/ssl/private_keys/tme25.chn.jd.com.pem]: Autorequiring File[/var/lib/puppet/ssl/private_keys]
debug: /File[/var/lib/puppet/ssl/private]: Autorequiring File[/var/lib/puppet/ssl]
debug: /File[/var/lib/puppet/ssl/public_keys]: Autorequiring File[/var/lib/puppet/ssl]
debug: /File[/var/lib/puppet/state]: Autorequiring File[/var/lib/puppet]
debug: /File[/var/lib/puppet/ssl/certs]: Autorequiring File[/var/lib/puppet/ssl]
debug: /File[/var/lib/puppet/lib]: Autorequiring File[/var/lib/puppet]
debug: /File[/var/lib/puppet/ssl]: Autorequiring File[/var/lib/puppet]
debug: /File[/var/lib/puppet/facts]: Autorequiring File[/var/lib/puppet]
debug: /File[/var/lib/puppet/ssl/private_keys]: Autorequiring File[/var/lib/puppet/ssl]
debug: /File[/var/lib/puppet/ssl/certs/tme25.chn.jd.com.pem]: Autorequiring File[/var/lib/puppet/ssl/certs]
debug: /File[/var/lib/puppet/ssl/certs/ca.pem]: Autorequiring File[/var/lib/puppet/ssl/certs]
debug: /File[/var/lib/puppet/ssl/certificate_requests]: Autorequiring File[/var/lib/puppet/ssl]
debug: /File[/var/lib/puppet/ssl/public_keys/tme25.chn.jd.com.pem]: Autorequiring File[/var/lib/puppet/ssl/public_keys]
debug: Finishing transaction -611779688
debug: Using cached certificate for ca
debug: Using cached certificate for tme25.chn.jd.com
debug: Finishing transaction -611951478
```
err: Could not run Puppet configuration client: Could not retrieve local facts: bad URI(is not URI?): http://169.254.169.254/2008-02-01/meta-data/<HTML><HEAD><TITLE>HTTP access denied</TITLE></HEAD><BODY><img src/

---

### Post by karthick87 on 2012-01-06
I think the error causes because of Amazon ec2 package installed in ubuntu. How to rectify it?

---


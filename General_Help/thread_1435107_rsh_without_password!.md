---
title: "rsh without password!"
date: 2010-03-21
forum: General Help
---

### Post by apach3 on 2010-03-21
Hey,
I am using lam-mpi( 7.1.2 ) on ubuntu (9.10) and I am stuck with rsh.
I need a rsh login without any password.I have already configured my 
host.equiv , .rhosts, host.allow, host.deny.
```

# /etc/hosts.equiv: list  of  hosts  and  users  that are granted "trusted" r
#            command access to your system .
10.9.20.197
10.9.20.91

``````

# /etc/hosts.allow: list of hosts that are allowed to access the system.
#                   See the manual pages hosts_access(5) and hosts_options(5).
#
# Example:    ALL: LOCAL @some_netgroup
#             ALL: .foobar.edu EXCEPT terminalserver.foobar.edu
#
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper, as well as for
# rpc.mountd (the NFS mount daemon). See portmap(8) and rpc.mountd(8)
# for further information.
#
in.rshd : 10.9.20. 
in.rlogind : 10.9.20. 
portmap : 10.9.20. 
sshd  : 10.9.20.

``````

# /etc/hosts.deny: list of hosts that are _not_ allowed to access the system.
#                  See the manual pages hosts_access(5) and hosts_options(5).
#
# Example:    ALL: some.host.name, .some.domain
#             ALL EXCEPT in.fingerd: other.host.name, .other.domain
#
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper, as well as for
# rpc.mountd (the NFS mount daemon). See portmap(8) and rpc.mountd(8)
# for further information.
#
# The PARANOID wildcard matches any host whose name does not match its
# address.

# You may wish to enable this to ensure any programs that don't
# validate looked up hostnames still leave understandable logs. In past
# versions of Debian this has been the default.
# ALL: PARANOID
ALL : ALL

```and .rhosts in my home dir
```

10.9.20.197
10.9.20.91

```
pls help me its urgent.

---


---
title: "Sguil Socket Error??"
date: 2010-10-21
forum: General Help
---

### Post by srslynrdy on 2010-10-21
Im getting this error whenever the sguil client tries to connect to the server. Currently im doing everything on localhost.

```

greenteam@greenteam-desktop:~/Desktop/sguil-0.7.0/server$ ./sguild 
pid(2730)  Loading access list: /etc/sguild/sguild.access
pid(2730)  Sensor access list set to ALLOW ANY.
pid(2730)  Client access list set to ALLOW ANY.
pid(2730)  Email Configuration:
pid(2730)    Config file: /etc/sguild/sguild.email
pid(2730)    Enabled: No
pid(2730)  Connecting to localhost on 3306 as sguil
pid(2730)  MySQL Version: version 5.1.41-3ubuntu12.6
pid(2730)  SguilDB Version: 0.12
pid(2730)  Retrieving DB info...
pid(2730)    SELECT sid, net_name, hostname, agent_type FROM sensor WHERE active='Y' ORDER BY net_name, sid ASC
pid(2730)  Warning: Event table appears to be empty.
pid(2730)  If this is a new DB, then you can safely ignore this warning.
pid(2730)  Retrieving DB info...
pid(2730)    Getting a list of tables.
pid(2730)    ...Getting info on history.
pid(2730)    ...Getting info on nessus.
pid(2730)    ...Getting info on nessus_data.
pid(2730)    ...Getting info on pads.
pid(2730)    ...Getting info on portscan.
pid(2730)    ...Getting info on sensor.
pid(2730)    ...Getting info on status.
pid(2730)    ...Getting info on user_info.
pid(2730)    ...Getting info on version.
pid(2730)  Sguild Initialized.
pid(2731)  Loaderd Forked
pid(2732)  Queryd Forked
pid(2730)  Client Connect: 127.0.0.1 53803 sock13
pid(2730)  Validating client access: 127.0.0.1
pid(2730)  Valid client access: 127.0.0.1
pid(2730)  Sending sock13: SGUIL-0.7.0 OPENSSL ENABLED
pid(2730)  Client Command Received: VersionInfo SGUIL-0.7.0 OPENSSL ENABLED
pid(2730)  ERROR: unable to set certificate file /etc/sguild/certs/sguild.pem: no start line
pid(2730)  No clients to send info msg to.
pid(2730)  ERROR: can not find channel named "sock13"
Error: can not find channel named "sock13"
can not find channel named "sock13"
    while executing
"close $socketID"
    (procedure "ClientVersionCheck" line 24)
    invoked from within
"ClientVersionCheck $socketID $data1 "
    ("VersionInfo" arm line 1)
    invoked from within
"switch -exact $clientCmd {
      DeleteEventID { $clientCmd $socketID $index1 $index2 }
      DeleteEventIDList { $clientCmd $socketID $data1 }
      ..."
    (procedure "ClientCmdRcvd" line 38)
    invoked from within
"ClientCmdRcvd sock13"
SGUILD: killing child procs...
SGUILD: Exiting...


```

Does anybody know how to fix this sock error? Thanks in advance

---


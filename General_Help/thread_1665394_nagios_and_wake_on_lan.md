---
title: "nagios and wake on lan"
date: 2011-01-12
forum: General Help
---

### Post by nicofff on 2011-01-12
I've set up Nagios to monitor the servers at the company I work for. Most of the servers have the BIOS option to power on after power failure, but some don't.
For those servers I tried to implement wake on lan. So I installed the wakeonlan package and tested it by hand and worked perfectly.
Then I set it up in Nagios this way (changed the server name and mac address just in case ;))


```
define host {
        host_name   Server1
        alias       Server1
        address     192.168.2.5
        use         generic-host
        event_handler WOLHandler
}

define command {
    command_name WOLHandler
    command_line /usr/bin/wakeonlan AA:BB:CC:DD:EE:FF
}

```
Being a critical server I couldn't just turn it off to test if this worked, so I hoped it will work.
Last night, light went out, and when it came back, the server didn't power back on.
So I checked nagios log and found this: 

```
**ePN failed to compile /usr/bin/wakeonlan: "Missing right curly or square bracket at (eval 1) line 183, at end of line
```

I retested it by copying the command in a shell and executed perfectly.

I'd love some help, I'm the only sysadmin at the company, and I'm going on vacations in a few days and don't want to get called because of servers going down.

Thanks

---


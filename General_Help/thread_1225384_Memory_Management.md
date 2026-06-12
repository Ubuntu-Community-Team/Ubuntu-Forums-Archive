---
title: "Memory Management"
date: 2009-07-28
forum: General Help
---

### Post by abazoskib on 2009-07-28
when i run free -m i get:

```
             total       used       free     shared    buffers     cached
Mem:          1746       1286        460          0        162        853
-/+ buffers/cache:        270       1475
Swap:          895          0        895

```

I feel like the system has been lagging ever since I changed my apache configuration. Here are my settings:

Apache
```
StartServers       20
MinSpareServers    30
MaxSpareServers   80
ServerLimit      256
MaxClients       256
MaxRequestsPerChild  4000
```

PHP

```
max_execution_time = 90     ; Maximum execution time of each script, in seconds
max_input_time = 240    ; Maximum amount of time each script may spend parsing request data
memory_limit = 128M      ; Maximum amount of memory a script may consume (16MB)

```

MYSQL

```
key_buffer_size,268435456
max_allowed_packet,33554432
max_binlog_cache_size,4294967295
max_binlog_size,1073741824
max_connect_errors,10
max_connections,4000
query_alloc_block_size,8192
query_cache_limit,1048576
query_cache_min_res_unit,4096
query_cache_size,0
query_cache_type,ON

```

How can I improve my configuration for performance? I am doing lots of db intensive work, mostly PHP scripting, running a SOAP server, and lots of PHP/curl data transmissions. Getting lots of traffic on the SOAP server per day.

---

### Post by Joeb454 on 2009-07-28
Thread moved to General Help :)

---

### Post by abazoskib on 2009-07-28
looks like those memory figures from "free -m" have stayed consistent, so i am not using any swap, however still not running as fast as id like it to be

---

### Post by trwww on 2009-07-28
> **abazoskib said:**
> I feel like the system has been lagging ever since I changed my apache configuration.

If it ran better before you changed the config, perhaps you should change it back?

---

### Post by abazoskib on 2009-07-28
I could do that. But I was not getting good speed with my scripts and curl transmissions. I'm just looking for experienced opinions on server management, worse comes to worst I'll have to change the settings back.

---

### Post by trwww on 2009-07-29
> **abazoskib said:**
> ... I was not getting good speed with my scripts and curl transmissions.

Allright. A little more like it. But you still haven't provided enough info to get real advice.

You say "scripts" in the context of "not getting good speed". Unfortunately you'll have to provide more detail in place of "scripts" That word in itself means a lot of different things to people. Same with "curl transmissions"

Perhaps if you could explain "curl transmissions" first since you mentioned it here and as far as we know, the most unique part of your setup.

Are you running curl in php scripts? If so, what type of content are you fetching? How often does happen?

Also, based on the info you gave, really I'm not surprised it is running even slower. For example, adding more MinSpareServers, MaxRequestsPerChild, and MaxClients on a already slow system is not a procedure that usually then speeds the application up. You're using more system resources, not less.

I see you've got 2 gb of ram, but could you provide specs on the rest of the hardware?

regards,

---

### Post by trwww on 2009-07-29
After re-re-re reading your OP, I finally see all of it.

I saw the curl part, but missed the other stuff... dont know how.

Along with what I said before, you may want to consider scaling your app to multiple machines (database on seperate/multiple machines, for example).

Either that or profile your app to find the slowest bits and speed them up one at a time untill its acceptible. This includes finding other config options that may indeed speed the app up.

Thems your options in a nutshell.

regards,

---


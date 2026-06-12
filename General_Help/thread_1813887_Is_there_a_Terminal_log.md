---
title: "Is there a Terminal log?"
date: 2011-07-28
forum: General Help
---

### Post by marsgorski on 2011-07-28
Hi all,

I've been trying to setup squidguard on my computer the following command

```
sudo squidGuard –C all
```

takes many hours to finish (at least 4, is this strange in itself?) Last night I ran the command and I left my computer running hoping that it would be done this morning, but I have this problem where the display freezes after it has gone to sleep. So, the problem is I don't know if the process finished because I had to restart my computer using ctrl+alt+f1 and the shutdown command. Is there some log I can look at or some other way I can check whether the process finished? Thanks

---

### Post by thefasterblueone on 2011-07-28
To check the SquidGuard log look in:

```
/usr/local/squidGuard/logs
```

---

### Post by marsgorski on 2011-07-28
Thanks for the fast reply. I could not find the squidGuard directory under local though, it is not there. I know there is a directory 

```
/var/log/squid
```

but I do not have permission to access it. I used the configuration instruction [here]("http://nwlinux.com/install-and-configure-squidguard-web-filter-on-ubuntu/") and [here]("https://help.ubuntu.com/community/SquidGuard").

This creates several questions: Is something wrong if I don't have a squidGuard directory under local? How can I acces the squid log under the log directory? and is there another way to see whether a given process running in the terminal actually finished?

---

### Post by thefasterblueone on 2011-07-28
Here is a link to [squid guard setup guide](http://www.squidguard.org/Doc/).


List processes with 'squid' in their name:

```
ps aux | grep squid
```


To show what is in squid directory:

```
cd /var/log/squid && ls
```

---

### Post by lkjoel on 2011-07-28
> **thefasterblueone said:**
> ...
To show what is in squid directory:

```
cd /var/log/squid && ls
```
A simpler way is to do this:
```
ls /var/log/squid
```

---

### Post by fdrake on 2011-07-28
```
locate squid | grep log
<get the list of the path-log files relate to squid >
sudo less path-log  #to read the file

```

---

### Post by thefasterblueone on 2011-07-28
Hey thanks for the commands. I always thought you would have to 'cd' to a directory before the 'ls' command.

Using 'locate' and 'less' makes quick work of reading files.
I added them to my arsenal.

:D

---

### Post by tom4everitt on 2011-07-29
Wow! How did I not know about locate!!!!!!!! It's the best thing ever (using find is sooo slow in comparison :) ).

---

### Post by marsgorski on 2011-07-29
From the  file squidGuard.log I get the following:

2011-07-27 09:21:13 [4543] New setting: dbhome: /var/lib/squidguard/db
2011-07-27 09:21:13 [4543] New setting: logdir: /var/log/squid
2011-07-27 09:21:13 [4543] destblock good missing active content, set inactive
2011-07-27 09:21:13 [4543] destblock local missing active content, set inactive
2011-07-27 09:21:13 [4543] squidGuard 1.4 started (1311783673.152)
2011-07-27 09:21:13 [4543] db update done
2011-07-27 09:21:13 [4543] squidGuard stopped (1311783673.153)

I'm not sure what to make of this; I don't think this means that "sudo squidGuard -C all" ran succesfully, does it? There we only two instances in the log where the "db update done" appears...out of ~5 tries. In none of the times did the "~$" appeared in the terminal after running the command, thinking that the process was not done and it was taking hours.

To be thorough, below is the log file in its entirety. The period of time where I left the process running (At least I think it was running) overnight is from july 27 to the 28.. Although I don't remember whether I tried running the command past midnight (the 28 or earlier.)

Thanks to everyone who has chipped in.

```
2011-07-27 09:21:13 [4523] New setting: dbhome: /var/lib/squidguard/db
2011-07-27 09:21:13 [4523] New setting: logdir: /var/log/squid
2011-07-27 09:21:13 [4523] destblock good missing active content, set inactive
2011-07-27 09:21:13 [4523] destblock local missing active content, set inactive
2011-07-27 09:21:13 [4523] squidGuard 1.4 started (1311783673.111)
2011-07-27 09:21:13 [4523] db update done
2011-07-27 09:21:13 [4523] squidGuard stopped (1311783673.111)
2011-07-27 09:21:13 [4543] New setting: dbhome: /var/lib/squidguard/db
2011-07-27 09:21:13 [4543] New setting: logdir: /var/log/squid
2011-07-27 09:21:13 [4543] destblock good missing active content, set inactive
2011-07-27 09:21:13 [4543] destblock local missing active content, set inactive
2011-07-27 09:21:13 [4543] squidGuard 1.4 started (1311783673.152)
2011-07-27 09:21:13 [4543] db update done
2011-07-27 09:21:13 [4543] squidGuard stopped (1311783673.153)
2011-07-27 10:24:23 [5573] New setting: dbhome: /var/lib/squidguard/db
2011-07-27 10:24:23 [5573] New setting: logdir: /var/log/squid
2011-07-27 10:24:23 [5573] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-27 10:24:23 [5573] Error db_open: No such file or directory
2011-07-27 10:24:23 [5573] Going into emergency mode
2011-07-27 10:28:11 [5586] New setting: dbhome: /var/lib/squidguard/db
2011-07-27 10:28:11 [5586] New setting: logdir: /var/log/squid
2011-07-27 10:28:11 [5586] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-27 10:28:11 [5586] Error db_open: No such file or directory
2011-07-27 10:28:11 [5586] Going into emergency mode
2011-07-27 12:01:42 [6773] New setting: dbhome: /var/lib/squidguard/db
2011-07-27 12:01:42 [6773] New setting: logdir: /var/log/squid
2011-07-27 12:01:42 [6773] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-27 12:01:42 [6773] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-27 12:01:42 [6773] Going into emergency mode
2011-07-27 12:01:42 [6774] New setting: dbhome: /var/lib/squidguard/db
2011-07-27 12:01:42 [6774] New setting: logdir: /var/log/squid
2011-07-27 12:01:42 [6774] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-27 12:01:42 [6774] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-27 12:01:42 [6774] Going into emergency mode
2011-07-27 12:01:42 [6775] New setting: dbhome: /var/lib/squidguard/db
2011-07-27 12:01:42 [6775] New setting: logdir: /var/log/squid
2011-07-27 12:01:42 [6775] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-27 12:01:42 [6776] New setting: dbhome: /var/lib/squidguard/db
2011-07-27 12:01:42 [6776] New setting: logdir: /var/log/squid
2011-07-27 12:01:42 [6776] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-27 12:01:42 [6775] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-27 12:01:42 [6775] Going into emergency mode
2011-07-27 12:01:42 [6776] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-27 12:01:42 [6776] Going into emergency mode
2011-07-27 12:01:42 [6777] New setting: dbhome: /var/lib/squidguard/db
2011-07-27 12:01:42 [6777] New setting: logdir: /var/log/squid
2011-07-27 12:01:42 [6777] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-27 12:01:42 [6777] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-27 12:01:42 [6777] Going into emergency mode
2011-07-27 12:05:38 [6805] New setting: dbhome: /var/lib/squidguard/db
2011-07-27 12:05:38 [6805] New setting: logdir: /var/log/squid
2011-07-27 12:05:38 [6805] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-27 12:05:38 [6805] Error db_open: No such file or directory
2011-07-27 12:05:38 [6805] Going into emergency mode
2011-07-27 12:36:30 [7252] New setting: dbhome: /var/lib/squidguard/db
2011-07-27 12:36:30 [7252] New setting: logdir: /var/log/squid
2011-07-27 12:36:30 [7252] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-27 12:36:30 [7252] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-27 12:36:30 [7252] Going into emergency mode
2011-07-27 12:36:30 [7253] New setting: dbhome: /var/lib/squidguard/db
2011-07-27 12:36:30 [7253] New setting: logdir: /var/log/squid
2011-07-27 12:36:30 [7253] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-27 12:36:30 [7253] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-27 12:36:30 [7253] Going into emergency mode
2011-07-27 12:36:30 [7255] New setting: dbhome: /var/lib/squidguard/db
2011-07-27 12:36:30 [7255] New setting: logdir: /var/log/squid
2011-07-27 12:36:30 [7255] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-27 12:36:30 [7254] New setting: dbhome: /var/lib/squidguard/db
2011-07-27 12:36:30 [7255] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-27 12:36:30 [7255] Going into emergency mode
2011-07-27 12:36:30 [7254] New setting: logdir: /var/log/squid
2011-07-27 12:36:30 [7254] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-27 12:36:30 [7254] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-27 12:36:30 [7254] Going into emergency mode
2011-07-27 12:36:30 [7256] New setting: dbhome: /var/lib/squidguard/db
2011-07-27 12:36:30 [7256] New setting: logdir: /var/log/squid
2011-07-27 12:36:30 [7256] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-27 12:36:30 [7256] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-27 12:36:30 [7256] Going into emergency mode
2011-07-27 12:36:31 [7252] ending emergency mode, stdin empty
2011-07-27 12:36:31 [7255] ending emergency mode, stdin empty
2011-07-27 12:36:31 [7253] ending emergency mode, stdin empty
2011-07-27 12:36:31 [7256] ending emergency mode, stdin empty
2011-07-27 12:36:31 [7254] ending emergency mode, stdin empty
2011-07-27 13:01:13 [1090] New setting: dbhome: /var/lib/squidguard/db
2011-07-27 13:01:13 [1093] New setting: dbhome: /var/lib/squidguard/db
2011-07-27 13:01:13 [1090] New setting: logdir: /var/log/squid
2011-07-27 13:01:13 [1093] New setting: logdir: /var/log/squid
2011-07-27 13:01:13 [1093] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-27 13:01:13 [1090] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-27 13:01:13 [1091] New setting: dbhome: /var/lib/squidguard/db
2011-07-27 13:01:13 [1094] New setting: dbhome: /var/lib/squidguard/db
2011-07-27 13:01:13 [1092] New setting: dbhome: /var/lib/squidguard/db
2011-07-27 13:01:13 [1094] New setting: logdir: /var/log/squid
2011-07-27 13:01:13 [1092] New setting: logdir: /var/log/squid
2011-07-27 13:01:13 [1094] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-27 13:01:13 [1092] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-27 13:01:13 [1091] New setting: logdir: /var/log/squid
2011-07-27 13:01:13 [1091] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-27 13:01:13 [1093] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-27 13:01:13 [1092] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-27 13:01:13 [1093] Going into emergency mode
2011-07-27 13:01:13 [1092] Going into emergency mode
2011-07-27 13:01:13 [1094] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-27 13:01:13 [1090] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-27 13:01:13 [1094] Going into emergency mode
2011-07-27 13:01:13 [1090] Going into emergency mode
2011-07-27 13:01:13 [1091] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-27 13:01:13 [1091] Going into emergency mode
2011-07-27 13:05:08 [2191] New setting: dbhome: /var/lib/squidguard/db
2011-07-27 13:05:08 [2191] New setting: logdir: /var/log/squid
2011-07-27 13:05:08 [2191] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-27 13:05:08 [2191] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-27 13:05:08 [2191] Going into emergency mode
2011-07-27 13:05:08 [2192] New setting: dbhome: /var/lib/squidguard/db
2011-07-27 13:05:08 [2192] New setting: logdir: /var/log/squid
2011-07-27 13:05:08 [2192] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-27 13:05:08 [2192] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-27 13:05:08 [2192] Going into emergency mode
2011-07-27 13:05:08 [2194] New setting: dbhome: /var/lib/squidguard/db
2011-07-27 13:05:08 [2194] New setting: logdir: /var/log/squid
2011-07-27 13:05:08 [2194] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-27 13:05:08 [2194] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-27 13:05:08 [2194] Going into emergency mode
2011-07-27 13:05:08 [2193] New setting: dbhome: /var/lib/squidguard/db
2011-07-27 13:05:08 [2193] New setting: logdir: /var/log/squid
2011-07-27 13:05:08 [2193] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-27 13:05:08 [2193] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-27 13:05:08 [2193] Going into emergency mode
2011-07-27 13:05:08 [2195] New setting: dbhome: /var/lib/squidguard/db
2011-07-27 13:05:08 [2195] New setting: logdir: /var/log/squid
2011-07-27 13:05:08 [2195] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-27 13:05:08 [2195] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-27 13:05:08 [2195] Going into emergency mode
2011-07-27 13:05:10 [2191] ending emergency mode, stdin empty
2011-07-27 13:05:10 [2194] ending emergency mode, stdin empty
2011-07-27 13:05:10 [2192] ending emergency mode, stdin empty
2011-07-27 13:05:10 [2195] ending emergency mode, stdin empty
2011-07-27 13:05:10 [2193] ending emergency mode, stdin empty
2011-07-27 14:07:10 [911] New setting: dbhome: /var/lib/squidguard/db
2011-07-27 14:07:10 [911] New setting: logdir: /var/log/squid
2011-07-27 14:07:10 [911] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-27 14:07:10 [913] New setting: dbhome: /var/lib/squidguard/db
2011-07-27 14:07:10 [913] New setting: logdir: /var/log/squid
2011-07-27 14:07:10 [913] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-27 14:07:10 [914] New setting: dbhome: /var/lib/squidguard/db
2011-07-27 14:07:10 [916] New setting: dbhome: /var/lib/squidguard/db
2011-07-27 14:07:10 [914] New setting: logdir: /var/log/squid
2011-07-27 14:07:10 [916] New setting: logdir: /var/log/squid
2011-07-27 14:07:10 [914] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-27 14:07:10 [916] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-27 14:07:10 [917] New setting: dbhome: /var/lib/squidguard/db
2011-07-27 14:07:10 [917] New setting: logdir: /var/log/squid
2011-07-27 14:07:10 [917] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-27 14:07:10 [913] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-27 14:07:10 [911] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-27 14:07:10 [911] Going into emergency mode
2011-07-27 14:07:10 [913] Going into emergency mode
2011-07-27 14:07:10 [914] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-27 14:07:10 [914] Going into emergency mode
2011-07-27 14:07:10 [916] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-27 14:07:10 [916] Going into emergency mode
2011-07-27 14:07:10 [917] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-27 14:07:10 [917] Going into emergency mode
2011-07-27 14:13:37 [3005] New setting: dbhome: /var/lib/squidguard/db
2011-07-27 14:13:37 [3005] New setting: logdir: /var/log/squid
2011-07-27 14:13:37 [3005] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-27 14:13:37 [3005] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-27 14:13:37 [3005] Going into emergency mode
2011-07-27 14:13:37 [3006] New setting: dbhome: /var/lib/squidguard/db
2011-07-27 14:13:37 [3006] New setting: logdir: /var/log/squid
2011-07-27 14:13:37 [3006] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-27 14:13:37 [3006] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-27 14:13:37 [3006] Going into emergency mode
2011-07-27 14:13:37 [3007] New setting: dbhome: /var/lib/squidguard/db
2011-07-27 14:13:37 [3008] New setting: dbhome: /var/lib/squidguard/db
2011-07-27 14:13:37 [3007] New setting: logdir: /var/log/squid
2011-07-27 14:13:37 [3008] New setting: logdir: /var/log/squid
2011-07-27 14:13:37 [3008] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-27 14:13:37 [3007] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-27 14:13:37 [3007] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-27 14:13:37 [3007] Going into emergency mode
2011-07-27 14:13:37 [3008] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-27 14:13:37 [3008] Going into emergency mode
2011-07-27 14:13:37 [3009] New setting: dbhome: /var/lib/squidguard/db
2011-07-27 14:13:37 [3009] New setting: logdir: /var/log/squid
2011-07-27 14:13:37 [3009] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-27 14:13:37 [3009] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-27 14:13:37 [3009] Going into emergency mode
2011-07-27 14:13:39 [3005] ending emergency mode, stdin empty
2011-07-27 14:13:39 [3007] ending emergency mode, stdin empty
2011-07-27 14:13:39 [3006] ending emergency mode, stdin empty
2011-07-27 14:13:39 [3009] ending emergency mode, stdin empty
2011-07-27 14:13:39 [3008] ending emergency mode, stdin empty
2011-07-27 14:22:57 [1128] New setting: dbhome: /var/lib/squidguard/db
2011-07-27 14:22:57 [1126] New setting: dbhome: /var/lib/squidguard/db
2011-07-27 14:22:57 [1128] New setting: logdir: /var/log/squid
2011-07-27 14:22:57 [1126] New setting: logdir: /var/log/squid
2011-07-27 14:22:57 [1128] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-27 14:22:57 [1126] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-27 14:22:57 [1129] New setting: dbhome: /var/lib/squidguard/db
2011-07-27 14:22:57 [1127] New setting: dbhome: /var/lib/squidguard/db
2011-07-27 14:22:57 [1125] New setting: dbhome: /var/lib/squidguard/db
2011-07-27 14:22:57 [1127] New setting: logdir: /var/log/squid
2011-07-27 14:22:57 [1125] New setting: logdir: /var/log/squid
2011-07-27 14:22:57 [1127] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-27 14:22:57 [1125] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-27 14:22:57 [1129] New setting: logdir: /var/log/squid
2011-07-27 14:22:57 [1129] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-27 14:22:57 [1128] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-27 14:22:57 [1128] Going into emergency mode
2011-07-27 14:22:57 [1127] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-27 14:22:57 [1127] Going into emergency mode
2011-07-27 14:22:57 [1125] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-27 14:22:57 [1125] Going into emergency mode
2011-07-27 14:22:57 [1126] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-27 14:22:57 [1126] Going into emergency mode
2011-07-27 14:22:57 [1129] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-27 14:22:57 [1129] Going into emergency mode
2011-07-27 14:28:38 [2202] New setting: dbhome: /var/lib/squidguard/db
2011-07-27 14:28:38 [2202] New setting: logdir: /var/log/squid
2011-07-27 14:28:38 [2202] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-27 14:28:38 [2202] Error db_open: No such file or directory
2011-07-27 14:28:38 [2202] Going into emergency mode
2011-07-27 22:46:04 [1125] ending emergency mode, stdin empty
2011-07-27 22:46:04 [1129] ending emergency mode, stdin empty
2011-07-27 22:46:04 [1127] ending emergency mode, stdin empty
2011-07-27 22:46:04 [1126] ending emergency mode, stdin empty
2011-07-27 22:46:04 [1128] ending emergency mode, stdin empty
2011-07-27 23:05:39 [911] New setting: dbhome: /var/lib/squidguard/db
2011-07-27 23:05:39 [911] New setting: logdir: /var/log/squid
2011-07-27 23:05:39 [911] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-27 23:05:39 [914] New setting: dbhome: /var/lib/squidguard/db
2011-07-27 23:05:39 [914] New setting: logdir: /var/log/squid
2011-07-27 23:05:39 [914] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-27 23:05:39 [915] New setting: dbhome: /var/lib/squidguard/db
2011-07-27 23:05:39 [915] New setting: logdir: /var/log/squid
2011-07-27 23:05:39 [915] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-27 23:05:39 [913] New setting: dbhome: /var/lib/squidguard/db
2011-07-27 23:05:39 [913] New setting: logdir: /var/log/squid
2011-07-27 23:05:39 [913] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-27 23:05:39 [916] New setting: dbhome: /var/lib/squidguard/db
2011-07-27 23:05:39 [916] New setting: logdir: /var/log/squid
2011-07-27 23:05:39 [916] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-27 23:05:39 [911] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-27 23:05:39 [911] Going into emergency mode
2011-07-27 23:05:39 [914] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-27 23:05:39 [914] Going into emergency mode
2011-07-27 23:05:39 [915] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-27 23:05:39 [915] Going into emergency mode
2011-07-27 23:05:39 [913] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-27 23:05:39 [913] Going into emergency mode
2011-07-27 23:05:39 [916] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-27 23:05:39 [916] Going into emergency mode
2011-07-28 01:38:34 [3980] New setting: dbhome: /var/lib/squidguard/db
2011-07-28 01:38:34 [3980] New setting: logdir: /var/log/squid
2011-07-28 01:38:34 [3980] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-28 01:38:34 [3980] Error db_open: No such file or directory
2011-07-28 01:38:34 [3980] Going into emergency mode
2011-07-28 09:26:44 [5038] New setting: dbhome: /var/lib/squidguard/db
2011-07-28 09:26:44 [5038] New setting: logdir: /var/log/squid
2011-07-28 09:26:44 [5038] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-28 09:26:44 [5038] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-28 09:26:44 [5038] Going into emergency mode
2011-07-28 09:26:44 [5040] New setting: dbhome: /var/lib/squidguard/db
2011-07-28 09:26:44 [5040] New setting: logdir: /var/log/squid
2011-07-28 09:26:44 [5040] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-28 09:26:44 [5040] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-28 09:26:44 [5040] Going into emergency mode
2011-07-28 09:26:44 [5042] New setting: dbhome: /var/lib/squidguard/db
2011-07-28 09:26:44 [5042] New setting: logdir: /var/log/squid
2011-07-28 09:26:44 [5042] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-28 09:26:44 [5042] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-28 09:26:44 [5042] Going into emergency mode
2011-07-28 09:26:44 [5041] New setting: dbhome: /var/lib/squidguard/db
2011-07-28 09:26:44 [5041] New setting: logdir: /var/log/squid
2011-07-28 09:26:44 [5041] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-28 09:26:44 [5041] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-28 09:26:44 [5041] Going into emergency mode
2011-07-28 09:26:44 [5039] New setting: dbhome: /var/lib/squidguard/db
2011-07-28 09:26:44 [5039] New setting: logdir: /var/log/squid
2011-07-28 09:26:44 [5039] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-28 09:26:44 [5039] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-28 09:26:44 [5039] Going into emergency mode
2011-07-28 09:26:46 [5039] ending emergency mode, stdin empty
2011-07-28 09:26:46 [5040] ending emergency mode, stdin empty
2011-07-28 09:26:46 [5041] ending emergency mode, stdin empty
2011-07-28 09:26:46 [5042] ending emergency mode, stdin empty
2011-07-28 09:26:46 [5038] ending emergency mode, stdin empty
2011-07-28 09:30:02 [959] New setting: dbhome: /var/lib/squidguard/db
2011-07-28 09:30:02 [959] New setting: logdir: /var/log/squid
2011-07-28 09:30:02 [959] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-28 09:30:02 [960] New setting: dbhome: /var/lib/squidguard/db
2011-07-28 09:30:02 [960] New setting: logdir: /var/log/squid
2011-07-28 09:30:02 [960] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-28 09:30:02 [962] New setting: dbhome: /var/lib/squidguard/db
2011-07-28 09:30:02 [962] New setting: logdir: /var/log/squid
2011-07-28 09:30:02 [962] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-28 09:30:02 [961] New setting: dbhome: /var/lib/squidguard/db
2011-07-28 09:30:02 [961] New setting: logdir: /var/log/squid
2011-07-28 09:30:02 [961] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-28 09:30:02 [963] New setting: dbhome: /var/lib/squidguard/db
2011-07-28 09:30:02 [963] New setting: logdir: /var/log/squid
2011-07-28 09:30:02 [963] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-28 09:30:02 [959] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-28 09:30:02 [959] Going into emergency mode
2011-07-28 09:30:02 [962] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-28 09:30:02 [962] Going into emergency mode
2011-07-28 09:30:02 [961] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-28 09:30:02 [961] Going into emergency mode
2011-07-28 09:30:02 [963] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-28 09:30:02 [963] Going into emergency mode
2011-07-28 09:30:02 [960] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-28 09:30:02 [960] Going into emergency mode
2011-07-28 17:08:31 [9132] New setting: dbhome: /var/lib/squidguard/db
2011-07-28 17:08:31 [9132] New setting: logdir: /var/log/squid
2011-07-28 17:08:31 [9132] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-28 17:08:31 [9134] New setting: dbhome: /var/lib/squidguard/db
2011-07-28 17:08:31 [9134] New setting: logdir: /var/log/squid
2011-07-28 17:08:31 [9134] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-28 17:08:31 [9132] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-28 17:08:31 [9132] Going into emergency mode
2011-07-28 17:08:31 [9134] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-28 17:08:31 [9134] Going into emergency mode
2011-07-28 17:08:31 [9136] New setting: dbhome: /var/lib/squidguard/db
2011-07-28 17:08:31 [9136] New setting: logdir: /var/log/squid
2011-07-28 17:08:31 [9136] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-28 17:08:31 [9135] New setting: dbhome: /var/lib/squidguard/db
2011-07-28 17:08:31 [9135] New setting: logdir: /var/log/squid
2011-07-28 17:08:31 [9135] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-28 17:08:31 [9136] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-28 17:08:31 [9136] Going into emergency mode
2011-07-28 17:08:31 [9135] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-28 17:08:31 [9135] Going into emergency mode
2011-07-28 17:08:31 [9133] New setting: dbhome: /var/lib/squidguard/db
2011-07-28 17:08:31 [9133] New setting: logdir: /var/log/squid
2011-07-28 17:08:31 [9133] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-28 17:08:31 [9133] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-28 17:08:31 [9133] Going into emergency mode
2011-07-28 17:08:32 [9133] ending emergency mode, stdin empty
2011-07-28 17:08:32 [9132] ending emergency mode, stdin empty
2011-07-28 17:08:32 [9134] ending emergency mode, stdin empty
2011-07-28 17:08:32 [9135] ending emergency mode, stdin empty
2011-07-28 17:08:32 [9136] ending emergency mode, stdin empty
2011-07-28 17:10:18 [1059] New setting: dbhome: /var/lib/squidguard/db
2011-07-28 17:10:18 [1059] New setting: logdir: /var/log/squid
2011-07-28 17:10:18 [1059] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-28 17:10:18 [1060] New setting: dbhome: /var/lib/squidguard/db
2011-07-28 17:10:18 [1062] New setting: dbhome: /var/lib/squidguard/db
2011-07-28 17:10:18 [1060] New setting: logdir: /var/log/squid
2011-07-28 17:10:18 [1062] New setting: logdir: /var/log/squid
2011-07-28 17:10:18 [1060] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-28 17:10:18 [1062] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-28 17:10:18 [1063] New setting: dbhome: /var/lib/squidguard/db
2011-07-28 17:10:18 [1063] New setting: logdir: /var/log/squid
2011-07-28 17:10:18 [1063] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-28 17:10:18 [1062] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-28 17:10:18 [1062] Going into emergency mode
2011-07-28 17:10:18 [1063] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-28 17:10:18 [1063] Going into emergency mode
2011-07-28 17:10:18 [1061] New setting: dbhome: /var/lib/squidguard/db
2011-07-28 17:10:18 [1061] New setting: logdir: /var/log/squid
2011-07-28 17:10:18 [1061] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-28 17:10:18 [1061] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-28 17:10:18 [1061] Going into emergency mode
2011-07-28 17:10:18 [1059] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-28 17:10:18 [1059] Going into emergency mode
2011-07-28 17:10:18 [1060] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-28 17:10:18 [1060] Going into emergency mode
2011-07-28 17:40:23 [2702] New setting: dbhome: /var/lib/squidguard/db
2011-07-28 17:40:23 [2702] New setting: logdir: /var/log/squid
2011-07-28 17:40:23 [2702] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-28 17:40:23 [2702] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-28 17:40:23 [2702] Going into emergency mode
2011-07-28 17:40:23 [2703] New setting: dbhome: /var/lib/squidguard/db
2011-07-28 17:40:23 [2703] New setting: logdir: /var/log/squid
2011-07-28 17:40:23 [2703] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-28 17:40:23 [2704] New setting: dbhome: /var/lib/squidguard/db
2011-07-28 17:40:23 [2704] New setting: logdir: /var/log/squid
2011-07-28 17:40:23 [2704] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-28 17:40:23 [2703] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-28 17:40:23 [2703] Going into emergency mode
2011-07-28 17:40:23 [2704] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-28 17:40:23 [2704] Going into emergency mode
2011-07-28 17:40:23 [2705] New setting: dbhome: /var/lib/squidguard/db
2011-07-28 17:40:23 [2705] New setting: logdir: /var/log/squid
2011-07-28 17:40:23 [2705] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-28 17:40:23 [2706] New setting: dbhome: /var/lib/squidguard/db
2011-07-28 17:40:23 [2706] New setting: logdir: /var/log/squid
2011-07-28 17:40:23 [2706] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-28 17:40:23 [2705] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-28 17:40:23 [2705] Going into emergency mode
2011-07-28 17:40:23 [2706] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-28 17:40:23 [2706] Going into emergency mode
2011-07-28 17:40:25 [2702] ending emergency mode, stdin empty
2011-07-28 17:40:25 [2705] ending emergency mode, stdin empty
2011-07-28 17:40:25 [2703] ending emergency mode, stdin empty
2011-07-28 17:40:25 [2704] ending emergency mode, stdin empty
2011-07-28 17:40:25 [2706] ending emergency mode, stdin empty
2011-07-28 22:36:20 [1027] New setting: dbhome: /var/lib/squidguard/db
2011-07-28 22:36:20 [1027] New setting: logdir: /var/log/squid
2011-07-28 22:36:20 [1027] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-28 22:36:20 [1029] New setting: dbhome: /var/lib/squidguard/db
2011-07-28 22:36:20 [1029] New setting: logdir: /var/log/squid
2011-07-28 22:36:20 [1029] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-28 22:36:20 [1030] New setting: dbhome: /var/lib/squidguard/db
2011-07-28 22:36:20 [1031] New setting: dbhome: /var/lib/squidguard/db
2011-07-28 22:36:20 [1030] New setting: logdir: /var/log/squid
2011-07-28 22:36:20 [1031] New setting: logdir: /var/log/squid
2011-07-28 22:36:20 [1030] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-28 22:36:20 [1031] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-28 22:36:20 [1031] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-28 22:36:20 [1031] Going into emergency mode
2011-07-28 22:36:20 [1032] New setting: dbhome: /var/lib/squidguard/db
2011-07-28 22:36:20 [1032] New setting: logdir: /var/log/squid
2011-07-28 22:36:20 [1032] init domainlist /var/lib/squidguard/db/porn/domains
2011-07-28 22:36:20 [1032] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-28 22:36:20 [1032] Going into emergency mode
2011-07-28 22:36:20 [1027] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-28 22:36:20 [1027] Going into emergency mode
2011-07-28 22:36:20 [1029] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-28 22:36:20 [1029] Going into emergency mode
2011-07-28 22:36:20 [1030] /var/lib/squidguard/db/porn/domains: No such file or directory
2011-07-28 22:36:20 [1030] Going into emergency mode
```

---


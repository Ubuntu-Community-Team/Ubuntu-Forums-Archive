---
title: "PAN server connections"
date: 2009-07-10
forum: General Help
---

### Post by MakTheKnife on 2009-07-10
By default, PAN sets the number of connections for a server to 3. If I try to increase this value I can't. If I type in a value of let's say 10, when I come back into the server settings the value is reset to 3. I figured I manually override this value and edited the servers.xml file. I set the value for "connection-limit" to 10 and saved the file. When I start PAN, it doesn't read the config file but replaces the 10 with the default 3. This is driving me nuts. my provider allows me 20 connections and I'm stuck with 3. Even with 3 PAN only uses one connection to download files. It'll start a second connection but only when the first download is just about finished.

Does anyone know how to permanently set the maximum number of connections?

Thanking everyone in advance.

MakTheKnife

---

### Post by DeMus on 2009-11-15
> **MakTheKnife said:**
> By default, PAN sets the number of connections for a server to 3. If I try to increase this value I can't. If I type in a value of let's say 10, when I come back into the server settings the value is reset to 3. I figured I manually override this value and edited the servers.xml file. I set the value for "connection-limit" to 10 and saved the file. When I start PAN, it doesn't read the config file but replaces the 10 with the default 3. This is driving me nuts. my provider allows me 20 connections and I'm stuck with 3. Even with 3 PAN only uses one connection to download files. It'll start a second connection but only when the first download is just about finished.

Does anyone know how to permanently set the maximum number of connections?

Thanking everyone in advance.

MakTheKnife

I realize it is an old post already, but I just saw it. I was looking for a reason why Pan occasionally stops working and saw your thread.
I have edited the servers.xml file in .pan2 manually and filled it 8 connections. When I start Pan it does use the 8 connections. Why that does not work for you remains a question. You did change it when Pan was not running, did you?
When you write it uses only 1 connection, you are wrong about that. It does use (in your case) 3 connections, but all on the same file it is downloading. I know on Windows when using Grabbit it downloads multiple files at the same time, each with 1/3 (1/8, 1/10 depending on the amount of connections) of the maximum download speed. Pan uses all connections on the same file and thus downloads that file faster. When you take a look at the download window it says:
```
Running - 55% Done - 00:00:45 Remaining (8 @ 1435KiB/s) - /home/user/pan
```
I can use 8 as maximum and it works.

---


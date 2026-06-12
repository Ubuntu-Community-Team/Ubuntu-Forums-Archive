---
title: "Teamspeak Server using normal User"
date: 2011-10-14
forum: General Help
---

### Post by oolfloo on 2011-10-14
Hey there!

I've got a quite easy problem for you, but it's still too hard for me... ;)

I've set up a TeamSpeak 3 Server today on my Ubuntu 10.04 Server.
To install this server I created a new user named "teamspeak". I extracted and installed everything using this user.

Now I want to start the Server. If I execute it using the "teamspeak" user, I get the message: "[...]TeamSpeak 3 server started[...]". But the Server doesn't work.

If I start the same file as root, everything works fine...

The logfile says:
```
2011-10-14 18:38:38.822101|INFO    |ServerLibPriv |   | Server Version: 3.0.0 [Build: 14957], Linux
2011-10-14 18:38:38.822385|INFO    |DatabaseQuery |   | dbPlugin name:    SQLite3 plugin, Version 2, (c)TeamSpeak Systems GmbH
2011-10-14 18:38:38.822413|INFO    |DatabaseQuery |   | dbPlugin version: 3.7.3
2011-10-14 18:38:38.822692|INFO    |DatabaseQuery |   | checking database integrity (may take a while)
2011-10-14 18:38:38.847477|INFO    |SQL           |   | pruning old database log entries where timestamp is older than 90 days
2011-10-14 18:38:38.859845|WARNING |Accounting    |   | Unable to find valid license key, falling back to limited functionality
2011-10-14 18:38:38.861017|ERROR   |Accounting    |   | failed to register local accounting service
2011-10-14 18:38:38.861045|ERROR   |ServerLibPriv |   | Server() error while starting servermanager, error: instance check error

```

I think that this is a simple problem of rights, but I'm not sure. Do you got any suggestion what I should change?

-floo ;)

---


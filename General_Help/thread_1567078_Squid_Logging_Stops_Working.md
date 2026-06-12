---
title: "Squid Logging Stops Working"
date: 2010-09-03
forum: General Help
---

### Post by Briffy on 2010-09-03
Hey there,

I'm running a squid proxy server on my installation and the logging all works fine; I get an entry in the access.log file generated everytime a traffic request is made.

So that's all wonderful and I'm happy.

The problem I'm having, however, is that I would like to delete certain entries in the log file based on a string. I've used sed to do this and it appears to work (the lines containing the string are deleted).

However, I've noticed that once sed is run on the access.log file, squid just stops logging. When I run the sed command on the file, any HTTP requests after that point do not get logged unless I restart squid.

I'm guessing this is something to do with sed locking the file for writing, though I'm not nearly advanced enough to understand much about that.

Does anyone here have any ideas?

---


---
title: "firefox doesn't seem to start"
date: 2012-05-20
forum: General Help
---

### Post by sebinbenjamin on 2012-05-20
I get this when i run in terminal

sebin@sebin-desktop:~$ firefox
15952589187 > 2421269950
CHECK IS 2161104738
Inconsistency detected by ld.so: dl-open.c: 667: _dl_open: Assertion `_dl_debug_initialize (0, args.nsid)->r_state == RT_CONSISTENT' failed!

sebin@sebin-desktop:~$ /usr/bin/firefox
15952624285 > 2421269950
CHECK IS 2161587318
Inconsistency detected by ld.so: dl-open.c: 667: _dl_open: Assertion `_dl_debug_initialize (0, args.nsid)->r_state == RT_CONSISTENT' failed!

---

### Post by carl4926 on 2012-05-20
Are you actually using Ubuntu 9.10?

---

### Post by hansdown on 2012-05-20
Hi, sebinbenjamin.

Could you please provide some info?

1-Which version of ubuntu are you running?

2-Is it a 32bit or 64bit system?

3-Do you have skype installed?

Thanks.

---

### Post by sebinbenjamin on 2012-05-20
I'm using Ubuntu  12.04 32- bit (i can't find how to update it here).  Yes I have installed skype.

---

### Post by sebinbenjamin on 2012-05-20
Problem kinda solved :-  when I made another profile and  copied files to new profile.


Thanks.

---

### Post by hansdown on 2012-05-21
> **sebinbenjamin said:**
> Problem kinda solved :-  when I made another profile and  copied files to new profile.


Thanks.

You're doing better than I am, sebinbenjamin.

I've been looking at the error message, 'till my eyes hurt.

There are bug reports, and many other matches, but nothing exactly matching.

I only asked about skype, because it popped up so many times.

Maybe I'm missing the right solution?

[http://duckduckgo.com/?q=15952589187+%3E+2421269950+CHECK+IS+2161104738+Inconsistency+detected+by+ld.so%3A+dl-open.c%3A+667%3A+_dl_open%3A+Assertion+%60_dl_debug_initialize+%280%2C+args.nsid%29-%3Er_state+%3D%3D+RT_CONSISTENT%27+failed](http://duckduckgo.com/?q=15952589187+%3E+2421269950+CHECK+IS+2161104738+Inconsistency+detected+by+ld.so%3A+dl-open.c%3A+667%3A+_dl_open%3A+Assertion+%60_dl_debug_initialize+%280%2C+args.nsid%29-%3Er_state+%3D%3D+RT_CONSISTENT%27+failed)!

---

### Post by sebinbenjamin on 2012-05-21
Problem solved if you can get firefox started in a new profile.

firefox -P should start firefox profile manager.

Make a new Profile and then if firefox start properly, then you can just copy most of the old data (bookmarks, auto-complete, passwords etc).

[http://support.mozilla.org/en-US/kb/Recovering%20important%20data%20from%20an%20old%20profile](http://support.mozilla.org/en-US/kb/Recovering%20important%20data%20from%20an%20old%20profile) tells everything in detail.

Best of Luck !

---

### Post by hansdown on 2012-05-21
Glad you fixed it, sebinbenjamin.

---


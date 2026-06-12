---
title: "Perl processes, run by www-data"
date: 2006-02-19
forum: General Help
---

### Post by IYY on 2006-02-19
When I run top, the first process in the list is:

```
28980 www-data  35  10  4924 3324 1652 R 98.3  1.7 500:01.47 perl
```

Sometimes there's more than one, but the %CPU is always very high. They are always run by the user www-data.

I've played around with perl and apache once, but right now none of this shouldn't be running. I can't kill it, even with sudo.

My question: why is this happening, and how do I get rid of it?

---

### Post by darth_vector on 2006-02-19
is apache still installed and set to run at boot time? try```
ls /etc/rc* | grep apache
```to check. if it is being started at boot time, you will have to remove the simlinks to apache from the /etc/rc* directories.

---

### Post by IYY on 2006-02-19
This grep returns nothing, and I'm not surprised because I already uninstalled apache.

---

### Post by darth_vector on 2006-02-19
thats odd. you could remove the www-data user. other than that, you may need someone else's help.

you will probably get more help in the servers forum, by the way.

---

### Post by IYY on 2006-02-19
Is the www-data user needed for anything else?

---

### Post by darth_vector on 2006-02-19
no, it should not be.

---

### Post by IYY on 2006-02-19
Even if I remove the user, how can I kill the process? 'sudo killall perl' doesn't work, and neither does 'sudo kill 28980'.

---

### Post by darth_vector on 2006-02-19
kill is used to send a signal to a process; it doesn't necessarily terminate a process. to send this process a kill signal you will have to```
sudo kill -9 PID
```

---

### Post by IYY on 2006-02-19
There we go.... Thanks!

---

### Post by Blues- on 2006-02-28
I'm having the same issues .. 
multiple processes running perl on the www-data account ..
and they are all taking up my CPU ..

I'm running some websites on my server so remove-ing apache is not an option.  I haven't changed anything on my box for weeks, then suddenly this behavior started 1 week ago and has been going on since .. even if i reboot the box .. the processes start coming about 1 day later ..

Any clues what might be causing this ?

---

### Post by Blues- on 2006-02-28
Found it ..
Mambo exploit on my machine ...
not the first one ...

---

### Post by IYY on 2006-03-06
Mind elaborating on that? I fixed my problem by removing the www-data user, but I'd still like to know what it was. I think it's the same problem, since I also ran Mambo.

---

### Post by brownrl on 2007-06-22
Have the same problem here too.

Disabled the site that was using mambo and it seems to go now.

Apparently, no surprise to me, Mambo is just as bad if not worse than phpBB for exploits and hacks.

Needless to say my client is not happy that I disabled their site until they use a new version of mambo or a different system.

The exploit that was running on my machine was some kind of click fraud bot  for getting more clicks to a site shopperuk.com

Regs
Rob

---


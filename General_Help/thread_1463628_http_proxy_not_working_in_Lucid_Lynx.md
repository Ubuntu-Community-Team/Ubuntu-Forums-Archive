---
title: "http_proxy not working in Lucid Lynx"
date: 2010-04-27
forum: General Help
---

### Post by crh0831 on 2010-04-27
Hello all,

I upgraded from Karmic to Lucid yesterday and today today I've noticed that I can no longer apt-get update through the terminal.  I'm behind a corporate firewall, so up till now I've always exported the proxy address like so:
```
export http_proxy=http://user:password@address:port
```This hasn't worked under Lucid.  I did some searching and found that Lucid did away with /etc/apt/apt.conf so the way proxies are handled changes as well.  I'll admit that I know very little beyond what has always worked for me.

I'm also aware that I've jumped on the Lucid bandwagon a little early - but I've installed it at home and without needing to export the proxy, it works very well!

Has anyone seen/dealt with this yet?  Any advice?

---

### Post by crh0831 on 2010-04-27
OK... I may have figured this one out: 
adding
```
export http_proxy="http://user:password@address:port"
```to the bottom of /etc/bash.bashrc allows me to apt-get update and apt-get upgrade but only from a root terminal window (it doesn't work from a user window with sudo)

I then added the same line to my local .bashrc (~/.bashrc) and was able to perform other internet functions ('wget' is the only one I tested) from a user terminal.  But still no apt-get update/upgrade.

I suppose this may be the intended behavior.  It's just not the way I've been doing it up until now.  Either way - I hope this helps someone else.

---

### Post by gmargo on 2010-04-27
When you run something using **sudo(1)**, the shell /bin/sh is used, which is actually /bin/dash, not /bin/bash.  So /etc/bash.bashrc is not used.  Try putting your environment variable in a script under /etc/profile.d/ (with filename ending with .sh).  [Note: see /etc/profile which is the script that runs those other scripts.]

---

### Post by robofish on 2010-07-15
I know this is kind of an old thread but I'm having a similar problem.

I just upgraded to Lucid Server and I can't even ping an outside site.  With 9.10 I had no problems so I know it's not network related.  Does anyone have a fix?

---

### Post by kdogksu on 2010-09-14
I just encountered this problem, too.  The Sudo settings are configured such that they clear all environment variables for the sudo command.  To fix this, you need to edit /etc/sudoers, run:
```

sudo visudo

```

Mine has this line in it that resets the environment:
> 
Defaults        env_reset


I added another line immediately after it to keep the http_proxy and ftp_proxy environment variables for the sudo command:
> 
Defaults        env_keep = "http_proxy ftp_proxy"


After making this change, apt started working for me.

visudo requires you to be familiar with vi.  I am unsure if it is okay to edit it with another editor, but a comment at the top of the file insists that you use visudo.  If you don't know how to use vi, follow these instructions after running visudo:

[LIST=1]
[*]Press 'g' twice to go to the top of the file
[*]Press 'j' until the cursor is on the "Defaults  env_reset" line
[*]Press 'y' twice to "yank" (copy) the line
[*]press 'p' to paste a copy of the line
[*]press 'w' until the cursor is on the 'e' in "env_reset"
[*]press 'C' (capital!) to change the rest of the line
[*]type ```
env_keep = "http_proxy ftp_proxy"
```
[*]press 'ESC' (the escape key) to stop inserting text
[*]type ':wq' to write (save) the file and quit
[/LIST]

---

### Post by Harpette on 2010-10-26
How about this : ```
$ echo 'Acquire::http { Proxy "http://user:password@address:port"; };' | sudo tee /etc/apt/apt.conf.d/02proxy
```

---


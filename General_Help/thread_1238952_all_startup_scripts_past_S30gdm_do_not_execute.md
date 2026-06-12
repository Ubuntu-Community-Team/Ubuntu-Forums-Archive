---
title: "all startup scripts past S30gdm do not execute"
date: 2009-08-13
forum: General Help
---

### Post by noahwallach on 2009-08-13
HI List,

my startup scripts are not executing scripts past S30gdm.  So I put a line /sbin/sulogin in the script and finally figured out where the script is hanging and never returning.  How can I cure the problem?

---- snip ---

                start-stop-daemon --start --quiet --oknodo --pidfile $PIDFILE --name gdm $SSD_ARG -- $CONFIG_FILE >/dev/null 2>&1 || log_end_msg 1

--- snip ---

What is the Best approach for allowing the start-stop-daemon to execute while allowing the script to continue?

~$ ps -auxww | grep S30
Warning: bad ps syntax, perhaps a bogus '-'? See
[http://procps.sf.net/faq.html](http://procps.sf.net/faq.html)
root      3246  0.0  0.0   1872   584 ?        S    12:25   0:00 /bin/sh
/etc/rc2.d/S30gdm start
root      3662  0.0  0.4  26724 16316 ?        S    14:07   0:01 emacs
/etc/rc2.d/S30gdm
noah      4034  0.0  0.0   3376   908 pts/2    S+   17:44   0:00 less
/etc/rc2.d/S30gdm
noah      4156  0.0  0.0   3340   808 pts/3    S+   18:30   0:00 grep S30

Cheers,

Noah

---


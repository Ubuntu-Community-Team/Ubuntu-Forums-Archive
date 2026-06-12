---
title: "start program at bootup"
date: 2006-01-25
forum: General Help
---

### Post by wonko on 2006-01-25
How do I make the noip2 - client start at bootup? But I cant find any folder rc2.d in init.d.. This is what the howto says:

The noip2 executable can be run by typing /usr/local/bin/noip2

If you want it to run automatically when the machine is booted, then
place the following script in your startup directory. (/etc/init.d/rcX.d
or /sbin/init.d/rcX.d or ???)

        #######################################################
        #! /bin/sh
        # . /etc/rc.d/init.d/functions  # uncomment/modify for your killproc
        case "$1" in
            start)
                echo "Starting noip2."
                /usr/local/bin/noip2
            ;;
            stop)
                echo -n "Shutting down noip2."
                killproc -TERM /usr/local/bin/noip2
            ;;
            *)
                echo "Usage: $0 {start|stop}"
                exit 1
        esac
        exit 0
        #######################################################

Where the 'X' in rcX.d is the value obtained by running the
following command
        grep initdefault /etc/inittab | awk -F: '{print $2}'

Killproc can be downloaded from [ftp://ftp.suse.com/pub/projects/init](ftp://ftp.suse.com/pub/projects/init)
Alternatively, you can uncomment the line after #! /bin/sh

---

### Post by Titus A Duxass on 2006-01-25
Normally you copy the script into your /etc/init.d directory and then run this command:

update-rc.d ???? defaults.

Where ???? is the name of your script.

It should give you a report about runlevels, etc.

I used the same commands to get a server working at boot. But it bypasses the user logon.

Let us know if it helped.

---

### Post by wonko on 2006-01-29
Thanks a lot! Seems to work perfectly :D

---


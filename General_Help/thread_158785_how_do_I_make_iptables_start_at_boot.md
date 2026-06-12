---
title: "how do I make iptables start at boot ?"
date: 2006-04-11
forum: General Help
---

### Post by albox on 2006-04-11
Hello,
I would like to know how do I make iptables start at boot ?
I tried to call my script with /etc/profile but It doesn't work when I'm not logged as root :
"iptables v1.3.1: can't initialize iptables table `filter': Permission denied (you must be root)"

Can you tell me how to do ?

Thank you ;-)

---

### Post by shame on 2006-04-11
Does it work if you are already logged in as user and run it from the command line as sudo?
Maybe put the script in /etc/init.d and do ```
sudo update-rc.d scriptname defaults xx
```
Where xx is how early/late you want it to start in the boot process.

---

### Post by albox on 2006-04-12
> Does it work if you are already logged in as user and run it from the command line as sudo?
Yes, it works but It's not what I want.

> sudo update-rc.d scriptname defaults xx
It should have a better solution. Moreover, I'm not sure it will work since it needs the root's pass.

---

### Post by shame on 2006-04-12
updaterc.d should work because it's run on boot like any other boot process.  Maybe do update-rc.d on iptables itself?
I thought iptables was automatically started on boot anyway, is your script trying to start it a second time?  If so it would need iptables restart.
I'm not entirely sure what it is you're trying to do but would firehol be any good? - [http://firehol.sourceforge.net/](http://firehol.sourceforge.net/)
> FireHOL, the iptables stateful packet filtering firewall builder
I use it myself and add any iptables commands to it's config file.

---

### Post by frodon on 2006-04-12
[QUOTE=albox]It should have a better solution. Moreover, I'm not sure it will work since it needs the root's pass.[/QUOTE]A better solution than starting your script on boot ? update-rc need to be run as root once, after that your script will be automaticaly run on boot, isn't it what you want ?

In addition iptables commands always need root rights to be run.

see the guide i'm writing to find an elegant way to use iptables scripts : [http://doc.gwos.org/index.php/IptablesFirewall](http://doc.gwos.org/index.php/IptablesFirewall)

---

### Post by albox on 2006-04-12
Indeed. It's exactly what I wanted. Sorry, I didn't understand how it works but it's Ok now.
Thanks !!! ;)

---

### Post by albox on 2006-04-12
I have one more question. Do you think I need to do something when the service is stopped ?

```
        case "$1" in
        start)
                # Start daemons.
                echo -n "Starting firewall"
                firewall.sh # calls my script with my iptables rules
                ;;
          stop)
                # Stop daemons.
                echo -n "Shutting down firewall"
                echo -n "Nothing to do ?"
                ;;
          *)
                echo "Usage: X {start|stop}"
                exit 1
        esac
```

---

### Post by frodon on 2006-04-13
To stop the firewall you need to delete all the rules and chains it's called a flush script.
Have a look in the script section of my guide, you will find the init.d script and the flush script, just cut and paste them form the guide all is explained.
[http://doc.gwos.org/index.php/IptablesFirewall](http://doc.gwos.org/index.php/IptablesFirewall)

---

### Post by albox on 2006-04-13
Ok ;-)
Thanks !

---


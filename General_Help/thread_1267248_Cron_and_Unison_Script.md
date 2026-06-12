---
title: "Cron and Unison Script"
date: 2009-09-15
forum: General Help
---

### Post by ferarg on 2009-09-15
Hi, I was reading all helps about how to configure Unison to work with cron, but was impossible for me.

I write a simple script to use unison profile to syncronize my data:

---------------------------------------------------
#!/bin/bash
server1="192.168.1.2"
server2="172.16.1.2"
perfil="profile.prf"

unison="$(which unison)"
if ping -c 1 $server1
        then
        $unison $perfil
elif ping -c 1 $server2
        then
        $unison $perfil
else
        echo "No tiene Acceso al Server"
fi
date >> unison-script.log
---------------------------------------------------

If I run this script from shell, it's do the work, but if I run this script from CRON, doesn't work the "unison" part, but the last line, the "log" work Ok.

why??

Thanks for your help or ideas!

---

### Post by CoolHand on 2009-09-15
Couple of ideas for you.  I'm not sure why it fails but I have seen this sort of thing before.  Do you have a local MTA set up so cron can mail you errors?  This may help figure it out.  

Asside from that check the cron environment.  In particular make sure to set the path in there so it has all the same destinations you have.  It may be as simple as the "which" command not finding your program in the path.  Remember that when cron runs it doesn't use the exact environment of the user.  Hope that helps.

---

### Post by ferarg on 2009-09-15
Hi, thanks for you reply, but the script work ok if I use the :

./unison-script.sh

and don't give me any error

---

### Post by CoolHand on 2009-09-15
> **ferarg said:**
> Hi, thanks for you reply, but the script work ok if I use the :

./unison-script.sh

and don't give me any error

Yes that is my point.  When you do that you are executing the script with your environment not the cron environment.  They are not the same.  In your term if you do echo $PATH you will see your path.  Cron does not have that path unless you set it.  Try setting these in your crontab:

SHELL=/bin/bash
PATH=/home/dweber/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

Then see if it makes a difference.

---

### Post by ferarg on 2009-09-15
Hi, thanks again.

I copy&paste the "path" but no luck.

I try to execute unison direct from cron:

*/2 * * * * /usr/bin/unison -batch profile.prf 

or

*/2 * * * * /usr/bin/unison profile.prf 

without any script and nothing, dont work!

---

### Post by DaithiF on 2009-09-15
Hi,
try putting:
```
MAILTO=""

```
at the top of your crontab

There is an issue in Ubuntu with cronjobs which generate a lot of output.  Cron tries to mail output to the user, but since there is no MTA (mail transfer agent) installed by default on Ubuntu desktop this output has nowhere to and when output is more than a certain buffer threshold the result is the command failing.  Setting MAILTO to "" effectively turns off the mailing of output behaviour.

---

### Post by ferarg on 2009-09-16
Thanks all of you for your help, this I can resolve it only with your ideas.

Now I tell you what I did to run UNISON script correctly from CRON:

1- install mailx (to watch the cron error)
2- redirect all script outpoot to a "log file" (to watch if this give me some idea)
3- activate cron logs in /etc/syslog.conf

With all this, the "error" was that the "'/home/ferarg/.ssh/id_rsa" has a 755 permission, and for CRON this is "TOO OPEN", then I changed the permissions to 700 and all run correctly.

Thanks for all your help!!!

---


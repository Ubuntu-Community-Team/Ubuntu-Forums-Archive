---
title: "Icinga running, how to get notified?"
date: 2010-03-25
forum: General Help
---

### Post by k-bl on 2010-03-25
I have Icinga running on 9.04 perfectly (I used the quickstart guide), with one exception, I would like to get email notifications.  The default commands are as follows, and I was hoping you guys could point me they way to change them to what I need.

```

/usr/bin/printf "%b" "***** Icinga *****\n\nNotification Type: $NOTIFICATIONTYPE$\nHost: $HOSTNAME$\nState: $HOSTSTATE$\nAddress: $HOSTADDRESS$\nInfo: $HOSTOUTPUT$\n\nDate/Time: $LONGDATETIME$\n" | /bin/mail -s "** $NOTIFICATIONTYPE$ Host Alert: $HOSTNAME$ is $HOSTSTATE$ **" $CONTACTEMAIL$

```

What would be the appropriate command to forward the mail to a gmail account?
I have postfix installed, and tested, it works fine.  I'm still in the intermediate linux desktop user migrating over to server.

Thanks Guys!

---

### Post by k-bl on 2010-03-25
I can get sendmail to work fine, but how to I automatically insert a Ctrl+D at the end, or tell it to send a specific message with a single command?

---

### Post by k-bl on 2010-03-25
Got it,  just replace all "/bin/mail" with "/usr/bin/mailx" and this should work just fine...

It is nice to be able to answer your own questions :)

---

### Post by martinkou on 2011-12-01
Except what you said, (change /bin/mail to /usr/bin/mailx)
 
also need to change the mail address in /usr/local/icinga/etc/objects/contacts.cfg
 
Is there need to add any definitions to host or service? *.cfg
 
Caused I am also install the postfix, and works with command. Now, the question is how to start the notifications by Icinga.
 
Thanks for your help.

---

### Post by Habitual on 2011-12-01
> **martinkou said:**
> ...Is there need to add any definitions to host or service? *.cfg...

Oh God, Yes!

Postfix is what I use on my icinga server. Yes, you can forward/send the notices to a gmail account.

Here's what I use/suggest...
you should have a /usr/local/icinga/etc/objects directory.
**Stick your handcrafted cfg files there and include them them in /usr/local/icinga/etc/icinga.cfg**,
(*one cfg for every server/host/target*) like so...
(it doesn't matter where in the /usr/local/icinga/etc/icinga.cfg file, but I usually include them at the bottom with some 
### "My Edits start here" type comments.)

Here's a real-life example
(from my own /usr/local/icinga/etc/icinga.cfg...)
```
### ftb Linux Server.
cfg_file=/usr/local/icinga/etc/objects/findthebest.cfg
```

Then my /usr/local/icinga/etc/objects/findthebest.cfg contains:
```

###############################################################################
###############################################################################
#
# CONTACTS
#
###############################################################################
###############################################################################
define contact{
        contact_name                    admins                 ; Short name of user
        use                             generic-contact             ; Inherit default values from generic-contact template (defined above)
        alias                           Martin the Admin           ; Full name of user
        email                           [COLOR="Red"]user@gmail.com[/COLOR]       ; Who is getting emails about this server?
}

define contactgroup{
        contactgroup_name       admins
        alias                   Admins
        members                 admins
        }

###############################################################################
###############################################################################
#
# HOSTS
#
###############################################################################
###############################################################################
define host{
        use             linux-server  	; hostgroup-name "Template".
        host_name       _findthebest_	    ; The name we're giving to this host
        alias           _findthebest_	    ; A longer name associated with the host
        address         _xxx.xxx.xx.xx_   ; IP address of the host
}

###############################################################################
###############################################################################
#
# SERVICES
#
###############################################################################
###############################################################################
define service{
        use                     generic-service
        host_name               _findthebest_
        service_description     HTTP
        check_command           check_http #Generic Apache/80 check
}

define service{
        use                     generic-service
        host_name               _findthebest_
        service_description     CPU Load
        check_command           check_nrpe!check_load -a "-w 15,10,5" "-c 30,25,20" # check load
        }
define service{
        use                     generic-service
        host_name               _findthebest_
        service_description     Disk Space
        check_command           check_disk!/dev/sda1 # Check Disk space...
        }

```

then in /usr/local/icinga/etc/objects/contacts.cfg:
```

###############################################################################
###############################################################################
#
# CONTACTS
#
###############################################################################
###############################################################################
# Just one contact defined by default - the Icinga admin (that's you)
# This contact definition inherits a lot of default values from the 'generic-contact' 
# template which is defined elsewhere.

define contact{
        contact_name                    icingaadmin		
	use				generic-contact		
        alias                           Icinga Admin		
        email                           [COLOR="Red"]_user@gmail.com_[/COLOR]	
        }
###############################################################################
###############################################################################
#
# CONTACT GROUPS
#
###############################################################################
###############################################################################

# We only have one contact in this simple configuration file, so there is
# no need to create more than one contact group.

define contactgroup{
        contactgroup_name       admins
        alias                   Icinga Administrators
        members                 icingaadmin
        }


```

Finally, test your configuration before you bounce the icinga service (which you should do on every edit/save of a cfg file)
```
/usr/local/icinga/bin/icinga -v /usr/local/icinga/etc/icinga.cfg | \egrep -n "Warn|Error"
```

If it has Warnings or Errors, I'd investigate again with 
```

/usr/local/icinga/bin/icinga -v /usr/local/icinga/etc/icinga.cfg 
```
and it will show you where the error is and in what section of the config 


That should get you started.
Subscribed with interest...

HTH.

Code snippets from cfg files that need YOUR attention are _underlined_. And the [COLOR="Red"]email details are in Red[/COLOR].

Good Luck.
(last edit, I promise but this is NOT an easy task/Getting started)

---

### Post by Habitual on 2011-12-01
Martin:

Did you install any nagios-plugins?

JJ

---


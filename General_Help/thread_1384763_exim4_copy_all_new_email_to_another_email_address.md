---
title: "exim4 copy all new email to another email address"
date: 2010-01-18
forum: General Help
---

### Post by digitalexpl0it on 2010-01-18
Is there a way to configure exim4 to bcc all new incoming emails to another email address? My boss wants a copy of all outgoing emails.

I know postfix can do this with a bcc_always option. Im sure exim4 should be able to also.

any help would be appreciated.

---

### Post by digitalexpl0it on 2010-01-19
any ideas?

---

### Post by digitalexpl0it on 2010-01-19
I found that I have to use filters for this to work. [http://www.devco.net/archives/2006/03/24/saving_copies_of_all_email_using_exim.php](http://www.devco.net/archives/2006/03/24/saving_copies_of_all_email_using_exim.php)

my /etc/exim4/systemfilter.txt

> if $sender_address_domain is caltrop.com
then
unseen deliver [email]user@caltrop.com[/email]
#unseen save /var/mail/caltrop.com/mailarchive/.${tr{$sender_address}{.}{_}}.outgoing/
endif


/etc/exim4/conf.d/transport/local_copy_outgoing

> local_copy_outgoing:
driver = appendfile
delivery_date_add
envelope_to_add
return_path_add
group = exim
user = exim
mode = 0660
maildir_format = true
create_directory = true


/etc/exim4/update-exim4.conf.conf

> system_filter = /etc/exim4/systemfilter.txt
system_filter_directory_transport = local_copy_outgoing


dc_eximconfig_configtype='internet'
dc_other_hostnames='caltrop.com, localhost, 192.168.10.*, 192.168.28.*, *, caltrop.corp'
dc_local_interfaces='192.168.10.58; 192.168.10.9'
dc_readhost=''
dc_relay_domains='caltrop.com'
dc_minimaldns='false'
dc_relay_nets='192.168.10.*/24:192.168.28.*/24:127.0.0.1'
dc_smarthost='192.168.10.58'
CFILEMODE='644'
dc_use_split_config='false'
dc_hide_mailname='false'
dc_mailname_in_oh='true'
dc_localdelivery='mail_spool'



when I restart exim4 I get this error

> root@out:/etc/exim4# /etc/init.d/exim4 restart
 * Stopping MTA for restart                                                                                                                                                                              /etc/exim4/update-exim4.conf.conf: 20: system_filter: not found
root@out:/etc/exim4#


not sure why it cant find the files

---

### Post by digitalexpl0it on 2010-01-19
nevermind I have a work around

> 
#!/bin/bash
# Created by Derrick Rose

TMPFILE=/tmp/eximstats.log
LOGFILE=/var/log/exim4/mainlog
DATE=`date +%Y-%m-%d`
EMAIL=user@domain.com

## Full Log file output
eximstats -ne -nr -nt $LOGFILE > $TMPFILE

## Per day log file output
#fgrep $DATE $LOGFILE | eximstats > $TMPFILE

## Put script to sleep for 3 seconds
sleep 3

## Mail Stats
mail -s "OUT Mail Statistics" $EMAIL < $TMPFILE



set this in a cronjob

---


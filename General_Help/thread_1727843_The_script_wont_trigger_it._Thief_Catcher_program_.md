---
title: "The script wont trigger it. Thief Catcher program (open source)"
date: 2011-04-13
forum: General Help
---

### Post by Kiraichi on 2011-04-13
me and my team working on a project called Stealth Hunter,

Summarize about our project:
Stealth Hunter is a thief catcher, It will silently take a snapshot of user using a stolen notebook or pc with webcam and send the information via email.

how it work is:
The scripts will triggered by the owner itself. he or she might go to another pc, compose new email and send email to integrated email which is configured in the stealth hunter script earlier (in stolen laptop) with "STOLEN" subject email. but nothing happened. it suppose trigger the scripts, once it triggered, it automatically capture the webcam (stolen laptop) together with their ip too. but, nothing happened. maybe something wrong with it.

so, the problem is, the scripts wont trigger it. Maybe something wrong with the script? hope someone can take a look on it. Thanks.

Here's our full Stealth Hunter Scripts - [http://www.mediafire.com/?nfvv748g5](http://www.mediafire.com/?nfvv748g5)...

and this is where the main line/code (also included on link above).

```
# ! /bin/sh
### BEGIN INIT INFO
# Provides:          Stealth Hunter
# Required-Start:    $local_fs $network
# Required-Stop:     $local_fs $remote_fs
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Stealth Hunter catcher
# Description:       Stealth Hunter is a thief catcher
#                    It will silently take a snapshot of user using a stolen notebook
#           or pc with webcam and send back an email.
### END INIT INFO

# Author: shunter

CONFIGURE="No"

# Reads config file
[ -r /etc/default/shunter ] && . /etc/default/shunter


if [ $CONFIGURED != "Yes" ]; then
   echo "/etc/default/shunter not configured yet!"
   echo "Exiting ..."
   exit 0
fi

PASSWORD=$(encrypt-decrypt decode $PASS | awk '$0!~/^$/ {print $0}')

do_start()
{
ping -c 2 google.com > /dev/null 2>&1
if [ $? -eq 0 ]; then
   #echo "Checking alert mail ..."
   check_mail=$(wget -T 3 -t 1 -q --secure-protocol=TLSv1 --no-check-certificate  --user=$USER --password=$PASSWORD https://mail.google.com/mail/feed/atom -O - |grep "$ALERT")
   if [ $? -eq 0 ];
   then
      #echo "Alert mail found, this notebook/pc might been stolen!!"
      #echo "Retrieving ip adress ..."
      IP=$(wget -q -O - http://whatismyip.org |tail) && wait $!
      DATE=`date`
      #echo "Taking snapshot ..."
      mplayer tv:// -tv driver=v4l2:width=320:height=240:outfmt=uyvy:device=/dev/video0 -frames 3 -vo jpeg:outdir=/tmp >/dev/null 2>&1 && wait $!
      #echo -n "Sending mail ..."
      sendEmail -f shunter@google.com -t $USER -s $MAIL_SERV:$PORT -xu $USER -xp $PASSWORD -u $TITLE -m "$MESSAGE\nIP : $IP  DATE: $DATE\n" -a $ATTACHMENT >/dev/null
      #echo "Done."
      exit
   else
      #echo "No alert message found ..exiting."
      exit
   fi
else
   #echo "Not online ..."
   exit
fi
}


case "$1" in
  start)
   do_start
   ;;
   
  stop)
   echo "This option is not supported."
   ;;

  restart)
   echo "This option is not supported"
   ;;
    *)
        echo "Usage: /etc/init.d/$0 {start|stop|restart}"
        exit 1
        ;;

esac

exit 0
```

---


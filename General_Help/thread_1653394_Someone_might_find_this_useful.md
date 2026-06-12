---
title: "Someone might find this useful"
date: 2010-12-26
forum: General Help
---

### Post by roobinatube on 2010-12-26
Hello all,

In case someone else might find this useful, I thought I would post it here. My short script for a gmail notifier.

I wrote this mainly because I could, I know there are gmail notifiers in the repos. This is a good alternative if you dont understand fancy programming languages and like to know what is going on!

```
#!/bin/bash

############################
#        written by        #
#            ME            #
############################

while true; do 

username=your_username
# can password be stored securely? gnome keyring?
password=your_password

check="$(wget --secure-protocol=TLSv1 --no-check-certificate -q -T 5 -t 2 -O - \
https://$username:$password@mail.google.com/mail/feed/atom \
| grep fullcount | sed -e 's:.*<fullcount>::;s:</fullcount>.*::' 2>/dev/null)"

if [ "$check" -gt 1 ]
 then
  plural="s"
 else
  plural=""
fi

if [ $check -gt 0 ]
 then
  zenity --info --text="You have $check unread email$plural" --window-icon="/usr/share/icons/gnome/scalable/actions/mail-message-new.svg" &
  zenity --notification --text="$check Unread" --window-icon="/usr/share/icons/gnome/scalable/actions/mail-message-new.svg"
  prism-google-mail
  sleep 180
 else
  sleep 180
fi

done
```

You can easily change prism-google-mail for whatever you use.

There is likely to be a better way of combining the two if statements, but hey, im no pro!

Roob

EDIT - also probs better to use cronjob than sleep.

---


---
title: "RSS/Feed on Conky"
date: 2010-01-01
forum: General Help
---

### Post by Psyfurius on 2010-01-01
Hi. I just want to know if there is a way to configure conky so it can show the total of feeds unread on Google Reader. Thanks.

---

### Post by HarrisonNapper on 2010-01-08
Google may have an api for it (if it does, it probably won't work with conky directly); search for it in google code or google reader's documentations. Also, please let us (me) know if you find anything because I think that would be pretty awesome.

Cheers.

---

### Post by nichipet on 2010-06-09
Even though this thread is a few months old, I thought I would share a solution I found. It is a shell script that is executed from conky. You will need a new file for the shell script and an execi line in conky. Of course, change "user" to your Google username and "pwd" to your Google password.

Here is the shell script:
```
#!/bin/sh
SID=$(wget --output-document=- --post-data 'Email=user@googlemail.com&Passwd=pwd' -q https://www.google.com/accounts/ClientLogin | grep -w SID);
unreadcountxml=$(wget --no-cookies --header "Cookie: $SID" --output-document=- -q http://www.google.com/reader/api/0/unread-count)
unreadcount=$(echo $unreadcountxml | awk 'BEGIN {RS="<object>";FS="count\">";sum=0} ; /reading-list/ {print $2}' | cut -d'<' -f1);
echo "$unreadcount"
```

I then execute it in conky with:
```
${execi 60 ~/scripts/greader}
```

Change the location to your script and "60" to however many seconds you want between each check.

I found the script here: [http://superuser.com/questions/68159/looking-at-google-reader-from-the-bash-prompt](http://superuser.com/questions/68159/looking-at-google-reader-from-the-bash-prompt)

The only tweak I made was to trim the echo line to just the unread count.

---


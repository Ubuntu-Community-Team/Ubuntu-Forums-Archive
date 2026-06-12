---
title: "Twitter from command line"
date: 2011-02-19
forum: General Help
---

### Post by anoopm101 on 2011-02-19
curl --basic --user "username:password" --data-ascii "status=`echo $@|tr ' ' '+'`" "http://api.twitter.com/version/statuses/update.json" -o /dev/null
echo Message Sent!


this is the script im using, got from the web
its not working
is it same for others who tried it
is it bcos of auth

---

### Post by polardude1983 on 2011-02-20
Yes its because of the New O Auth that they are using. :/

---


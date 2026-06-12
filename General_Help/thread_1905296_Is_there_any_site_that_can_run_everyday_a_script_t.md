---
title: "Is there any site that can run everyday a script that i have made?"
date: 2012-01-06
forum: General Help
---

### Post by leon.vitanos on 2012-01-06
Hello! I have made a script, and i have my laptop all day running so it runs the script.. it changes every hour an image in my website so i need it to be runned every hour.. but leaving my laptop everyday running, is kinda annoying and i would like to ask, if there is any site that can run the script for u.. thanks by the way.. :(

---

### Post by Habitual on 2012-01-06
Terminal > ```
crontab -e
``` and add
```
*/60 * * * * /absolute/path/to/your/script.sh 
```


Once it works as expected you can suppress the emails with
```
*/60 * * * * /absolute/path/to/your/script.sh > /dev/null 2>&1 
```

---

### Post by leon.vitanos on 2012-01-06
You didn't understand my question.. i know how can the script run every hour by itself, i am wondering if there is a website that can run this script for me...

---

### Post by papibe on 2012-01-06
Wouldn't be the server the best place to put and run the script?

Could you tell us a little bit more about your website?

Regards.

---

### Post by QIII on 2012-01-06
Can we mention the very serious security risk posed by allowing an outside agent to have the credentials to pass through your public-facing perimeter to do something that should be happening behind your presentation layer?

There are people who get paid a lot of money to keep that from happening.

---

### Post by efflandt on 2012-01-06
Web search "free shell account".  Some of them may run some other *nix, but should be similar enough for shell or other scripts.  Some may have extra features if you make a donation.  Typically you ssh to them.  They also include web space.

One that has been around for a long time that I have not visited for years is [http://sdf.lonestar.org/](http://sdf.lonestar.org/) and I just found out they have their own minecraft server (which is a java game that works in Linux).  I forget what OS they use, but it is some *nix on Alpha servers and you should be able to do a crontab.

---

### Post by flyingfisch on 2012-01-06
Another solution wuld be to rewrite the script in PHP and do it on-server.

---

### Post by gsgleason on 2012-01-06
Either schedule a cron job on the web server itself or use a server side script on the web page to dynamically pick the picture.

---


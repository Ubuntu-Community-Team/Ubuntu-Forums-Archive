---
title: "apt-get problem"
date: 2011-12-18
forum: General Help
---

### Post by gprasanthkumar on 2011-12-18
==>I am facing a problem with "apt-get update", I have freshly installed 10.04 LTS and trying to install apache2 with "apt-get install apache2", but the console hangs with "0% [Waiting for Headers]" indefinitely, expecting that the problem with retreving only for apache I tried php5 and mysql-server but the same result is being displayed. I googled and found some solutions stating that working fine is mirrors are updated in the sources.list file which didn't worked for me, & also I tried decreasing the NIC MTU from 1500 to 1480 but still the problem persists, I re-installed OS and tried but still the same problem, but when I tried the same from another place the apt-get is working fine without any problem.

==>ping command on [www.google.com]("http://www.google.com"), [www.mail.yahoo.com]("http://www.mail.yahoo.com") are working  perfectly along with pinging to us.archive.ubuntu.com but only the  difference is the time taken to retrieve them.

 ==>Any suggestions on solving this problem will be very greatful.

---

### Post by seawolf167 on 2011-12-19
Is your internet connection working properly?

Are there any error messages from running the following commands? If you post the output in [noparse]```
 
```[/noparse] tags so we can see

```
sudo apt-get update && sudo apt-get upgrade
```

---


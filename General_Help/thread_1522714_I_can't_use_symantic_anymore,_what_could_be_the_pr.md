---
title: "I can't use symantic anymore, what could be the problem,solution?"
date: 2010-07-02
forum: General Help
---

### Post by judoka1113 on 2010-07-02
I have ubuntu 10.04 and lost the ability to use synaptech package manager.  I was able to use it yesterday and everything was fine;however, yesterday evening it stopped seing my internet connection.  I am connected to the internet I can surf the net, but when I try to use ubuntu software center it says "Failure to download package files" and in the in the details it says " cannot connect to [my ip address]:8080    ,now 8080 is the port that i remember closing like this $ sudo uwf delete allow 8080", so i tried to open it with $ sudo ufw allow 8080"  but that didn't work,  so i tried $sudo iptables -F even though i never installed firewall but that did nothing either. Can someone help please?  I really need to fix this soon.

---

### Post by yetiman64 on 2010-07-02
I'm not entirely familiar with manually editting ufw entries as you have done, but on running
```
man ufw
``` in terminal I would suggest you try
```
sudo ufw insert 8080 allow
``` and see if that reopens the port correctly. I would recommend you check this command with "man ufw" first to see how I've come up with the suggestion.

---

### Post by judoka1113 on 2010-07-02
I know that the syntax for the command to open the port is $ sudo ufw allow 8080   ,but when i do this it just says skipping adding existing rule, so the rule exists and the port 8080 is open, but I still can't download anything via symantic or ubuntu software center,  and get the same message that cannot connect to [my_ip]:8080.

---

### Post by judoka1113 on 2010-07-02
it also says connect(111:connection refused)

---

### Post by judoka1113 on 2010-07-02
I had to clear System->Preferences->Network Proxy and Restart My Computer Now it all works!

---


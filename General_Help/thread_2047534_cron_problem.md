---
title: "cron problem"
date: 2012-08-25
forum: General Help
---

### Post by CarlWalters on 2012-08-25
I've created a bash script which I can run on my home computer which will grab my external IP address and e-mail it to my gmail account.  I've done this since work has just started blocking DynDNS and I wanted a way of getting to my TiVo on my home network from work.  

Anyway the script "GetMyIP.sh" works fine when I run it from the terminal and I get a nice e-mail with my home computers external IP address in it. 

Then I thought I'd like to run it automatically, so I tried to put in a cron entry to run it at 00:30 evry day like this

crontab -e

```


# mmm  hhh  ddd  mmm  DAY   COMMAND
  30   00    *    *    *     /home/carl/RunGetMyIP.sh

```

but this doesn't seem to work.  Instead of an e-mail like theis
```

Message Begins
IP ADDRESS = XX.XX.XX.XX
Message Ends

```

I get a message 
```

/home/carl/RunGetMyIP.sh: line 18: ssmtp: command not found

```

Do I need to declare the path to ssmtp explicitly?

---

### Post by Cheesemill on 2012-08-25
> **CarlWalters said:**
> Do I need to declare the path to ssmtp explicitly?
Yes.

Crontab runs with a very limited set of environmental variables set. Giving the full path for any commands in the script should fix this.

---

### Post by CarlWalters on 2012-08-25
> **Cheesemill said:**
> Yes.

Crontab runs with a very limited set of environmental variables set. Giving the full path for any commands in the script should fix this.

Excellent!  That did the trick.  Thank you very much :)

---


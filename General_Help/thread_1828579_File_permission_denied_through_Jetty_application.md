---
title: "File permission denied through Jetty application"
date: 2011-08-19
forum: General Help
---

### Post by irsalina on 2011-08-19
Hai everyone, 

I was trying to deploy an application in /webapps in JETTY. In my program, I'll have to write and get some data from a file e.g. [SIZE=1][B][FONT=Arial]/home/isuprapt/databases/brokerdb.data

[/FONT][/B][FONT=Arial]After I run the server Jetty and the application through firefox, I can't get some data because it is said : [/FONT][/SIZE][SIZE=1]/home/isuprapt/databases/brokerdb.data (Permission denied)

Is there any setting permission I should change in Jetty? Or is there any other path that doesn't need permission access?

Thank you for your help!
[/SIZE]

---

### Post by tcsmith1978 on 2011-08-19
Does brokerdb.data have read permissions for everyone?

---

### Post by irsalina on 2011-08-19
> **tcsmith1978 said:**
> Does brokerdb.data have read permissions for everyone?

I check ls -l and it is the response:

-rw-r--r-- 1 root root 0 2011-08-19 12:54 brokerdb.data

I thought the application run in root, so it should be able to access the file, right?

---

### Post by tcsmith1978 on 2011-08-19
Curious. A couple of question tho:

1. Where is the error (permission denied) occurring? Is it in the logs or reported by the browser?

2. I'm unfamiliar with a .data file - is this just a flat data file?

3. Could you provide some code relating to how the .data file is being accessed?

Not saying I can help - but info here might trigger someone else into helping! :)

U can try ps -aux to see who is running jetty.

---


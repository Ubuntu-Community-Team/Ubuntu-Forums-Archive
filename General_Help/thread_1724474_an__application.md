---
title: "an  application"
date: 2011-04-08
forum: General Help
---

### Post by vivek.pandey on 2011-04-08
hey everyone 
   i am writing a code for an application for my ubuntu . in this application i need the list of all websites i go to every day and the duration and frequency of visit. every browser i have must have its own list of websites i went. i can get that from log file of the browser but how to get the duration of visit...?
thanx to all

---

### Post by sanguinoso on 2011-04-08
If that information isn't stored in the browser logs you may be out of luck. You might be able to pull some trickery watching the actual packets being sent.

---

### Post by vivek.pandey on 2011-04-08
ok a new question i was thinking i can get the log file /var/log but its not there !!! i know its silly but where else can i find log file of chrome and mozilla ?
thanx again to all

---

### Post by sanguinoso on 2011-04-08
Chrome and Firefox store their history in sqlite databases I believe.

---

### Post by techunit on 2011-04-08
If you are attempting to write a program to share with the community the way you go about this process is very important. If you allow them to install the application and do not put warnings about how the program works it may be suspicious and cause problems for you.

Getting the log files out of the browsers is something I can't help you with but I wanted to leave you this message as a warning.

Good Luck.

---

### Post by vivek.pandey on 2011-04-08
> **techunit said:**
> If you are attempting to write a program to share with the community the way you go about this process is very important. If you allow them to install the application and do not put warnings about how the program works it may be suspicious and cause problems for you.

Getting the log files out of the browsers is something I can't help you with but I wanted to leave you this message as a warning.

Good Luck.

i have not thought about making it available to community or not.. its just that i browse almost 100 sites a day. so i just wanna keep a kinda track of for how long did i stay at one site , when did i visited it, a link to directly go to a particular page and many other options.... well if people are interested i can make this as an open project and then if its a good app , we will try to make it public.. but right now i feel i should better do it on my own....

---

### Post by vivek.pandey on 2011-04-10
bump

---

### Post by sanguinoso on 2011-04-12
You are bumping but have not asked a further question.

---

### Post by SeijiSensei on 2011-04-12
You really should look into running a [transparent Squid proxy]("http://www.google.com/search?q=squid+transparent+proxy+ubuntu") between your local machines and the Internet.  Squid will log every object you download from the Internet.  You can get extensive reports on your activities using [SARG]("http://sarg.sourceforge.net/").

It makes a lot more sense to log things at the gateway so it doesn't matter what computer or browser you're using.

---


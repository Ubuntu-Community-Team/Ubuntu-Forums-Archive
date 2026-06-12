---
title: "Crontabs - help plz :-)"
date: 2012-04-16
forum: General Help
---

### Post by trigity on 2012-04-16
Hey everyone- 

I was hopeful someone might be able to help me to solve this little cron lab issue with me. I keep screwing it up, 

MOTD - An abbreviation for "message of the day", it had been traditionally used on Linux/UNIX systems for just that - send a message of the day to anyone logging into the system for the first time. It sits in the /etc directory. System administrators use this file to send a quick message to users at logon time.
The cron Utility
In this lab, you will use cron jobs to create three messages to your users. So, on each week, on MONDAY, do the following:

1. If users log in between 5:00PM to 5:59PM, create this login message: "Welcome to ITEC1475 - Linux System Admistration."
2. If users log in between 6:00PM and 6:59PM, create this login message: "You are late! Come to class a little early next time."
3. If users log in between 7:00PM and 8PM, create this message: "There is not much time left for class. Shouldn't you be going home instead?"

Would it look something like this:
* 17 * * 1 root echo "Welcome to ITEC1475 - Linux System Administration." > /ect/motd
* 18 * * 1 root echo "You are late! Come to class a little early next time." > /etc/motd
0-59 19 * * 1 root echo "There is not much time left for class. Shouldn't you be going home instead?" > /etc/motd

Now, will this work or would I need to create a separate file for each of these? I don't want the answers but if someone could clue me in on to what is wrong I might see it right away



Thanks in advance!!
trigity

---

### Post by dcstar on 2012-04-17
> **trigity said:**
> Hey everyone- 

I was hopeful someone might be able to help me to solve this little cron lab issue with me.
.........

The whole point about going to school is for **you** to learn how to do things, not for **others to do them for you**.

---

### Post by trigity on 2012-04-17
> **dcstar said:**
> The whole point about going to school is for **you** to learn how to do things, not for **others to do them for you**.

Could you look at what I did and clue me into what might be wrong, I did rephrase the question with my solution, but it still doesn't look right to me?? 

trigity

---


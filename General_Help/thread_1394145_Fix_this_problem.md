---
title: "Fix this problem?"
date: 2010-01-30
forum: General Help
---

### Post by PDA1 on 2010-01-30
I have to enter the following commands in Terminal every time I start Ubuntu otherwise I can't access my email via Thunderbird and other internet stuff.  No, the problem isn't with Thunderbird.  The stuff I enter is in bold.


$ **sudo -s**

/root $  password?  (Then I enter my key ring password)

root $   **iptables -F**


Or.....exactly (not theoretically) how do I create a script that'll perform the previous entries automatically when I enter the scripts file name?  (or however it's done).

---

### Post by garvinrick4 on 2010-01-30
> **PDA1 said:**
> I have to enter the following commands in Terminal every time I start Ubuntu otherwise I can't access my email via Thunderbird and other internet stuff.  No, the problem isn't with Thunderbird.  The stuff I enter is in bold.


$ **sudo -s**

/root $  password?  (Then I enter my key ring password)

root $   **iptables -F**


Or.....exactly (not theoretically) how do I create a script that'll perform the previous entries automatically when I enter the scripts file name?  (or however it's done).
Are you saying you just do not want a password, just to have everything capable of not using your password to get root capabilities.

---

### Post by JSeymour on 2010-01-30
> **PDA1 said:**
> I have to enter the following commands in Terminal every time I start Ubuntu otherwise I can't access my email via Thunderbird and other internet stuff.  No, the problem isn't with Thunderbird.  The stuff I enter is in bold.


$ **sudo -s**

/root $  password?  (Then I enter my key ring password)

root $   **iptables -F**


Or.....exactly (not theoretically) how do I create a script that'll perform the previous entries automatically when I enter the scripts file name?  (or however it's done).Why don't you fix whatever it is in your iptables config that's stopping you from getting to the mail server, instead?

Jim

---

### Post by oldfred on 2010-01-30
Man says -F is flush all entries, so you must have a "bad" entry?

My listing has nothing.
fred@fred-laptop:~$ sudo iptables -L
[sudo] password for fred: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
fred@fred-laptop:~$

---

### Post by gdonwallace on 2010-01-30
Run Thunderbird from terminal and paste the output here so we can see what is happening.  It may be something else that is causing the problem, and it is causing some errors to occur in iptables.

---

### Post by PDA1 on 2010-01-30
> **JSeymour said:**
> Why don't you fix whatever it is in your iptables config that's stopping you from getting to the mail server, instead?

Jim


Oh?  And how do I do that?

---

### Post by t4thfavor on 2010-01-30
Just sudo ufw disable then check back after a reboot.

---

### Post by PDA1 on 2010-01-30
Like I said in my post- there's nothing wrong with TB.  For whatever reason I'm blocked from accessing mail AND certain stuff on the web unless I do that sudo and iptables stuff.  Exactly what stuff?  I don't know exactly what.....but this I know- I don't want to be blocked from certain websites.

---

### Post by PDA1 on 2010-01-30
> **oldfred said:**
> Man says -F is flush all entries, so you must have a "bad" entry?

My listing has nothing.
fred@fred-laptop:~$ sudo iptables -L
[sudo] password for fred: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
fred@fred-laptop:~$


Is this supposed to mean something to me?

---

### Post by PDA1 on 2010-01-30
> **t4thfavor said:**
> Just sudo ufw disable then check back after a reboot.


What will the command you recommended do?

Will it mess up my system, leave it vulnerable to some sort of computer hack or virus?

---

### Post by PDA1 on 2010-01-30
> **t4thfavor said:**
> Just sudo ufw disable then check back after a reboot.


No difference.  Same problem.

---

### Post by PDA1 on 2010-01-30
It seems the problem is associated only with accessing sites with https in the address.

---

### Post by oldfred on 2010-01-30
Did you run the command to see what entries you have?

sudo iptables -L

---

### Post by PDA1 on 2010-01-30
Here's what I get-


earl@earl-laptop:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Chain ALLOW_MATCH (0 references)
target     prot opt source               destination         

Chain BLOCK_MATCH (0 references)
target     prot opt source               destination         

Chain INPUT_QUEUE (0 references)
target     prot opt source               destination         

Chain OUTPUT_QUEUE (0 references)
target     prot opt source               destination         
earl@earl-laptop:~$

---

### Post by JSeymour on 2010-01-31
> **PDA1 said:**
> Oh?  And how do I do that?Find the iptables rule that's blocking the traffic and remove it.  (I don't muck-about with iptables often enough to be able to tell you, off-hand, how to do that.  There are iptables tutorials on the web, tho.)


> **PDA1 said:**
> What will the command you recommended do?

Will it mess up my system, leave it vulnerable to some sort of computer hack or virus?ufw is a kind of "user friendly" (and I use the term loosely) interface to iptables.  You've been doing an "iptables -F," which whacks all your iptables rules, anyway.

> **PDA1 said:**
> Here's what I get-

earl@earl-laptop:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Chain ALLOW_MATCH (0 references)
target     prot opt source               destination         

Chain BLOCK_MATCH (0 references)
target     prot opt source               destination         

Chain INPUT_QUEUE (0 references)
target     prot opt source               destination         

Chain OUTPUT_QUEUE (0 references)
target     prot opt source               destination         
earl@earl-laptop:~$There are no rules in there.  Did you do this *before* you did the -F, or afterward?

Jim

---


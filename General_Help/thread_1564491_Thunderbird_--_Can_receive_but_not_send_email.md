---
title: "Thunderbird -- Can receive but not send email"
date: 2010-08-30
forum: General Help
---

### Post by LaughingHorse on 2010-08-30
I am having a very strange problem.

I have a desktop that has been running Ubuntu for years.
Finally I convinced my wife to get rid of windows XP and move to Lucid.

I did a clean install of Lucid on her system writing over windows.:tongue:

After the install I installed Thunderbird using Synaptic
Version 3.0.6 was installed on her system.

On my desktop I am also running Thunderbird 3.0.6

We have several domains and mail servers on those domains.

They all use SMTP 

First, I installed the ISP email and that works perfectly.
She can send and receive using our ISP's mail server.

I then set up an email account in Thunderbird using the SMTP email server form one of our domains. She used to be able to send and receive from for one of our domains.

She can receive email from that email server, but can not send :confused:

(I can send _*and*_ receive from the same domain using Thunderbird)
**Her SMTP and mine are set up identically:**

Server Name: mail.[domain]
Port: 50
Username: [user]@[domain]
Secure Authentication: No
Connection Security: No

She is able to receive email but when she tries to send... the connection in Thunderbird either times out... or gives a password error.

The password is correct, because we can use Firefox, and go to the pop and log in.
Also, she can receive email direct on her computer and has to log in using her password.

**So I opened Terminal and tested using:**

telnet mail.[domain] 50

**I got**

Trying [IP address]
Connected to mail.[domain]
Escape character is '^']'.
220 mail.[domain]

This leads me to believe something in Ubuntu is blocking her system from using Thunderbird to send emails through the email server.

I've been at this for several days now.
I did try totally un-installing Thunderbird using Synaptic. Then manually deleting the .Thunderbird file. Then doing a fresh install of Thunderbird using Synaptic.

Still get the same results ](*,)

I am thinking that maybe App Armor is stopping this?
Or perhaps some other security issue in Ubuntu like Linux Security Module?

**Any help will be greatly appreciated.**

Otherwise the installation went flawlessly.
We even got Skype working on the first try!
Printers installed correctly and perfectly too.

---

### Post by theDaveTheRave on 2010-08-30
LaughingHorse

That sounds completely topsy turvy?

my only suggestion is as follows...

I assume that your and the wife's pcs are both desktops?

I assume that you have a separate /home partition on your system?

I suggest trying the following...

[LIST]
[*]first option
[/LIST]
[LIST][*]copy the whole of your /home to an external HDD.[/LIST] make sure you get all the hidden directories too
[LIST][*]create another user on the wife's pc[/LIST]ensure you match your login / password details from your pc.
[LIST][*]now copy over all of your /home to the /home for the new user you have just created.[/LIST] again ensure you get all the hidden directories.

finally...

reboot into the wife's pc, and login as the new 'user' and see if thunderbird is still playing silly games.


Now repeat doing the same thing in the opposite direction (wife login /home onto your pc.

This should tell you if it a 'user area' problem or a 'system problem'

[LIST]
[*]second option
[/LIST]
[LIST][*]install another email client, to see if that makes any difference[/LIST]

My hope is that when you transfer your /home thunderbird will break down, and your wife will be OK on your system.

quick question,

what makes you think that you have an apparmor problem? did you install them differently on each pc?

another option may be a rule on your router to the IP for the outgoing mail server in the open ports stuff??

personally I'm not sure, I'm just hoping I may give you an idea, or maybe the results of the 'tests' will give other more experienced people out there ideas for solutions.

good luck, and I'm going to keep an eye on this thread as it sound like an interesting (albeit very strange) problem

David

---

### Post by LaughingHorse on 2010-08-30
Hi Dave,

Yeah, this is a very weird problem.

"what makes you think that you have an apparmor problem? did you install them differently on each pc?"

She has a notebook, and I am using a desktop.

But since I can get to the mail server using Terminal
telnet mail.[domain] 50

It but can not send, I'm thinking it must be something crazy with permissions or somehting.

She can download her email from that server using Thunderbird, just can't send using that server.

The other thing I am thinking is maybe Thunderbird stores the security settings somewhere that we are not aware of and for some reason it did not delete it.
Though I canceled that account, removed it from Thunderbird. SHut it down, and then created another account. But maybe the security settings stayed in some hidden database in Thunderbird?

Very, very weird.

> **theDaveTheRave said:**
> LaughingHorse

That sounds completely topsy turvy?

my only suggestion is as follows...

I assume that your and the wife's pcs are both desktops?

I assume that you have a separate /home partition on your system?

I suggest trying the following...

[LIST]
[*]first option
[/LIST]

[LIST]
[*]copy the whole of your /home to an external HDD.
[/LIST]
make sure you get all the hidden directories too
[LIST]
[*]create another user on the wife's pc
[/LIST]
ensure you match your login / password details from your pc.
[LIST]
[*]now copy over all of your /home to the /home for the new user you have just created.
[/LIST]
again ensure you get all the hidden directories.

finally...

reboot into the wife's pc, and login as the new 'user' and see if thunderbird is still playing silly games.


Now repeat doing the same thing in the opposite direction (wife login /home onto your pc.

This should tell you if it a 'user area' problem or a 'system problem'

[LIST]
[*]second option
[/LIST]

[LIST]
[*]install another email client, to see if that makes any difference
[/LIST]

My hope is that when you transfer your /home thunderbird will break down, and your wife will be OK on your system.

quick question,

what makes you think that you have an apparmor problem? did you install them differently on each pc?

another option may be a rule on your router to the IP for the outgoing mail server in the open ports stuff??

personally I'm not sure, I'm just hoping I may give you an idea, or maybe the results of the 'tests' will give other more experienced people out there ideas for solutions.

good luck, and I'm going to keep an eye on this thread as it sound like an interesting (albeit very strange) problem

David

---

### Post by tardis2010 on 2010-09-03
Hi,

I am having the same problem, it started when Thunderbird started using their automated setup procedure, it reads different pop and smtp servers than what my  ISP recommends. The POP works with their selection or the ISP's choice but sending email by the SMTP server fails whether I use Thunderbirds selection or the ISP recommended server. The one thing I notice is that Thunderbird does not like my ISP's security selection and asks whether I want to continue. I am still working at it but if anyone has already figured it out, let us know.
Thanks

---

### Post by Star88 on 2010-09-21
Having the same problem! Windoze works fine. But Ubtu cannot send anything. Settings are exactly the same!

---

### Post by pbrane on 2010-09-21
In order for you to send using one of your domains your ISP will have to allow mail relaying, most ISPs don't.

Have you tried this with **evolution**?

---

### Post by Star88 on 2010-09-21
Evolution does not work either

---

### Post by SeijiSensei on 2010-09-21
You've probably checked this, but I need to ask anyway.  If you look in Account Settings, are the two accounts set up to use their respective SMTP servers, or is one SMTP host the default, and both of them are trying to send through it?  Just make sure each account is using its own unique SMTP server.

Next, do you need to authenticate yourselves to the server you cannot reach?  If you need user/password authentication, TLS, or whatever, make sure each account has SMTP authentication set up correctly.

---

### Post by 99_rover on 2010-10-29
Have a similar issue - posted to another thread as well - thunderbird was working fine incoming and outgoing then 2 days ago the outgoing packed it in. Incoming still works but the outgoing keeps timing out.

Help?

---

### Post by argyrism on 2012-10-02
i have the same problem with Thunderbird , outlook works ok (send/receive) , Thunderbird only can receive (POP3). 

At the beginning i thought that the problem it was with Thunderbird, so i downgraded to version 12 (from 15.01) and i have the same issue. Any help would be appreciated.

---

### Post by argyrism on 2012-10-03
now i noticed that for some email addresses i get the error

Server error: '554 5.7.1 <email@address.com>: Relay access denied'

but for some others it works (outlook only)

---

### Post by argyrism on 2012-10-03
ok i have fixed it, the problem was with sasl authentication, i have reconfigured sasl to defaults and it works now

---

### Post by gertcher on 2012-10-13
> **argyrism said:**
> ok i have fixed it, the problem was with sasl authentication, i have reconfigured sasl to defaults and it works nowWhat is 'sasl'?  Where do you reconfigure it and how is it done?  I know how to get the command line, after that it is a mystery.

Thanks  Greg

---

### Post by wildmanne39 on 2012-10-13
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---


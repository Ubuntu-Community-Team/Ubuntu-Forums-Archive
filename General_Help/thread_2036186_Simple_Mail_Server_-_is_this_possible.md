---
title: "Simple Mail Server - is this possible?"
date: 2012-08-01
forum: General Help
---

### Post by slyme on 2012-08-01
Hi All,

I am relatively new to Ubuntu although I do consider my self to be generally comfortable with finding my way around new (to me) concepts and approaches in IT.

I want to set up a simple mail server and this is what I want it to do:

Collect email from one POP3 mailbox and drop it into the appropriate user directory (there will be only one user).

Allow that user on the local network to log in and read the email using IMAP.

And that's it. It doesn't need to be open to the internet and, for now, it doesn't have to deal with SMTP.

The goal is for me to be able to access my email from any device on my local network using standard email clients.

I have searched for answers and I have been overwhelmed by the variety and detail available. Most 'How To' articles seem to so complicated (not necessarily a problem in itself) and are offering much more comprehensive solutions. Maybe that's how it has to be?

I am not asking for massive detail just broad sweep suggestions along the lines of, "Program/utility X will collect the mail and program/utility Y will present it," or perhaps, "You can't do that."

Thanking you all in advance,

Simon.

---

### Post by mastablasta on 2012-08-01
that's a silly setup.
 
basically you would have a computer where you would run an email client that would collect email from elswhere. and then you would use another computer and email client to access the emails that the client has downloaded.

---

### Post by slyme on 2012-08-01
> **mastablasta said:**
> that's a silly setup.
 
basically you would have a computer where you would run an email client that would collect email from elswhere. and then you would use another computer and email client to access the emails that the client has downloaded.

:) I'm well known for being rather silly from time to time so that's no surprise!

Let's make sure I understand this ... so, I have a single machine on the network. Currently it does nothing other than run as a web server (not exposed to the internet) and I never switch it off.

It had occurred to me that I could set up say, Thunderbird on that web server and then I could set up Thunderbird on all of my other devices and somehow point all of those installations at the same profile folder on the web server. Is this what you mean?

I didn't pursue that strategy because I thought to myself, "No, it can't be that simple surely?" My first thought was that different OSs would handle the profile folder in ways that would prevent this from working.

Thanks so much for your reply mastablasta, I never expected to get such a quick response - this is my first question here.

all the best,

Simon.

---

### Post by mastablasta on 2012-08-03
> **slyme said:**
>  It had occurred to me that I could set up say, Thunderbird on that web server and then I could set up Thunderbird on all of my other devices and somehow point all of those installations at the same profile folder on the web server. Is this what you mean?

 
if that is what you want to achieve then yes... bt it's a bit silly.
 
otherwise you can have multiple email acocunts in thunderbird (or other clients) so if you want you email for exmaple from various accounts to be accessible from any mashcine in the LAN you just add those acocunts to their email clients and chose IMAP as email access.
 
for example we have 2 desktops and a laptop at home. i can access gmail form everywhere via thunderbird as well as email on our web server etc. using IMAP protocol on all.
 
you can also have multiple thunderbird profiles. for example when i start thunderbird it asks me if which email accounts i want to access as my wife and i use different accounts ofcourse.: [http://kb.mozillazine.org/Profile_Manager](http://kb.mozillazine.org/Profile_Manager)

---


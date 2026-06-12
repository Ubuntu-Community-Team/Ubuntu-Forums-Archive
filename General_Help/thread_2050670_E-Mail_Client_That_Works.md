---
title: "E-Mail Client That Works"
date: 2012-08-31
forum: General Help
---

### Post by Phugoid on 2012-08-31
Hello!

I switched to Ubuntu from Windows (spit!) both at home and in work about 3 months ago now and generally speaking it has been the best decision of my computing life.

There's just one REALLY big issue that's annoying me, and once I solve it (with your help, hopefully), then I'll have 100% satisfied with my Ubuntu set up... and that's e-mail clients.

With windows I used MS Outlook and it was pretty great, I have to say. It was relatively easy to set up for the two accounts that I use and synchronised perfectly with the e-mail server.

Since moving to Ubuntu, however, I've lost that functionality. I'm using (or trying to use...) Thunderbird,  and ideally I want to have the same set up that I used to have with Outlook.

I have two accounts - one is a personal Windows (spit!) Live account, and the other is a university e-mail account which is set up as a Microsoft Office Outlook Web Access/Microsoft Exchange account.

I've currently tried to set up the Windows Live account using pop3 settings and my University account using imap settings.

The issues I have at the moment is as follows:

1) In both accounts I have several subfolders which I use (plus the usuals - junk, drafts, etc), but in Thunderbird I only get Inbox and Trash. How do I get the others to sync?
2) When I delete an e-mail in Thurderbird, I don't think it gets deleted from the server, even when I delete it from the trash folder too.

I have similar problems on my Android device. Another problem I have there is that occasionally I will refresh my e-mail and it will bring up a lot of OLD messages and display them as unread... which is really annoying.

Any hints/tips then for getting all of my folders from both accounts to show up in Thunderbird and for it to sync properly with my server (i.e. if I delete/move on server, it deletes/moves on Thunderbird and vice versa)?

Another thing - how do I get Ubuntu to run Thunderbird on startup and also how do I minimise it so that it goes to the system tray but still displays alerts, etc, the way that Microsoft Outlook does. I've tried the Firetray add-on but that doesn't work as there's a bug somewhere and many people seem to be having problems with that - not sure what it is, but surely there must be some other way to do it?

---

### Post by BBQdave on 2012-08-31
I use Thunderbird too, great email client and configurable.

A great resource for your questions:

[https://support.mozillamessaging.com/en-US/home](https://support.mozillamessaging.com/en-US/home)

This should help with your Thunderbird configuration and maybe even present new functions :)

---

### Post by Gordonbp531 on 2012-08-31
> **Phugoid said:**
> 
Since moving to Ubuntu, however, I've lost that functionality. I'm using (or trying to use...) Thunderbird,  and ideally I want to have the same set up that I used to have with Outlook.

I have two accounts - one is a personal Windows (spit!) Live account, and the other is a university e-mail account which is set up as a Microsoft Office Outlook Web Access/Microsoft Exchange account.

I've currently tried to set up the Windows Live account using pop3 settings and my University account using imap settings.

The issues I have at the moment is as follows:

1) In both accounts I have several subfolders which I use (plus the usuals - junk, drafts, etc), but in Thunderbird I only get Inbox and Trash. How do I get the others to sync?
2) When I delete an e-mail in Thurderbird, I don't think it gets deleted from the server, even when I delete it from the trash folder too.



The POP account (Hotmail) will only download emails in the Inbox. That's how POP mail works. As Hotmail doesn't do IMAP and you're not using Outlook with the Outlook Connector then AFAIK you're stuck with that.
The IMAP account should synchronise all your folders.
Maybe you haven't subscribed to them in TBird?
In Thunderbird, right-click on the account name in the left-hand pane, and choose "Subscribe". A list of folders should open up in a new window and you can then select the folders to subscribe to.
Have a look here: [https://picasaweb.google.com/115914092296730644096/Thunderbird#5782872122552922946](https://picasaweb.google.com/115914092296730644096/Thunderbird#5782872122552922946)

---

### Post by Frogs Hair on 2012-08-31
Thunderbird does not delete from my Windows Live POP 3 account nor did Windows Live Mail which is different than Outlook. 

Items from my GMX IMAP account are deleted from Thunderbird. You may Want to see if Evolution, which was the default client prior to Thunderbird has the features you want.

---

### Post by Phugoid on 2012-08-31
> **gendibal said:**
> The POP account (Hotmail) will only download emails in the Inbox. That's how POP mail works. As Hotmail doesn't do IMAP and you're not using Outlook with the Outlook Connector then AFAIK you're stuck with that.
The IMAP account should synchronise all your folders.
Maybe you haven't subscribed to them in TBird?
In Thunderbird, right-click on the account name in the left-hand pane, and choose "Subscribe". A list of folders should open up in a new window and you can then select the folders to subscribe to.
Have a look here: [https://picasaweb.google.com/115914092296730644096/Thunderbird#5782872122552922946](https://picasaweb.google.com/115914092296730644096/Thunderbird#5782872122552922946)

Ah well... looks like I'll have to migrate my personal email to another provider that does imap.

I tried to subscribe with my imap account but only Trash showed up in the subscription list... nothing else there even though I definitely have additional folders when I sign into the OWA portal!

---

### Post by dodo3773 on 2012-08-31
The email client you are looking for is called "evolution" email. I came from Outlook originally as well and it is the only replacement I have found. After using it for a while though I have come to like it better then Outlook personally. But yeah, it should do all the things you are trying to do.

---

### Post by Gordonbp531 on 2012-08-31
> **dodo3773 said:**
> The email client you are looking for is called "evolution" email. I came from Outlook originally as well and it is the only replacement I have found. After using it for a while though I have come to like it better then Outlook personally. But yeah, it should do all the things you are trying to do.

No it won't. It won't show all the Hotmail folders because the only clients that will do that are Outlook using the Outlook Connector or Windows Live Mail.
Secondly there must be a problem on the Exchange server end with IMAP because Thunderbird will show IMAP folders perfectly well. It does here...

---

### Post by dodo3773 on 2012-08-31
Must be something windows did to stick it to you then I guess with hotmail. Bummer. Kind of figures they would attempt to force you to use outlook though.

---

### Post by Gordonbp531 on 2012-08-31
> **dodo3773 said:**
> The email client you are looking for is called "evolution" email. I came from Outlook originally as well and it is the only replacement I have found. After using it for a while though I have come to like it better then Outlook personally. But yeah, it should do all the things you are trying to do.

No it won't. It won't show all the Hotmail folders because the only clients that will do that are Outlook using the Outlook Connector or Windows Live Mail.
Secondly there must be a problem on the Exchange server end with IMAP because Thunderbird will show IMAP folders perfectly well. It does here...

---

### Post by Phugoid on 2012-08-31
> **dodo3773 said:**
> Must be something windows did to stick it to you then I guess with hotmail. Bummer. Kind of figures they would attempt to force you to use outlook though.

Yeah... that's the proprietary way! Create something and design it so that it can only be used with your existing products and nothing else...

Shame the model doesn't work as all it does is drive away customers who prefer to have consumer choice :|.

So I'll migrate my personal e-mail to something else. I've actually been meaning to do it for years, but there's more than a decades worth of online accounts associated with my hotmail account so it's going to be a LOT of work migrating it all to another address. But I have to do it sometime!

As for my IMAP problem, I'm not sure what the problem could be.

---

### Post by Gordonbp531 on 2012-08-31
> **Phugoid said:**
> 

As for my IMAP problem, I'm not sure what the problem could be.

Might be worth asking your Exchange Admin....

---

### Post by fabietto0102 on 2012-08-31
Try Devmail [http://davmail.sourceforge.net/](http://davmail.sourceforge.net/)

I use Devmail in connection to Thunderbird for the MS Exchange we use at work, and it works great.

---

### Post by dodo3773 on 2012-08-31
> **Phugoid said:**
> Yeah... that's the proprietary way! Create something and design it so that it can only be used with your existing products and nothing else...

Shame the model doesn't work as all it does is drive away customers who prefer to have consumer choice :|.

So I'll migrate my personal e-mail to something else. I've actually been meaning to do it for years, but there's more than a decades worth of online accounts associated with my hotmail account so it's going to be a LOT of work migrating it all to another address. But I have to do it sometime!

As for my IMAP problem, I'm not sure what the problem could be.


Me and pretty much everyone I know uses gmail. Probably save you a lot of headache switching to that

---

### Post by fabietto0102 on 2012-08-31
I use gmail too, and while it's very nice and user friendly on the browser it's a pain on the desktop if you want to use it with an email client. 

It's just weird if you're used to Outlook, which, let's be frank here, it's an awesome application.

---

### Post by dodo3773 on 2012-08-31
> **fabietto0102 said:**
> I use gmail too, and while it's very nice and user friendly on the browser it's a pain on the desktop if you want to use it with an email client. 

It's just weird if you're used to Outlook, which, let's be frank here, it's an awesome application.

I don't use a web browser to check my email ever really so I cannot comment on the comparison. I have never had any problems at all setting it up with an email client though.

---

### Post by Gordonbp531 on 2012-09-01
> **fabietto0102 said:**
> I use gmail too, and while it's very nice and user friendly on the browser it's a pain on the desktop if you want to use it with an email client. 

It's just weird if you're used to Outlook, which, let's be frank here, it's an awesome application.

Gmail using IMAP behaves the same in TBird as it does in Outlook.
Can't see how you can call it a "pain"....

---

### Post by rickm1945 on 2012-09-01
I use Thunderbird and the Lightning Scheduler. I have four email accounts setup, 2 roadrunner accounts, Hotmail, which is Windows live mail, and Gmail. I use all these accounts and I have no problems with any of them. I use them all on my wireless network and I have the calendar setup for my appointments. I also have several folders in which I store emails from these accounts. I have moved emails from one account to another and to various folders. I really find it quite accommodating. Maybe I'm missing something in the OP that hasn't sunk in yet, but I don't know what more anyone could want than whatThunderbird has to offer. In fact if you use Firefox for your browser setting up the accounts is a breeze, since Thunderbird will use the Firefox data base to configure the different email accounts.:)

---

### Post by Phugoid on 2012-09-01
Okay guys, I sorted the issues with my work account. It's now fully synced up with the server and works perfectly.

I switched to a different personal e-mail account through my own personal website which can be set up with imap. However I'm now having a different issue with that account.

Whenever I try to enter any folders on that account, Thunderbird throws up the following error:


"The current operation on "Sent Items" did not succeed. The mail server for account [EMAIL="myaccount@mydomain.com"]myaccount@mydomain.com[/EMAIL] responded: Command Error. 12."

This happens to all my folders, not just "Sent Items". For comparison I set up my account on Evolution, and that worked perfectly, so it definitely seems to be a Thunderbird issue rather than an issue with the account itself. But I prefer Thunderbird as a client and would like to use that instead of Evolution.

Any hints/tips on what this problems could be ?!?!?! Really frustrating.

---

### Post by Phugoid on 2012-09-03
Solved my issue.

For future reference for anybody else:

Edit -> Preferences -> General Tab -> Config Editor

Toggle mail.server.default.send_client_info from True to False.

---


---
title: "separation of two linked email addresses by evolution"
date: 2011-02-11
forum: General Help
---

### Post by nicnok on 2011-02-11
Hope this is the right forum?
I am a non-techie.
We have 2 email addresses on one email account from Madasafish.
Their formats are:
[email]mywife@madasafish.com[/email]
and mine = [email]me@mywife.madasafish.com[/email].
Despite what it said in Madasafish's sales blurb they refuse to supply me with a totally separate email address without paying double.

My wife's browser collects all the stuff addressed to her and none of mine.
My evolution collects ANY uncollected mails for either address.
Managing this is cumbersome and annoying.
Is there a filter I need to apply to evolution to fix it?
If so how? ... I have tried various options to no result.
I read the sticky about posting of wireless threads and have collected that data, but it runs to 600 or so lines, so I thought it would be unhelpful to copy it here.

---

### Post by herdwick on 2011-02-11
Can you tell us what username you/she put in in each case in the account settings or browser.

Typically in these situations using [email]me@mywife.madasafish.com[/email] should collect just your mail, but I might need to read up a bit more. 

This is the wrong section really but don't stress about it !


Phil

---

### Post by nicnok on 2011-02-12
Thanks for your interest Phil. I put the post here because my Evolution pc uses a wireless connection to the router, & I thought the problem might lie there, but very happy to have thread moved - how do we do that? [have tried in another instance with no success!]

Some research shows the following on my [Evolution] pc:
**Evolution> Edit> Preferences> Account Editor> **
Identity> Account Information: Name: [email]me@mywife.madasafish.com[/email] 
              Required Information: email address:  [email]me@mywife.madasafish.com[/email] 

Receiving Email: Configuration: Server: mail.madasafish.com 
                            Username: mywife.madasafish.com 

My wife's Outlook Express shows:
[B]Tools> Accounts> Mail>
[/B]mail.madasafish.com
[B]Properties> General>
[/B]Mail account: mail.madasafish.com
User information: E-mail address: mywife.madasafish.com
[B]Servers>
[/B]Server information: incoming: POP3: mail.madasafish.com
Incoming Mail Server account: mywife.madasafish.com

I hope I have set out all the relevant settings & not got them scrambled.

Barry

---

### Post by nicnok on 2011-02-12
Sorry- correction:

My wife's Outlook Express shows:
[B]Tools> Accounts> Mail>
[/B]mail.madasafish.com
[B]Properties> General>
[/B]Mail account: mail.madasafish.com
User information: E-mail address: [email]mywife@madasafish.com[/email]
[B]Servers>
[/B]Server information: incoming: POP3: mail.madasafish.com
Incoming Mail Server account: [email]mywife@madasafish.com[/email]

---

### Post by bobpullen on 2011-02-14
> **nicnok said:**
> 
Despite what it said in Madasafish's sales blurb they refuse to supply me with a totally separate email address without paying double.


What sales blurb would that be? If it's something on our website then I can look at making it clearer.

I can also set you up a second account free of charge with a completely different email address. Drop me a message if you'd like me to do that for you.

Best rgds,

---

### Post by herdwick on 2011-02-14
Evolution> Edit> Preferences> Account Editor> 
Identity> Account Information: Name: [email]me@mywife.madasafish.com[/email] 
Required Information: email address: [email]me@mywife.madasafish.com[/email] 

Receiving Email: Configuration: Server: mail.madasafish.com 
Username: *mywife.madasafish.com *

I would try it with [email]me@mywife.madasafish.com[/email] as the username instead of the italics part. I don't know if it'll work but it's worth a go. [http://www.madasafish.com/support/email/setup/setup/alias_email_address.shtml](http://www.madasafish.com/support/email/setup/setup/alias_email_address.shtml) suggests using filters.

Bob Pullen has also replied and he'll be a le to fix it either way.

---

### Post by nicnok on 2011-02-15
Bob, [do I take it Madasafish is part of Plusnet?] When my wife signed up with madasafish we were very specific that my wife [as main user] had to have a separate email address [business reasons] but I also needed one. She was assured there would be absolutely no problem. The business having spent £150 on a consultant to get msf working on her XP and [wireless on] my [then] ME because the instructions were so poor we then found msf refused to let me have anything other than an 'alias'. Despite being furious we couldn't face the weeks of disruption in ditching msf & moving elsewhere [BT had been even worse when we tried them]. ... so, not on the website! .. but no one ever suggested we could have a separate a/c for free.
The offer is much appreciated, and I may come back if that's ok, but having got life set up around the alias I'll see if Phil's hard work works out - I'll continue the thread by responding to him now.
Thanks again 
Many thanks for the offer

---

### Post by nicnok on 2011-02-15
Phil,
Thanks for your work: I've just made the suggested adjustments: will need to wait for some emails! Shouldn't be long. However Evolution seemed to be quite annoyed [said that the password was wrong once I changed the USERNAME].
Thanks for the link in the madasafish website - illuminating, but of course directly relevant to Outlook Express only.
I've intuited importing the changes into Evolution by setting 2 rules:
Message> Create Rule> Filter on Recipient> allow 'me@' into Inbox and 
Message> Create Rule> Filter on Recipient> imposing 'Stop Processing' if recipient does NOT contain 'me@'

Madasafish markets itself as 'the friendly ISP', however when I tried [more than once] to work this through with them [by 'phone & 'ticket'] they c/would give no help when they found I was using Evolution.

Barry

---

### Post by herdwick on 2011-02-15
I think it is standard behaviour to delete the password if you change the username, Thunderbird does it too.

What I suggested - the selective mail download - requires their POP3 server to support it. This may not be the case or it may need the @ symbol to be replaced with + or similar in the username. We'll see :-)

---

### Post by howefield on 2011-02-15
> **nicnok said:**
> I thought the problem might lie there, but very happy to have thread moved - how do we do that? [have tried in another instance with no success!]

Use the Report button, which you will find in the bottom left corner of your post and a member of staff will attend to it. I'll move your thread to General Help.

One way round the issue might be to use IMAP with one address and POP with the other, I don't know if this is possible with your madasafish account, I have my isp mail setup with POP and a gmail account setup with IMAP.

Evolution will create a set of folders for the IMAP separate to your POP folders, something like the screenshot.

---

### Post by nicnok on 2011-02-15
> **howefield said:**
> Use the Report button, which you will find in the bottom left corner of your post and a member of staff will attend to it..

Re Moving threads and posts: Thanks, I was using 'Contact Us' bottom right [wrong!, but 'Report Abuse' seemed a wee bit strong, especially as I was  the unwitting abuser!]

---

### Post by nicnok on 2011-02-15
> **herdwick said:**
>  selective mail download - requires their POP3 server to support it. This may not be the case or it may need the @ symbol to be replaced with + or similar in the username. We'll see :-)

Unfortunately the changes had no effect. 'Evolution> Edit> Preferences> Account Editor> Receiving Email:' says the Server Type: is POP [not POP3?] 
so I've changed the '@'s to '+'s: waiting to see!

If I alter the Server Type to IMAP as howefield suggests, what other changes would I need to make? 
If Bob Pullen is watching this thread I wonder whether he knows, & would be good enough to say if madasafish would allow IMAP to function in an 'alias' account?

---

### Post by lisati on 2011-02-15
> **nicnok said:**
> Unfortunately the changes had no effect. 'Evolution> Edit> Preferences> Account Editor> Receiving Email:' says the Server Type: is POP [not POP3?] 
so I've changed the '@'s to '+'s: waiting to see!

If I alter the Server Type to IMAP as howefield suggests, what other changes would I need to make? 
If Bob Pullen is watching this thread I wonder whether he knows, & would be good enough to say if madasafish would allow IMAP to function in an 'alias' account?

I gather that the creation of a separate account, as offered [here]("http://ubuntuforums.org/showpost.php?p=10457382&postcount=5"), isn't an option. Have you contacted Bob Pullen about this yet?

---

### Post by nicnok on 2011-02-15
Just been prodding.

There's an option at:

'Evolution> Message>'  called "Apply Filters". What's it for? Is this anything to do with my problem? Nothing seems to happen when I click it.

By-the-bye the route to alter the filters I set took some finding: its not under 'Messages', the route is  'Evolution> Edit> Message Filters>.

---

### Post by nicnok on 2011-02-15
> **lisati said:**
> I gather that the creation of a separate account, as offered [here]("http://ubuntuforums.org/showpost.php?p=10457382&postcount=5"), isn't an option. Have you contacted Bob Pullen about this yet?

I posted my last query re IMAP before I saw your comment. 
I am going to try to get the emails separated using the 'alias' a/c if I can. OK, I'm just stubborn, but it might help someone else too, so I've not yet contacted Bob Pullen,
 but sorry, I don't know how to contact him other than by posting onto this thread.

---

### Post by bobpullen on 2011-02-16
If your account has the ability to add additional mailboxes, then you should be able to have a separate local part and nominate one as the catch-all.

e.g.

[EMAIL="me@domain.tld"]```
me@domain.tld <-- default
```[/EMAIL] 
[EMAIL="you@domain.tld"]```
you@domain.tld
```[/EMAIL]Each mailbox is then accessible independently of each other using IMAP or POP3.

You may need to set some stuff up on our website before this becomes possible though.

My Account > Internet > Manage additional mailboxes

Although come to think of it, that option only exists where you have a hosted .co.uk domain name, and each separate mailbox would share the same domain but just have a different local part.

Do you have the option when logged into our website to register a .co.uk domain name?

I've subscribed to this thread now anyway so I */should/* get notification of any further replies.

Rgds,

---

### Post by nicnok on 2011-02-19
> **bobpullen said:**
> I.... Do you have the option when logged into our website to register a .co.uk domain name? ... ,

Yes, I've requested to register a free domain [www//mywife.org.uk]. Will await more from Madasafish shortly no doubt, then revert to your previous posted suggestions. Thanks

---

### Post by nicnok on 2011-02-20
> **bobpullen said:**
> .....
You may need to set some stuff up on our website before this becomes possible though. .....
Although come to think of it, that option only exists where you have a hosted .co.uk domain name, and each separate mailbox would share the same domain but just have a different local part.

Rgds,

I've had confirmation that we've now got a domain registered [mywife.org.uk] 
Before I go messing with it do you have any more specifics on your quoted comments above? or shall I just start? As a fall-back I suppose I could now create 'me@madasafish.com' using the domain facility [a wee bit reluctant as a lot of people use my current address]

---

### Post by bobpullen on 2011-02-22
You should find it reasonably intuitive. You would just need to create a new mailbox via our website under the .uk domain name.

You would then access each mailbox independently of each other using the full email address as the username.

It's been a while since I played around with it, but I */think/* there's a way to have your existing mail default to the same location as one of your domain mailboxes.

Best rgds,

---


---
title: "Evolution: gmail IMAP settings"
date: 2010-05-01
forum: General Help
---

### Post by ebro173 on 2010-05-01
I've seen a bunch of other posts on this topic but they haven't solved my problem.  I just installed Ubuntu Netbook Remix 10.04.  Love it so far. 

Except, I can't figure out how to setup my gmail account in Evolution so that I can see the emails on the server or download them locally.  I had it working before both in 8.04 LTS and a flash drive install of UNR 9.10.  I really can't figure out why it is so difficult this time.

Gmail settings are/were already on IMAP - checked while logged in through browser.

In Evolution, I've tried changing the account name, user name (for receiving mail), etc. and different combos of same settings.  The receiving mail settings I'm using for IMAP authentication are password and save password. Security is set to SSL.

Evolution tries to access the server but never asks for a password.  Likely, because something is wrong with my settings.  I just don't know what.

I have successfully sent email from the gmail account, and I have set up google calendar, using Evolution.  

Suggestions on the right settings so I can receive email?

---

### Post by bubblehead74 on 2010-05-01
I don't remember the settings, and I don't have my comp with me now. I just wanted to say that if you selected Save password, Evolution saved it and won't ask for it when you login to Gmail. So that's normal. If no one helps you, I will try to give you the answer later this evening when I get the chance to peek into my settings.

---

### Post by ebro173 on 2010-05-01
To clarify, for this task of accessing the server to see emails, I haven't ever put in a password.  From reading other posts, it seems that the first time Evolution successfully gets to the server, it will ask for the password, keep it, and then never ask for it again.  Well, Evolution never gets far enough to ask me for the password.

---

### Post by howefield on 2010-05-01
> **ebro173 said:**
> Evolution never gets far enough to ask me for the password.

What are you using for the server name?

imap.gmail.com ?

---

### Post by ebro173 on 2010-05-01
yes

---

### Post by howefield on 2010-05-01
> **ebro173 said:**
> yes

Ok, and your username is the full address, eg [email]xxxxxxxx@gmail.com[/email]

---

### Post by ebro173 on 2010-05-01
I have tried it as [email]XXXXX@gmail.com[/email] and as just XXXXX.

---

### Post by bubblehead74 on 2010-05-01
Check this out:

[http://ulyssesonline.com/wp-content/uploads/2008/10/receivingemail.png](http://ulyssesonline.com/wp-content/uploads/2008/10/receivingemail.png)

Although I think I didn't enter @gmail.com in my account name and I did not specify the port either. Also be sure to check for typos. :-)

---

### Post by ebro173 on 2010-05-01
That looked promising.  I tried it though and I still get the same error message.  The addition was on the Recieving Mail tab, in the box for the server I added the :993.

So the server was imap.gmail.com:993

Still no luck.

One thing.  I'm not on my home network.  I'm at work.  Still this has not been an issue in the past.

---

### Post by bubblehead74 on 2010-05-01
Aha! Then there is a good chance that you are behind a proxy. Try to search for Evolution and proxy issues.

---

### Post by ebro173 on 2010-05-01
Alright, I'll check into it.  

But, I've never had this trouble before.  Maybe it is because in the past, the first time I set up Evolution I was on my home network.  I'm thinking that, in the past, Evolution was able to get to the server the first time, or what ever the case I was able to give Evolution my email password.  Then when using the network at work everything was in already place and it just worked.

---

### Post by ebro173 on 2010-05-01
So, I deleted the account from Evolution.  Then I opened up Evolution at home and created the account again.  Basically all the same settings, there is no mystery.  It all worked without problems as I expected it to in the first place.

I'm thinking the problem was to do with the firewalled wireless network at work.

When I go back to work I'll try it again to see if it works fine.

---

### Post by ebro173 on 2010-05-03
I've still  not checked Evolution/proxy issues.  Just a note to say that while it worked at home and the password is now stored, it did not work straight away upon returning to work.

---

### Post by ebro173 on 2010-05-03
Maybe this other thread sheds some light or will at some point.

[http://ubuntuforums.org/showthread.php?t=1385015](http://ubuntuforums.org/showthread.php?t=1385015)

---

### Post by adnafunnyfarm on 2010-05-03
I had the same issue installing evolution on my laptop at home. I just went with Thunderbird. No problems there.

---

### Post by a.weiberjager on 2010-05-05
Check this configuration steps for your Gmail account

[http://weakish.int.eu.org/tutorial/configure-evolution-for-gmail.xhtml](http://weakish.int.eu.org/tutorial/configure-evolution-for-gmail.xhtml)

Worked like charm for me.

---

### Post by ebro173 on 2010-05-05
Thanks for the tips.  I will look into making some changes to the drafts and sent folders based on the tutorial at that link.  I'm also going to research what the PGP keys are/do.

I think I'm going to stick with Evolution.  Its integrated into Ubuntu Netbook Edition 10.04 by default so that just seems easier.  

I'm pretty sure to make Evolution work at work I just need to do a little reading about proxy issues.

---

### Post by robhamm on 2010-10-15
Just in case someone else comes across this while looking for a solution to a similar issue--Although your issue seems to have been a firewall (since it worked at home), if a user has his or her gmail preferences set up for POP (as opposed to imap), I believe the server would be pop.gmail.com instead of imap.gmail.com.

---


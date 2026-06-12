---
title: "Evolution &amp; Exchange2003"
date: 2009-09-16
forum: General Help
---

### Post by rebellion2tyrants on 2009-09-16
Hi there, 
 
I'm new to Ubuntu and the forum. I have successfully installed Ubuntu, set up most of my programs, but can't seem to get Evolution to authenticate my exchange 2003 account from work.
 
First, I ask your patience since I'm clueless.
 
Second, I've done some of the following:
 
1. tried every variation of doman\username, domain/username, username, user.name in the login credentials. I do not believe this to be the source of the issue.
2. determined that my employer has locked down IMAP on the server (boo!)
3. determined that my employer is one of those braniacs who has a dynamic location for things based on whether you're logging in, got a password wrong, or logging out. As such, the url for the mail online is something like [https://mail.company.com/exchweb/bin/auth/owalogon.asp?url=https://mail.company.com/exchange&reason=0](https://mail.company.com/exchweb/bin/auth/owalogon.asp?url=https://mail.company.com/exchange&reason=0) I think this is a fairly important piece in all of this.
4. I tried to install the exchange plugin, but even after I installed that, and a host of other packages, (libebook, lcurl, etc), I still can't see the plugin in my options in Evolution.
 
I'm running Ubuntu Jaunty Jackalope 9.04 with Evolution 2.26.1.
 
I think point #3 above is crucial and may actually mean I can't do this at all. If that's the case, it's kind of a deal breaker since I need to be able to access my mail from something other than the browser that times out. If something other than Evolution is needed, I'm open to that.
 
I'm very much the beginner, so if someone can offer help, please do so with very detailed, specific instructions. Assume I know how to use the mouse and keyboard. :)
 
I apologize if I'm posting something that has been resolved!
 
Thanks,
 
rebellion2tyrants

---

### Post by Rob_H on 2009-09-16
Actually, #4 is the first deal-breaker. Make sure you've installed the **evolution-exchange** package and that "Microsoft Exchange" appears in the list of server types when you're going through the account wizard. Are you getting that far?

The fact that you mentioned domain leads me to think you're trying to use the "MAPI" server type rather than "Microsoft Exchange". MAPI support is pretty unstable right now. I've never gotten it to work. And since you're using Exchange 2003, stick to the "Microsoft Exchange" server type.

---

### Post by rebellion2tyrants on 2009-09-16
Thank you for taking the time to reply!

I am selecting Microsoft Exchange server in the account set up. That's something that has been a little confusing to me: I don't see the exchange plugins in the list of plugins in Evolution, but I've been able to select Exchange Server the whole time. From what I've read, that shouldn't be the case.

So yes, I am definitely setting it up as an exchange server, but whenever I try to authenticate, it tells me the server cannot be located. This is what made me think the dynamically changing url would be part of the problem.

---

### Post by Rob_H on 2009-09-16
I don't see it in my list of plugins, either, but Exchange support works in my environment, so I don't think that's a factor.

The dynamic URLs could be a factor, I'm not sure. But if it helps, I can tell you what works for me. I have my OWA URL set to "https://mail.mycompany.com/Exchange/". Username is my domain username (without any domain qualification or anything). At that point, I can click *Authenticate* and will be prompted for my password. You could try fiddling with the authentication type settings at the bottom if you haven't already. The default setting works fine for me.

---

### Post by rebellion2tyrants on 2009-09-16
Thanks for writing!

Unfortunately, I'm unable to locate the server with your settings. Not terribly surprised since this is where I *think* I started yesterday morning. This is quite frustrating.

I have seen other websites referencing the fact that they dynamic url is an issue, but no explanation or resolution. I'm doubtful that I'm the only one to have this problem, but I can't find anyone who got around it.

I sure hope someone who has gotten around this sees this thread!

---

### Post by Rob_H on 2009-09-16
The situation might get better once MAPI support matures in Evolution. In the meantime, you might also want to check out [DavMail]("http://davmail.sourceforge.net/"). It acts as a bridge between Exchange OWA and IMAP/SMTP/LDAP/etc. I have never used it personally, but I've seen discussions about it in the forums.

---

### Post by rebellion2tyrants on 2009-09-16
It's funny you should mention that!

I was just starting to experiment with DAVMail, and it works!

For the other Ubuntu newcomers that might someday run into this problem, I will share a few things:

1. User Thunderbird, not Evolution
2. Set up DAVMail so that the OWA url is [https://mail.company.com/exchange/](https://mail.company.com/exchange/) (No, this didn't work when you tried in Evolution, but yes, it will work for you now. Also, make sure you don't forget the secure 's' on the http or it will fail.)
3. Go into Thunderbird and set up a new account. Your server will be 'localhost' throughout. And by 'localhost' I actually mean that string, not something that is your local server or something. You are pointing Thunderbird to your computer so that DAVMail can do the work.
4. Make sure the ports in Thunderbird match the port values on DAVMail for the IMAP and SMTP.
5. Celebrate! You're done with Outlook.

Thanks to everyone for their help!

---

### Post by rebellion2tyrants on 2009-09-17
Update:

I got Evolution working on email through DAVMail, but have yet to get the calendar working. Once I either surrender or win, I'll post my settings.

---


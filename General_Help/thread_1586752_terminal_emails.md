---
title: "terminal emails???"
date: 2010-10-02
forum: General Help
---

### Post by spiky001 on 2010-10-02
Ok here is what I want to do use terminal to send and receive emails, I have googled I see sendmail and postfix and mutt, I have seen sendmail has security issues so to the others, I have just a home system setup.
  Which 1 would be the easiest to setup and use, I just want to be able to send emails to other ppl, I use aol as my email,
Why use terminal well I just want to learn/play it,s all to do with learning,

---

### Post by Johnny B on 2010-10-02
I have heard that both Mutt and Alpine are good (and in the repos). Alpine is supposed to be easier to use, although I have no experience with either program.

This will help you get set up:
[Configure Alpine - Ubuntu forums]("http://ubuntuforums.org/showthread.php?t=596964")

[Help to configure Mutt - Ubuntu forums]("http://ubuntuforums.org/showthread.php?t=389949")

---

### Post by SeijiSensei on 2010-10-02
I recommend Alpine; it has easily accessible menus and help.

Sendmail is a lot more secure now than it was some years back.  Still Ubuntu prefers Postfix so I'd use that.

However you might discover you can't send mail to anyone.  If your ISP blocks outbound traffic on the "SMTP port" (port 25), you won't be able to send.  Many ISPs no longer permit direct connections from their customers' computers to remote mail servers.  Reading your mail won't be affected, but sending might be blocked.  Over the past few years spammers have used malware to infect hundreds of thousands, if not millions, of Windows machines and turn them into little "spambots."  Most of the incoming spam my servers see these days comes from those infected machines.  So ISPs have started blocking external mail transfers to help mitigate the problem.

---

### Post by spiky001 on 2010-10-02
Ok thks SeijiSensei I will try by starting with postfix, I will be back for help configureing hope you dont mind helping out I know I said I want to learn I have looked at some of the configureing was out of  my depth with it

---

### Post by spiky001 on 2010-10-02
Ok I have installed postfix from package manager have looked through google for some sort of tutorial on configuration this is way over my head, I dont mind changing things in the config file but where to start i found a site they say add " Gmail Relay" 
relayhost = [smtp.gmail.com]:587

---

### Post by SeijiSensei on 2010-10-02
Don't do anything to the Postfix configuration to start with.  Just open Alpine and try sending a message to your AOL account.  By default it should hand the message to Postfix for delivery.  The question is what happens next.

If it arrives, you're good to go.  If not, try looking in /var/log/mail.log for hints as to the problem.  "sudo tail -n 20 /var/log/mail.log" will show you the last twenty lines of the file.  If Postfix successfully delivers the mail, you should see an entry like "status=sent (250 2.0.0 o92MiIxa023809 Message accepted for delivery)" in /var/log/mail.log.  If it fails, it'll give you a reason why.

---

### Post by spiky001 on 2010-10-02
ok i noticed in the log file timed out, it was looking at port 25 Now the outgoing port should be smtp 465 dose this help

---

### Post by SeijiSensei on 2010-10-02
Probably not.  Port 465 is designed for SMTP sent via SSL, the same encryption mechanism that secure websites use.  You'd need to be using a email server that accepts traffic on port 465 (I don't, for instance), and you'd need things like "certificates" to authenticate yourself to the remote server(s) and set up SSL encryption.

You need to contact your ISP's support staff and explain that you want to send mail from your computer.  Either they'll say, "no way, buddy," or they'll offer you some options.  The best option is for the ISP to unblock port 25.  Many providers are willing to do so upon request because they realize that someone asking specifically isn't likely to be running an infected machine with a spambot.  Another possibility is that they'll tell you which machine on the provider's network you can use as a mail relay.  You can use that information to change the relayhost field in Postfix that you mentioned before.  However their servers might only permit mail from people with mailboxes in the provider's own domain.  They might refuse to forward mail from you with an @aol.com From address. (Plus if you sent it to one of my clients, I'd reject it, since I only accept mail claiming to be from an AOL user if it's sent from AOL's own servers.)

---

### Post by spiky001 on 2010-10-03
Ok I have made some changes to Alpine setup
```
smtp.aol.com:465/ssl/
```I get error msg back "spiky@dell-laptop sender address rejected need fully qualified address?". Dose this mean I need certificates as mentioned by SeijiSensei to Verify? Any assistance plz

---

### Post by SeijiSensei on 2010-10-03
No, it means your email address doesn't have a domain part.  A "fully-qualified" address is [email]you@[something.]domain.name[/email], where the "something" part is optional.  

spiky@dell-laptop doesn't have any domain attached.  You can try using your AOL address by using (S)etup > (C)onfig from the main Alpine menu.  Highlight the "User Domain" field, type "?" for help, then follow the link in the line that begins "If you want to change the value of what gets included in the From address."

---

### Post by spiky001 on 2010-10-03
done that now get error "Need MAIL command"

---


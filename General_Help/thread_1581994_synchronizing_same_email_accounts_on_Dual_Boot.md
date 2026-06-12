---
title: "synchronizing same email accounts on Dual Boot"
date: 2010-09-25
forum: General Help
---

### Post by SuperFreak on 2010-09-25
I am in the process of trying a dual boot of Ubuntu with XP before I build a computer with just Ubuntu on it. I would like to get a feel for the Ubuntu OS before I finalize my MS divorce.
My wife is not familiar with Ubuntu and for a while will likely stick with XP while I would like to try out Ubuntu. What I am wondering is it possible to have email set up with XP (Outlook Express) and Ubuntu (probably Thunderbird) using the same email address and receive and send the same emails in both OSs. I guess I would be synchronizing the two email programs so neither my wife or I would miss any emails that might be sent/received in the other OS.
I did  a forum search of this topic but I am afraid the threads were a little confusing and I am not sure if they dealt with my issue.Right now I have decided to wait for Ubuntu 10.10 release in October before I install  and I am gathering as much information as I can for all aspects of the install and configuration.
Thanks

---

### Post by SeijiSensei on 2010-09-25
If your email provider supports the IMAP protocol, then you'll get the same view of your inbox and folders regardless of the client.  If you're stuck using POP3, then this is a more dicey proposition because all your mail is stored locally.  Thunderbird has the ability to [import Outlook Express]("http://kb.mozillazine.org/Import_from_Outlook_Express") folders when you configure a mail account.  I suggest you try it out first in Windows so you can see if it works for your wife or not.

---

### Post by SuperFreak on 2010-09-25
Yes my incoming mail is POP3 and outgoing is SMTP.
I realize I can import my folders and contacts into Thunderbird initially, but I don't see how that will solve my problem on an ongoing basis. The problem is not whether my wife will be able to use Thunderbird ( in XP or Ubuntu) but whether she will be comfortable with Thunderbird and Ubuntu generally. I realize she probably will have little difficulty with Thunderbird but she uses XP for a whole host of other programs that will be replaced by Ubuntu programs eventually.

---

### Post by SuperFreak on 2010-09-25
I am given to understand that there may be a way of doing this using a Gmail account which syncs to Outlook Express and Thunderbird. I guess all mail from my POP3 server would first go to my Gmail account (which would be configured as IMAP) then synchronize with my email software in Thunderbird and Outlook Express. Is this possible?

---

### Post by lisati on 2010-09-25
My $0.02: Something to keep in mind is that if you've been using POP3, the email has probably been deleted from the server. Some of the email clients I've used (including Evolution and Thunderbird) have an option buried away in the settings to not delete email from the POP3 server.

---

### Post by SeijiSensei on 2010-09-25
> **SuperFreak said:**
> The problem is not whether my wife will be able to use Thunderbird ( in XP or Ubuntu) but whether she will be comfortable with Thunderbird and Ubuntu generally. I realize she probably will have little difficulty with Thunderbird but she uses XP for a whole host of other programs that will be replaced by Ubuntu programs eventually.

That's a much more complex set of issues than just synchronizing mail.  As I said, the easiest short-term test is to try importing her mail into Thunderbird in Windows and see how she likes it.  Maybe she should just stick to Windows.

> **SuperFreak said:**
> I am given to understand that there may be a way of doing this using a Gmail account which syncs to Outlook Express and Thunderbird. I guess all mail from my POP3 server would first go to my Gmail account (which would be configured as IMAP) then synchronize with my email software in Thunderbird and Outlook Express. Is this possible?

If your email provider allows forwarding, then this will work.  You can set up an [IMAP account at gmail]("http://mail.google.com/support/bin/answer.py?hl=en&answer=180189") to which your POP3 mail would be forwarded.  Is it not possible to use IMAP with your current provider?  If you can change protocols without changing providers, that's probably an easier solution.

---

### Post by SuperFreak on 2010-09-26
I am beginning to wonder how secure an IMAP mail system is in light of recent events with Gmail ([http://threatpost.com/en_us/blogs/google-warning-gmail-users-china-spying-attempts-092310](http://threatpost.com/en_us/blogs/google-warning-gmail-users-china-spying-attempts-092310)). I may just try Ubuntu without email to test out its various attributes and once satisfied gradually introduce my wife to Ubuntu before migrating my Outlook Express folders to Thunderbird.

---


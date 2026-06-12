---
title: "Email Setup"
date: 2011-05-22
forum: General Help
---

### Post by kylepaddock on 2011-05-22
Hi, I am new to Unbuntu I just installed 11 and sofar love it. I am setting up my email on it. I use a Gmail account. I like how on Android and iOS the device does not download any emails but it keeps them on my sever and only views hen and then updates the changes so all of my email are on the Gmail server. What option will I need to use to obtain that.
Thanks,
Kyle Paddock
[www.tekgoblin.com](www.tekgoblin.com)

---

### Post by ajgreeny on 2011-05-22
Use the IMAP4 protocol for email and the mails will all be left on the server.  You can just view headers if you want, then click on each message you want to view in full.  Using IMAP you can view your mail in all your machines, if you have more than one, without the server archiving them all so that a pop protocol mail client would no longer be able to view them.

There is a lot of info on setting up various clients and the pros/cons of the protocols if you go to gmail in your web-browser and click on the flower icon top right->settings->Forwarding and POP/IMAP, and not knowing what client you will use, I will let you read and learn.

---

### Post by kylepaddock on 2011-05-22
I don't see that option. I see IMAP or IMAP+.

---

### Post by ajgreeny on 2011-05-22
Which email client are you using?

---

### Post by kylepaddock on 2011-05-22
Evolution mail. If that is not good I can use an different one.

---

### Post by SeijiSensei on 2011-05-22
IMAP usually means IMAP4.  Personally I prefer Mozilla Thunderbird over Evolution, but that's a matter of personal taste.  If you want to give it a try, install the "thunderbird" package from your software manager, or run "sudo apt-get install thunderbird" in a terminal.

If you're using GMail, just entering your address during the initial configuration should set everything up automatically for you.

---

### Post by Southwind on 2011-05-22
> **SeijiSensei said:**
> IMAP usually means IMAP4.  Personally I prefer Mozilla Thunderbird over Evolution, but that's a matter of personal taste.  If you want to give it a try, install the "thunderbird" package from your software manager, or run "sudo apt-get install thunderbird" in a terminal.

If you're using GMail, just entering your address during the initial configuration should set everything up automatically for you.

Ah! fellow Thunderbird user!:D SeijiSensei, I have a dual boot system, windows XP and Ubuntu10.10 upgrading to 11.04.  I wish to use my Ubuntu system much more than i do now, but one of my hangups i my email is all on windows.  Is there a way that I can use the same thundarbird files on both operating systems so that i may access an email from either OS?  This way, if I am in windows and download my mail, then later reboot into Ubuntu, I will have the email just downloaded available to me.  Have you any thoughts? Thanks
Larry

---

### Post by ajgreeny on 2011-05-22
> **Southwind said:**
> Ah! fellow Thunderbird user!:D SeijiSensei, I have a dual boot system, windows XP and Ubuntu10.10 upgrading to 11.04.  I wish to use my Ubuntu system much more than i do now, but one of my hangups i my email is all on windows.  Is there a way that I can use the same thundarbird files on both operating systems so that i may access an email from either OS?  This way, if I am in windows and download my mail, then later reboot into Ubuntu, I will have the email just downloaded available to me.  Have you any thoughts? Thanks
Larry
If you use the IMAP4 protocol, all the mail will still be there for both OSs anyway. 

However it is possible to share the thunderbird profile between windows and ubuntu, I think, though it has to stay on the windows filesystem as windows can not read a linux filesystem  I think there is a tutorial on the thunderbird website somewhere, and also probably in the ubuntu wiki or simlar.

---


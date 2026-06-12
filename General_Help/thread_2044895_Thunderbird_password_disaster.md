---
title: "Thunderbird password disaster"
date: 2012-08-20
forum: General Help
---

### Post by Buster95 on 2012-08-20
While our whole family uses our computer, I wanted to put a unique password on Thunderbird so it couldn't accessed by others (the kids). Sounds simple!

That led me to inserting a master password in Thunderbird. My thinking ... "That couldn't hurt - could it? If it doesn't suit, I can always reverse it can't I?"

Well, it didn't work as expected. I could still access Thunderbird and all the stored message folders whether I used the password or not. The only thing that I could find that it did was to block all sending of mail. About as useful as an ashtray on a mototbike, but a lesson learned and no harm done! Or so I thought.

I unticked "use a master password", closed it down and started up again. trouble is, it just refuses to go away.
Now, it doesn't recognise the password and I can't send emails.

Can anyone guide me on getting my email mojo back?

I'm using Ubuntu 12.04 on Classic mode with Thunderbird 14.1. I have two email accounts - mine and my wifes. Neither work!

---

### Post by Zill on 2012-08-20
Does this help?

[Master password]("http://kb.mozillazine.org/Master_password")

---

### Post by Buster95 on 2012-08-21
> **Zill said:**
> Does this help?

[Master password]("http://kb.mozillazine.org/Master_password")

Thanks but no - that's what got me into trouble.
It seems that the master password only protects access to other passwords. It does prevent sending and receiving of emails, but does NOT prevent access to Thunderbird folders.
Furthermore, when I tried that approach, I was unable to revert it (following the guide you directed me to). I now have NO access to my own email.

My very simple need is for a password that controls access to Thunderbird.

Cheers

---

### Post by Wim Sturkenboom on 2012-08-21
I can't help you with your current problem.

> **Buster95 said:**
> My very simple need is for a password that controls access to Thunderbird.

Give every family member his / her own Ubuntu account. Currently it sounds like your kids have access to administrative privileges as well.

---

### Post by Zill on 2012-08-21
> **Buster95 said:**
> Thanks but no - that's what got me into trouble.
It seems that the master password only protects access to other passwords. It does prevent sending and receiving of emails, but does NOT prevent access to Thunderbird folders.
Furthermore, when I tried that approach, I was unable to revert it (following the guide you directed me to). I now have NO access to my own email.
AIUI, the master password *should not* prevent sending or receiving email as it should only prevent others gaining access to your stored passwords.  However, as I don't use a master password I cannot confirm this.

Have you tried to reset the master password as described in the link? (Note that you will lose all the stored information in the Password Manager)  i.e.
> Thunderbird: Choose Tools -> Error Console, paste the expression: openDialog("chrome://pippki/content/resetpassword.xul") and press the Evaluate button. That will open a dialog asking you if you want to reset your password.

If you have tried this and your mail still does not work then it may be worth trying a new Thunderbird profile. If you are using imap this should be straightforward as your emails should be stored on the server.  However, if you are using pop3 then you will first need to ensure your downloaded emails are safely backed up so that they can be restored to the new profile.

> **Buster95 said:**
> My very simple need is for a password that controls access to Thunderbird.
I agree with Wim Sturkenboom that the best way is to use separate user accounts, each with its own email settings.

---

### Post by ds5v50 on 2012-08-21
Not a fix for your password issue, But to keep everyone to there own mail accounts use Thunderbirds profile manager

$thunderbird --profilemanager 

Then create an profile for each user, which all can be password protected. "Not Master Password"

---

### Post by Buster95 on 2012-08-22
> **Zill said:**
> AIUI, the master password *should not* prevent sending or receiving email as it should only prevent others gaining access to your stored passwords.  However, as I don't use a master password I cannot confirm this.

Have you tried to reset the master password as described in the link? (Note that you will lose all the stored information in the Password Manager)  i.e.


If you have tried this and your mail still does not work then it may be worth trying a new Thunderbird profile. If you are using imap this should be straightforward as your emails should be stored on the server.  However, if you are using pop3 then you will first need to ensure your downloaded emails are safely backed up so that they can be restored to the new profile.


I agree with Wim Sturkenboom that the best way is to use separate user accounts, each with its own email settings.

Thanks for the help. I had previously tried the "cut-and-paste" reset method in the guide. It didn't work when I did it once, but after three repeats, it now sends and receives. I don't know why I had to do it over and over, but alls well that ends well.

I will abandon password protecting my mail, while retaining open access to the system. Instead, I will use the "sledgehammer to break a nut" method of creating alternate profiles for each user of the family computer.

Thanks - I appreciate your assistance.

---


---
title: "I need help configuring Evolution with windows live outlook web app."
date: 2010-11-16
forum: General Help
---

### Post by Slobby on 2010-11-16
Okay so I go straight to hotmail.com and login with my email [email]xxxxxxxx@email.socc.edu[/email]  After I login I am taken to my mail and the upper right corner says "Outlook Web App Beta"  So I'm a little confused about setting up Evolution.

I tried it with the normal hotmail information pop3.live.com and  smtp.live.com but my password wasn't accepted.  I'm guessing because this is not the way I should have it configured.  Next I tried microsoft exchange and it asks for my OWA URL.  I'm assuming OWA stands for outlook web app.  So is this the way I need it set up?  And if so how do I find my OWA URL?

---

### Post by Nakken on 2010-12-20
OWA means Outlook Web Access, f.x mail.yourcompany.com.

---

### Post by Gordonbp531 on 2010-12-20
> **Slobby said:**
> Okay so I go straight to hotmail.com and login with my email [email]xxxxxxxx@email.socc.edu[/email]  After I login I am taken to my mail and the upper right corner says "Outlook Web App Beta"  So I'm a little confused about setting up Evolution.

I tried it with the normal hotmail information pop3.live.com and  smtp.live.com but my password wasn't accepted.  I'm guessing because this is not the way I should have it configured.  Next I tried microsoft exchange and it asks for my OWA URL.  I'm assuming OWA stands for outlook web app.  So is this the way I need it set up?  And if so how do I find my OWA URL?

I suspect that you can't set up a Hotmail email account in anything that is not Microsoft, unless you use Thunderbird and the Hotmail extensions. I've just tried it in Evolution and I can't get it to work either.

---

### Post by Foxcow on 2010-12-20
My school moved to live mail too.  Its actually pretty simple to set up.

Once you log in, look for a blue question mark at the top right corner of the page.  Next to that will be a black arrow that indicates there is a dropdown menue.  If you click on that black arrow, you ought to have two options; about or help.

If you select 'about' it will give you all of the info needed to set up such as the incoming and smtp server address info for pop or imap.

I hope this helps.

---

### Post by Gordonbp531 on 2010-12-20
I stand corrected. From this thread: [http://ubuntuforums.org/showthread.php?t=200408&page=50](http://ubuntuforums.org/showthread.php?t=200408&page=50)
I got this, which works - just done it.

These settings work with no other configuration needed /required:

Incoming server: pop3.live.com
Username: your_username @hotmail.com
Use secure connection: SSL
Authentication type: password

Server: smtp.live.com
Use Secure Connection: TLS Encryption
Authentication Type: Login

---

### Post by Foxcow on 2010-12-20
> **gendibal said:**
> I stand corrected. From this thread: [http://ubuntuforums.org/showthread.php?t=200408&page=50](http://ubuntuforums.org/showthread.php?t=200408&page=50)
I got this, which works - just done it.

These settings work with no other configuration needed /required:

Incoming server: pop3.live.com
Username: your_username @hotmail.com
Use secure connection: SSL
Authentication type: password

Server: smtp.live.com
Use Secure Connection: TLS Encryption
Authentication Type: Login



That'll work but only for POP3.  I guess it it depends on what the original poster wants :D.

---

### Post by Gordonbp531 on 2010-12-20
I don't think there IS any way of using Hotmail with anything else other than POP unless you use Outlook and the Outlook connector...or Windows Live Mail.

---

### Post by Foxcow on 2010-12-20
> **gendibal said:**
> I don't think there IS any way of using Hotmail with anything else other than POP unless you use Outlook and the Outlook connector...or Windows Live Mail.



I use my Windows Live/hotmail account via Evolution and its set up as an IMAP account.

---

### Post by Foxcow on 2010-12-20
> **gendibal said:**
> I don't think there IS any way of using Hotmail with anything else other than POP unless you use Outlook and the Outlook connector...or Windows Live Mail.



Do you know if there is a difference between Windows Live Mail and hotmail?  I just signed into my Hotmail account to see if I could replicate what I did with my Live account and as of yet, haven't found the settings.

---


---
title: "How can i send an email to a gmail account from the command line?"
date: 2011-03-02
forum: General Help
---

### Post by ~Middle on 2011-03-02
Pretty much all in the title, i am working on a neat little bash script, and i want the output to be mailed to my email account. So far i have tried installing sendmail then running:  mail -s Test [email]myemail@gmail.com[/email]  But that hasn't worked; and i did check my spam folder.   Am i missing something or is there a better technique all together?  Thanks a lot!

---

### Post by rbishop on 2011-03-02
Where is your server located?  If it's connected to a home high speed account your provider is probably blocking the connection.  Just my $0.02.

---

### Post by ~Middle on 2011-03-02
Wait do i need to setup a mail server?  I thought it was simpler than that =s  Thanks

---

### Post by ~Middle on 2011-03-02
These forums are too big!   As soon as it goes off the first page, its gone, and that is pretty quick!  I will post in smaller sections in the future!  Thanks

---

### Post by kaibob on 2011-03-03
You may want to try sendemail, a small utility that's available in the Synaptic Package Manager. The following is an example of how this utility might be used in a shell script. I regularly use sendemail to forward attachments to my gmail account, and it works great. 

```
sendemail \
  -f kaibob@verizon.net \     # Sender's email address.
  -t middle@gmail.com \       # Recipient's email address.
  -u "Subject" \              # Email subject.
  -m "Message" \              # Email message body.
  -s outgoing.verizon.net \   # SMTP server.
  -xu kaibob \                # Username.
  -xp 123456                  # Password.
```

---

### Post by ~Middle on 2011-03-04
Could you possibly just give me like a one line commamd to send an email.  And do i need to set up something for the last three options?

---

### Post by lisati on 2011-03-04
> **~Middle said:**
> Could you possibly just give me like a one line commamd to send an email.  And do i need to set up something for the last three options?

The example given by kaibob *can* be done on one line, it's just that it's sometimes easier to present it over multiple lines. 

```

sendemail -f kaibob@send.com -t kaibob@receive.com -u "Subject"  -m "<put your message here>"   -s outgoing.send.com -xu username -xp password

```

---

### Post by VCoolio on 2011-03-04
You could setup and use mutt. Create a ~/.muttrc like this:```
set imap_user = "you@gmail.com"
set imap_pass = "YourPassword"

set smtp_url = "smtp://you@smtp.gmail.com:587/"
set smtp_pass = "YourPassword"
set from = "you@gmail.com"
set realname = "Your Name"

set folder = "imaps://imap.gmail.com:993"
set spoolfile = "+INBOX"
set postponed="+[Gmail]/Drafts"
```
Then a oneliner like this:```
mutt -i /path/to/file -s "Subject here" recipient@domain.com
or
<command that generates output> | mutt -s "subject" recipient@domain.com
```
mutt -i file will put file in message; mutt -a will attach file. Have fun. Man mutt.

Edit: 700th post. Yay! \\:D/

---

### Post by ~Middle on 2011-03-04
Thanks a lot for that!  Quick question do i need to sign up for something with sendmail to get it to work?  If i do then mutt looks like an excellent option!  Thanks

---


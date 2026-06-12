---
title: "Msmtp to send mail from command line"
date: 2009-11-19
forum: General Help
---

### Post by Rayve on 2009-11-19
Sorry to post a thread which I know has been opened before, but I've been over at least 50 similar threads and haven't been able to send email from the command line.

All I'm looking for is something I can set up to send a simple, one-line text message to my cell phone as a sort of alarm-reminder at a certain time, and I figure if I can get it going through the command line (or a simple script), I can set it to a cron and it'll be perfect.

I've tried Mutt, sendEmail, mail, msmtp, Mutt with Gmail, and more.  Right now, when I do "sendEmail -f [EMAIL="fromemail@domain.com"]fromemail@domain.com[/EMAIL] -t [EMAIL="cellphone@carrier.net"]cellphone@carrier.net[/EMAIL] -m Reminder" it says message completed successfully, but no text message comes through.

When I try to use mutt, I can create a To email and a Subject, but then when it tries to open (I'm assuming) the body of the email, I get an error on gedit about "Could not open the file: gedit has not been able to detect the character coding.  Please check that you are not trying to open a binary file.  Select a character coding from the menu and try again." and I can't go any further.

Trying to use msmtp... hm, okay.  So I just tried 

```


msmtp phonenumber@carrier.net


```and it worked, I got a text message on my phone from [EMAIL="myaccount@gmail.com"]myaccount@gmail.com[/EMAIL]... but it's a blank message.  Is there anything I can do to make it have at least a subject?  Message or subject line, both aren't necessary, one or the other will do just fine.

EDIT: I can now do "mail -s "Subject" [email]phonenumber@carrier.net[/email]" and it works fine (thanks in part to [http://georgia.ubuntuforums.org/showthread.php?p=7012161](http://georgia.ubuntuforums.org/showthread.php?p=7012161) and being able to spell /usr correctly...) but I have to be there to press Ctrl+D.  The line at the bottom of the referenced post mentions putting it in a Python script, but is that enough to not have to do anything interactively at the terminal?

---

### Post by diesch on 2009-11-19
Use
```
 echo 'some text' | mail -s "Subject" [EMAIL="phonenumber@carrier.net"]phonenumber@example.com[/EMAIL]
```

---

### Post by Rayve on 2009-11-19
Excellent! Hours of work, for that.  :)  Thanks!

---

### Post by dcstar on 2009-11-19
> **diesch said:**
> Use
```
 echo 'some text' | mail -s "Subject" [EMAIL="phonenumber@carrier.net"]phonenumber@example.com[/EMAIL]
```

```
cat filename | mail -s "Subjext" name@address
```

---


---
title: "Simple sendmail question"
date: 2006-06-15
forum: General Help
---

### Post by SadaraX on 2006-06-15
All I want is the ability to have a script sent a single one line message to my gmail account when necessary. I am completely new to linux console mail (though not to linux or scripting). I do not need it to do anything very complicated, I just want know a more or less one line command (if possible) to send an email to a specified gmail account.

After reading through all the manuals and googling the forum, most of it seems to be about configuring sendmail, not actually sending an email. I have apt-get installed sendmail but there is not 'mail' command found in my system.

Can someone help me?

---

### Post by rai4shu2 on 2006-06-15
I don't know much myself, but I can quote from perldoc:

```
Use the "sendmail" program directly:

           open(SENDMAIL, "&#9474;/usr/lib/sendmail -oi -t -odq")
                               or die "Can&#8217;t fork for sendmail: $!\n";
           print SENDMAIL <<"EOF";
           From: User Originating Mail <me\@host>
           To: Final Destination <you\@otherhost>
           Subject: A relevant subject line

           Body of the message goes here after the blank line
           in as many lines as you like.
           EOF
           close(SENDMAIL)     or warn "sendmail didn&#8217;t close nicely";
```

---

### Post by ifokkema on 2006-06-15
[QUOTE=SadaraX]All I want is the ability to have a script sent a single one line message to my gmail account when necessary. I am completely new to linux console mail (though not to linux or scripting). I do not need it to do anything very complicated, I just want know a more or less one line command (if possible) to send an email to a specified gmail account.

After reading through all the manuals and googling the forum, most of it seems to be about configuring sendmail, not actually sending an email. I have apt-get installed sendmail but there is not 'mail' command found in my system.

Can someone help me?[/QUOTE]

The 'mail' executable is from the package mailx (although mailutils also seems to provide it). I've quickly gone through the manpage, and altough there are lots of things you can specify directly in the command as an argument, the actual mail body doesn't seem to be one. You may be able to use a here-document (aren't these called like that?) - but the suggestion above to directly talk to sendmail might help you out, too.

---


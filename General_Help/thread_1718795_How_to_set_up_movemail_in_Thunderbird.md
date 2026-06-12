---
title: "How to set up movemail in Thunderbird"
date: 2011-03-31
forum: General Help
---

### Post by Ralph L on 2011-03-31
I understand that a movemail account under Thunderbird should be able to pick up local email from the file /var/spool/mail/ralph and put it into the TB Inbox. (ralph is my account name and ralph-laptop is my hostname.) However, I don't know how to set it up to make it work. Under TB I go to File>New>Other Accounts, click Unix Mailspool (Movemail), and click next. However, at this point I don't know what to enter. Should the name be ralph (my account name)? Should the email address be ralph@ralph-laptop or my external email address at "mylastname@mchsi.com? Should the outgoing user name be ralph or mylastname (part of my external email address? Should I use my default outgoing server, which sends mail to mail.mchsi.com or should I use ralph@ralph-laptop, or just ralph-laptop?

I am running Lucid and Thunderbird 3.1.4

Any help much appreciated.
Ralph

---

### Post by Ralph L on 2011-04-08
With the help of ([http://forums.debian.net/viewtopic.php?f=5&t=8707](http://forums.debian.net/viewtopic.php?f=5&t=8707)) I was able to configure Movemail in TB to pickup local mail from /var/spool/mail/ralph where sendmail sends its mail by default.  (Actually /var/spool/mail/ralph is just a link to /var/mail/ralph).  Here are my settings:

Go TB>Edit>Account Settings.  At the bottom of the left pane select Add Other Account.  In the window that comes up check Unix Mailspool (Movemail).  

Set up the Default Identity to be:  
Your Name: username (in my case "ralph")
Email Address:  username (ralph)
Reply-to Address: username (ralph)

Set Server Name to be name of computer (ralph-laptop)
Under "Copies&Folders set everything to username@computername (ralph@ralph-laptop)

Under Outgoing Server add a new server:  It should have Port 25, Connection Security: None, Authentication method: No authentication.

Set the Movemail Account (under first level in left pane) to use this Outgoing Server.

Test it by going to Terminal and typeing "sendmail username" (sendmail ralph).  Type in a message, then a line with only a period (.) in it.  This should send the message.  Click on the Inbox of the new Movemail account and click Get Mail.  This should show the message.

Note that TB has a bug in it as described in [http://ubuntuforums.org/showthread.php?t=1711482](http://ubuntuforums.org/showthread.php?t=1711482).

For a discussion of why I needed movemail see:  [http://ubuntuforums.org/showthread.php?t=1711482](http://ubuntuforums.org/showthread.php?t=1711482)

Ralph

---


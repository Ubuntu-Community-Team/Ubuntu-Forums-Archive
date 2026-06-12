---
title: "How Do I Receive Email From the Command Line?"
date: 2011-05-20
forum: General Help
---

### Post by sgreenwood on 2011-05-20
**Background:** I want to send and receive emails from the command line. I'm an OS X immigrant and I don't know my way around a shell. I learned what sudo and man pages are last week. I'm hoping to learn more by doing more in the Terminal, and I check my emails a lot, so that would be a nice place to start.

I've had a root around, but there doesn't seem to be much on the relevant fora or wikis to help me.

**The core of the problem:** When I enter

```
$ mail
```

the shell returns

```
No mail for USER
```

I know that there's mail waiting for me. When I log into Gmail in my web browser, I can see it. So, I assume that the problem is that heirloom-mailx (the mail app I've installed) isn't connecting to my Gmail account for some reason.

I originally also noticed that I couldn't send emails by typing

```
$ mail name@address.tld
```

but I found [this post]("http://klenwell.com/is/UbuntuCommandLineGmail"), and after following the steps it outlines, I have successfully composed and sent mail from the command line. I assume that I have just missed some fundamental final step in linking my Gmail account with mailx.

Do you know what I need to do to fix this? I'm really enjoying getting to grips with Linux, and I don't want to be stopped now by what seems to be such a piffling problem.

---

### Post by dcstar on 2011-05-20
> **sgreenwood said:**
> **Background:** I want to send and receive emails from the command line. I'm an OS X immigrant and I don't know my way around a shell. I learned what sudo and man pages are last week. I'm hoping to learn more by doing more in the Terminal, and I check my emails a lot, so that would be a nice place to start.

I've had a root around, but there doesn't seem to be much on the relevant fora or wikis to help me.

**The core of the problem:** When I enter

```
$ mail
```

the shell returns

```
No mail for USER
```
..........

The "mail" command only access your **local** system for **local** mail - it has absolutely nothing to do with accessing external mail servers.

---

### Post by Telengard C64 on 2011-05-20
In ye olden days when tens or hundreds of users accessed a single Unix server from dumb terminals, they needed some way to send messages to each other. That is what Linux's mail command is for. In these modern times of single user computers, such a command seems pretty useless (or at least I haven't found a good use for it.)

Now there actually may be a way to configure a real Internet email server to forward mail to your local Unix mail box, and thus you might read your Internet email from the Linux command line.

TLDR version: I dunno, but I would like to   :popcorn:

---

### Post by alem189 on 2011-05-20
You might want to look into the "mutt" e-mail program:
```
sudo apt-get install mutt
```
By default, it looks for mail on the local machine, but you can configure it to retrieve it from the server. Here is a guide:
[http://mutt.blackfish.org.uk/]("http://mutt.blackfish.org.uk/")

The "mail storage" section will help you set it up. I use imaps://<username>@imap.gmail.com/INBOX to access my mailbox, other providers will probably be different.

---

### Post by Stephen Morgan on 2011-05-21
Well, the mail command is still useful for those of us who like to send mail quickly from the terminal. For reading mail it is inferior to mutt, but if you use fetchmail to retrieve mail from your internet server (I use it with gmail just fine) you will be able to read and reply with the old mailx utility.

So, install and configure fetchmail, and possibly msmtp for sending, and you'll be golden.

---

### Post by nothingspecial on 2011-05-21
If you want a cli mail client, I would recommend alpine, here's a guide to setting it up

[http://kmandla.wordpress.com/2009/02/12/in-the-end-alpine-was-just-easier/](http://kmandla.wordpress.com/2009/02/12/in-the-end-alpine-was-just-easier/)

Here is a guide for mutt

[http://ubuntuforums.org/showthread.php?t=1021746](http://ubuntuforums.org/showthread.php?t=1021746)

if you prefer.

---

### Post by sgreenwood on 2011-05-22
> **dcstar said:**
> The "mail" command only access your **local** system for **local** mail - it has absolutely nothing to do with accessing external mail servers.

Thank you. That explains the problem.

> **Telengard C64 said:**
> In ye olden days when tens or hundreds of users accessed a single Unix server from dumb terminals, they needed some way to send messages to each other. That is what Linux's mail command is for.

Thank you for verbalising what I was beginning to grasp intuitively. I guess I have unrealistic expectations of what my system is geared to do, but I was hoping that whatever hack I needed to perform, someone had done it before me.

> **alem189 said:**
> The "mail storage" section will help you set it up. I use imaps://<username>@imap.gmail.com/INBOX to access my mailbox, other providers will probably be different.

Thank you. Seems like I need to *sudo get-apt install* five or six apps for everything I want to do.

> **Stephen Morgan said:**
> Well, the mail command is still useful for those of us who like to send mail quickly from the terminal. For reading mail it is inferior to mutt, but if you use fetchmail to retrieve mail from your internet server (I use it with gmail just fine) you will be able to read and reply with the old mailx utility.

So, install and configure fetchmail, and possibly msmtp for sending, and you'll be golden.

I'm afraid that, for whatever reason, I couldn't get fetchmail to work, even using tutorials to configure it. I kept getting the message

```
fetchmail: skipping poll of gmail.com, ppp0/0.0.0.0/0.0.0.0 down
```

I know that I needed to replace ppp0/0.0.0.0/0.0.0.0 with something more appropriate, but Gmail's IMAP setup page didn't seem to provide much help, and a cursory Google yielded nothing, so I decided to try alpine.

> **nothingspecial said:**
> If you want a cli mail client, I would recommend alpine, here's a guide to setting it up

[http://kmandla.wordpress.com/2009/02/12/in-the-end-alpine-was-just-easier/](http://kmandla.wordpress.com/2009/02/12/in-the-end-alpine-was-just-easier/)

Phew! After days of struggling with this, it took seconds to set up alpine. It would still be nice to be able to circumvent the alpine UI by calling up an inbox with the mail command, but I've given up hope of that now.

Thanks to everyone who offered advice on this. The journey has forced me to teach myself a lot about the shell, which is what I wanted in the first place. As an addendum, if anyone can tell me what I might have been doing wrong with fetchmail, I'd appreciate the help.

---

### Post by Stephen Morgan on 2011-05-22
So, you have a line like 

        interface [B]ppp0/0.0.0.0/0.0.0.0

[/B]in your .fetchmailrc?

There's no line like that in mine, fetchmail shouldn't actually need such a line in most cases.

Mine is like this:

```
set daemon 60
set logfile ~/.fetchmail_log

poll pop.gmail.com proto POP3
user "@gmail.com" pass "" is ""
ssl
fetchall
no keep
mda "/usr/bin/procmail -f %F -d %T";
```

I cut my details out of there, obviously.

Might not need that last line, either. That grabs the mail on the server, downloads it to the local mailbox accessible by mutt or mailx/mail and deletes it from the gmail server. Works fine for me.

---

### Post by sgreenwood on 2011-05-27
> **Stephen Morgan said:**
> So, you have a line like 

        interface [B]ppp0/0.0.0.0/0.0.0.0

[/B]in your .fetchmailrc?

There's no line like that in mine, fetchmail shouldn't actually need such a line in most cases.

Mine is like this:

```
set daemon 60
set logfile ~/.fetchmail_log

poll pop.gmail.com proto POP3
user "@gmail.com" pass "" is ""
ssl
fetchall
no keep
mda "/usr/bin/procmail -f %F -d %T";
```

I cut my details out of there, obviously.

Might not need that last line, either. That grabs the mail on the server, downloads it to the local mailbox accessible by mutt or mailx/mail and deletes it from the gmail server. Works fine for me.

Thank you! I got rid of that line, and now fetchmail seems to work. But now I'm getting:

```
fetchmail: Warning: the connection is insecure, continuing anyway. (Better use --sslcertck)
2 messages for USERNAME@gmail.com at pop.gmail.com.
reading message USERNAME@gmail.com@dy-in-xxxx.xxxxx.net:1 of 2 (xxxx header octets) (xxxx body octets) flushed
reading message USERNAME@gmail.com@dy-in-xxxx.xxxxx.net:2 of 2 (xxxx header octets) (xxxx body octets) flushed

```

Obviously, fetchmail has got as far as my inbox. It saw my messages and marked them as read ("flushed" them). But now I don't know how to read my messages. Typing mail told me only that I had no new messages.

---

### Post by Thewhistlingwind on 2011-05-27
> **sgreenwood said:**
> Thank you! I got rid of that line, and now fetchmail seems to work. But now I'm getting:

```
fetchmail: Warning: the connection is insecure, continuing anyway. (Better use --sslcertck)
2 messages for USERNAME@gmail.com at pop.gmail.com.
reading message USERNAME@gmail.com@dy-in-xxxx.xxxxx.net:1 of 2 (xxxx header octets) (xxxx body octets) flushed
reading message USERNAME@gmail.com@dy-in-xxxx.xxxxx.net:2 of 2 (xxxx header octets) (xxxx body octets) flushed

```Obviously, fetchmail has got as far as my inbox. It saw my messages and marked them as read ("flushed" them). But now I don't know how to read my messages. Typing mail told me only that I had no new messages.

I'm sorry but I can't let this go, not using ssl/etc will totally get your Gmail cracked.

(Or at least, greatly heightens the risk.)

---

### Post by sgreenwood on 2011-05-27
> **Thewhistlingwind said:**
> I'm sorry but I can't let this go, not using ssl/etc will totally get your Gmail cracked.

Okay. So, what should I do? Is there a way to use ssl to log into my Gmail from the command line, or is this a pipe dream I should abandon for security reasons?

---

### Post by Stephen Morgan on 2011-05-28
In the line that looks like:

```
user "@gmail.com" pass "password" is "user" here options ssl
```

replace "user" with your username on your machine so it puts the mail in right mailbox. If mail is showing no messages try running `sudo su` then typing mail again, that will log you in as root and if it's collected messages and not put them in your box it might have put them in for root. 

Adding 'options ssl' to the end of the line should work, if you have the ca-certificates package installed, I can't remember if it installs by default of if I installed it manually.

---

### Post by MattBD on 2011-05-29
The following .fetchmailrc works really well for me:
```
set daemon 3600
set logfile /home/username/.fetchmail.log
set no bouncemail
poll pop.gmail.com
        proto pop3
        auth password
        no dns
        user "username@gmail.com"
        pass "password"
        is username
        keep
        ssl

mda "/usr/bin/procmail -d %T"

```

Note the "set daemon 3600" - this is how often fetchmail will run in seconds - I run it once per hour. Once this is all done, all you need to just call fetchmail once from the command line and it will run at the specified interval.

I use procmail as well to filter my email (hence the line at the end), and use mutt to read it. I believe you can use IMAP with fetchmail as well, although I haven't tried it.

It's definitely worth checking out procmail as a mail filter - there's a lot you can do with it. It can filter out specific attachments, send emails that meet specific criteria straight to a specified folder (so for instance, all the ones from a specific mailing list might go to one folder), and automatically delete ones if necessary. The syntax is pretty daunting, but you can find a few useful procmail recipes on the web.

It's possible to use the mail command to send external email, but as far as I know you can only do so if you're actually running a mail server on that computer and it has a fully qualified domain name. I don't believe it's possible to use it with another email provider.

---

### Post by Stephen Morgan on 2011-05-29
> **MattBD said:**
> It's possible to use the mail command to send external email, but as far as I know you can only do so if you're actually running a mail server on that computer and it has a fully qualified domain name. I don't believe it's possible to use it with another email provider.

You can install msmtp, then add the line 

```
set sendmail="/usr/bin/msmtp"
```

to .mailrc, then put your account details in .msmtprc

After that the mail command will send via msmtp, which sends through normal smtp via whatever webserver (like gmail) you prefer.

---

### Post by MattBD on 2011-05-29
> **Stephen Morgan said:**
> You can install msmtp, then add the line 

```
set sendmail="/usr/bin/msmtp"
```

to .mailrc, then put your account details in .msmtprc

After that the mail command will send via msmtp, which sends through normal smtp via whatever webserver (like gmail) you prefer.

Ah, I had wondered about msmtp. I'd heard of it and that it could do that, but wasn't familiar with it. Oh well, learn something new every day!

---

### Post by dromichaetes on 2011-12-05
hello, I'm having the same problem as you, just trying to retrieve mail from my Gmail account and read it from the cli. Sofar I managed to get msmtp and mailx working (piece of cake, really) and I can now send emails to whomever I care. Still to solve is fetching the darn emails. I'm just curious which is the way to go: with Alpine or fetchmail? To which of the two have you settled in the end? Have you managed to get emails with fetchmail? As long as I put the emails in the local mailbox I should be able to read them with a simple 'mailx' from the command line, right?
 
P.S. I'm trying to stay in the cli as much as possible, for learning purposes, I'm aware that there are plenty of email clients out there, I just don't fancy them.

---


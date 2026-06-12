---
title: "Can't use 'mail' command in shell"
date: 2011-09-07
forum: General Help
---

### Post by yotamoo on 2011-09-07
Hi there
I am typing echo "hello, world" | mail [email]mymail@mail.com[/email]
and I get no error but also no mail.

When I first tried it I was informed that I don't have the
right package so I downloaded 'mailutils', is this the right
one? Another one was offered to me but I can't remember its name.

So to conclude I have no idea what to do :)
Thanks

---

### Post by btindie on 2011-09-07
Make sure you have an MTA installed such as Postfix installed and that you have the sendmail command available.
```
sudo service postfix status
sudo service postfix restart
```to make sure postfix is running.

---

### Post by haqking on 2011-09-07
> **yotamoo said:**
> Hi there
I am typing echo "hello, world" | mail [EMAIL="mymail@mail.com"]mymail@mail.com[/EMAIL]
and I get no error but also no mail.

When I first tried it I was informed that I don't have the
right package so I downloaded 'mailutils', is this the right
one? Another one was offered to me but I can't remember its name.

So to conclude I have no idea what to do :)
Thanks

sudo apt-get install sendmail

then when this is  installed  from prompt  type

**mail -s &#8220;Hello&#8221; [EMAIL="myemail@gmail.com"]myemail@gmail.com[/EMAIL]** and hit enter
this is a test message (i typed this on the new line afer hitting enter) ctrl+d
cc: ctrl+d
 

replace the email address with one to test with and your mail should get sent, may need to check junk filters in the mailbox

---

### Post by yotamoo on 2011-09-07
Hi, I tried what you said, and I keep getting this error:

[PHP]
yotamoo@yotamoo-desktop:~/workspace/ex3$ sudo apt-get install sendmail
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  sendmail: Depends: sendmail-bin but it is not going to be installed
E: Broken packages

[/PHP]

---

### Post by SeijiSensei on 2011-09-07
If you already have Postfix installed, Ubuntu will balk at installing sendmail.  I'd just use Postfix since it's the Ubuntu default.  Try 

```
sudo apt-get purge postfix sendmail
sudo apt-get install postfix
```

The "mail" command requires a "mail transfer agent" to handle the actual sending of the message.  Ubuntu uses Postfix for the standard MTA.

However, even if you have everything set up correctly, you might not actually be able to send outbound mail.  Many ISPs prohibit outbound SMTP traffic to remote servers to block spambots.  You'll want to look at /var/log/mail.log for details.

---

### Post by dcstar on 2011-09-08
> **yotamoo said:**
> Hi there
I am typing echo "hello, world" | mail [email]mymail@mail.com[/email]
and I get no error but also no mail.

When I first tried it I was informed that I don't have the
right package so I downloaded 'mailutils', is this the right
one? Another one was offered to me but I can't remember its name.


Install the **bsd-mailx** package.

---


---
title: "Outgoing mail server? Where to start?"
date: 2010-10-07
forum: General Help
---

### Post by leesiulung on 2010-10-07
I need an outgoing mail server setup on Ubuntu 9.10 for a PHP/Drupal setup. 

I did some research on Postfix, but the setup is somewhat involved with SPF, TXT, main.cf and mailx. Not sure what all of those are and I read the tutorial here:  


[LIST]
[*][Postfix - Installation]("http://ubuntuforums.org/index.php/Postfix_-_Installation")
[*][Postfix - Basic Settings  in main.cf]("http://ubuntuforums.org/index.php/Postfix_-_Basic_Settings_in_main.cf")
[*][Postfix - MX Records  and Receiving Emails]("http://ubuntuforums.org/index.php/Postfix_-_MX_Records_and_Receiving_Emails")
[*][Postfix - Using Telnet  to Test Postfix]("http://ubuntuforums.org/index.php/Postfix_-_Using_Telnet_to_Test_Postfix")
[*][Postfix - Checking for an  Open Relay]("http://ubuntuforums.org/index.php/Postfix_-_Checking_for_an_Open_Relay")
[/LIST]
Any suggestions on where I should start to setup and secure an outgoing mail server only (I receive mail through Google Apps) on Ubuntu? 

Links to resources would be good and yes, I googled.

I feel really lost. In fact, I feel really lost in general on Linux. Help would be much appreciated! :P

---

### Post by Merthod on 2010-10-07
There's a SMTP module on Drupal for outgoing mail. Just install it and configure your email account SMTP info into it. The own module will specify the steps to take to get it working.

The CMS have its configuration bundled in with its modules. If you are developing the php files directly you can just enable your php mail function. For that go check into php.net site.

[http://drupal.org/project/phpmailer](http://drupal.org/project/phpmailer)
[http://drupal.org/project/smtp](http://drupal.org/project/smtp)

---

### Post by leesiulung on 2010-10-07
> **Merthod said:**
> There's a SMTP module on Drupal for outgoing mail. Just install it and configure your email account SMTP info into it. The own module will specify the steps to take to get it working.

The CMS have its configuration bundled in with its modules. If you are developing the php files directly you can just enable your php mail function. For that go check into php.net site.

[http://drupal.org/project/phpmailer](http://drupal.org/project/phpmailer)
[http://drupal.org/project/smtp](http://drupal.org/project/smtp)

Thanks!

That is one way of doing it, but I'm not sure Google Apps will be too happy about me using their service to send out mass email (not spam, just registration information to new account holders). I guess the alternative is to buy a service, but that would be costly.

Is it difficult to setup and secure your own outgoing email server?

---

### Post by leesiulung on 2010-10-08
For those wondering about this in the future, I followed an excellent article here:

[http://articles.slicehost.com/2010/3/1/barebones-postfix-install-for-ubuntu](http://articles.slicehost.com/2010/3/1/barebones-postfix-install-for-ubuntu)

Works like a charm!

---


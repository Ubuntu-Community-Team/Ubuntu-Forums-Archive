---
title: "howto setup postfix to send emails out with gmail in 11.10"
date: 2011-10-21
forum: General Help
---

### Post by alfonso78 on 2011-10-21
You want to send ONLY email out from your box using postfix (which comes preinstalled in ubuntu 11.10) using a gmail account.

[COLOR="Red"]Actually, in the meanwhile I found [this]("http://zackreed.me/articles/39-send-system-email-with-gmail-and-ssmtp") that might solve your problem WAY easier.[/COLOR]

I had to work on this for a while, but mainly I looked at:

[http://bookmarks.honewatson.com/2008/04/20/postfix-gmail-smtp-relay/](http://bookmarks.honewatson.com/2008/04/20/postfix-gmail-smtp-relay/)
[http://prantran.blogspot.com/2007/01/getting-postfix-to-work-on-ubuntu-with.html](http://prantran.blogspot.com/2007/01/getting-postfix-to-work-on-ubuntu-with.html)
[https://mail.google.com/support/bin/answer.py?answer=14257](https://mail.google.com/support/bin/answer.py?answer=14257)
[http://www.openssl.org/docs/apps/ca.html](http://www.openssl.org/docs/apps/ca.html)
[http://www.google.com/support/forum/p/gmail/thread?tid=7e4a679f5917149e&hl=en](http://www.google.com/support/forum/p/gmail/thread?tid=7e4a679f5917149e&hl=en)
[http://www.linuxquestions.org/questions/linux-software-2/how-do-you-test-postfix-for-sending-mail-out-106027/](http://www.linuxquestions.org/questions/linux-software-2/how-do-you-test-postfix-for-sending-mail-out-106027/)
[http://fixunix.com/openssl/248250-re-ca-client-failed-update-database-txt_db-error-number-2-a.html](http://fixunix.com/openssl/248250-re-ca-client-failed-update-database-txt_db-error-number-2-a.html)

This howto should help you (possibly):

```
$ /usr/lib/ssl/misc/CA.sh -newca
CA certificate filename (or enter to create)
**(press Enter here)**
Making CA certificate ...
Generating a 1024 bit RSA private key
..........++++++
.........++++++
writing new private key to './demoCA/private/./cakey.pem'
Enter PEM pass phrase: **<type a password here>**
Verifying - Enter PEM pass phrase: **<retype the password>**
-----
You are about to be asked to enter information that will be incorporated
into your certificate request.
What you are about to enter is what is called a Distinguished Name or a DN.
There are quite a few fields but you can leave some blank
For some fields there will be a default value,
If you enter '.', the field will be left blank.
-----
Country Name (2 letter code) [AU]: **<enter>**
State or Province Name (full name) [Some-State]: **<enter>**
Locality Name (eg, city) []: **<enter>**
Organization Name (eg, company) [Internet Widgits Pty Ltd]: **<enter>**
Organizational Unit Name (eg, section) []: **<enter>**
Common Name (eg, YOUR name) []: **<your name>**
Email Address []: **<your email>**

Please enter the following 'extra' attributes
to be sent with your certificate request
A challenge password []: **<enter>**
An optional company name []: **<enter>**
Using configuration from /usr/lib/ssl/openssl.cnf
Enter pass phrase for ./demoCA/private/./cakey.pem: **<same password as before>**
Check that the request matches the signature
Signature ok

```

```
$ openssl genrsa -out NAS.key 1024
Generating RSA private key, 1024 bit long modulus

$ openssl req -new -key NAS.key -out NAS.csr -days 3650
You are about to be asked to enter information that will be incorporated
into your certificate request.
What you are about to enter is what is called a Distinguished Name or a DN.
There are quite a few fields but you can leave some blank
For some fields there will be a default value,
If you enter '.', the field will be left blank.
-----
Country Name (2 letter code) [AU]: **<enter>**
State or Province Name (full name) [Some-State]: **<enter>**
Locality Name (eg, city) []: **<enter>**
Organization Name (eg, company) [Internet Widgits Pty Ltd]: **<enter>**
Organizational Unit Name (eg, section) []: **<type something here, this must be different from above>**
Common Name (eg, YOUR name) []: **<your name>**
Email Address []: **<your email>**

Please enter the following 'extra' attributes
to be sent with your certificate request
A challenge password []: **<enter>**
An optional company name []: **<enter>**

$ openssl ca -days 3650 -crldays 3650 -out NAS.pem -infiles NAS.csr
Using configuration from /usr/lib/ssl/openssl.cnf
Enter pass phrase for ./demoCA/private/cakey.pem: **<same password as before>**
Check that the request matches the signature
Signature ok

Certificate is to be certified until Oct 18 11:08:58 2021 GMT (365 days)
Sign the certificate? [y/n]: **<type y>**


1 out of 1 certificate requests certified, commit? [y/n] **<type y>**
Write out database with 1 new entries
Data Base Updated


```

```

sudo mkdir /etc/postfix/certs
sudo cp NAS.key NAS.pem /etc/postfix/certs
sudo cp /etc/ssl/certs/Equifax_Secure_CA.pem  /etc/postfix/certs/cacert.pem

```

then create /etc/postfix/sasl/sasl_passwd

```
sudo vi /etc/postfix/sasl/sasl_passwd
```

and enter your email account and password. You can create a new gmail account if you are not happy to leave your password in the file. Also in case you sometimes change your own gmail password, you don't have to remember to change it here.

the file should look like this:

```
gmail-smtp.l.google.com myaccount@gmail.com:mypassword
smtp.gmail.com myaccount@gmail.com:mypassword
```

```
sudo chmod 400 /etc/postfix/sasl/sasl_passwd
```

then edit /etc/postfix/main.cf

```
sudo cp /etc/postfix/main.cf /etc/postfix/main.cf.orig
sudo vi /etc/postfix/main.cf
```

this is how my looks now (in bold the differences):

```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

[B]# auth
smtp_sasl_auth_enable=yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl/sasl_passwd

# TLS client side certificate
smtp_use_tls = yes
smtp_sasl_security_options = noanonymous
smtp_sasl_tls_security_options = noanonymous
smtp_tls_note_starttls_offer = yes
tls_random_source = dev:/dev/urandom
smtp_tls_scert_verifydepth = 5
smtp_tls_CAfile = /etc/postfix/certs/cacert.pem
smtp_tls_key_file=/etc/postfix/certs/NAS.key
smtp_tls_cert_file=/etc/postfix/certs/NAS.pem
smtp_tls_enforce_peername = no
[/B]
# TLS parameters
[B]
smtpd_tls_ask_ccert = yes
smtpd_tls_req_ccert =no
[/B]
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = NAS
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = NAS, localhost.localdomain, , localhost
#relayhost =
**relayhost = [smtp.gmail.com]:587**
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all

```


```
sudo postmap /etc/postfix/sasl/sasl_passwd

sudo /etc/init.d/postfix reload
```

from the box you will send emails from, login with your browser to:
[http://www.google.com/accounts/DisplayUnlockCaptcha](http://www.google.com/accounts/DisplayUnlockCaptcha)
and unlock your IP to allow you to send email from postfix

open two terminals:

in one type tail -f /var/log/mail.log

and in other do your test to send out an email:

```

telnet 127.0.0.1 25
EHLO test
MAIL FROM: <from-email>
RCPT TO: <recipient-email>
DATA
Type message here.
<Enter>.<Enter>  **(press enter, type a dot, press enter)**
QUIT

```

if you don't get an email at your <recipient-email> check the error in /var/log/mail.log

if you're paranoid like me, I suggest to add this little script to your /etc/cron.hourly/ folder:

```
#!/bin/bash
#OUTBOX=`postqueue -p | grep -i empty`
OUTBOX=`postqueue -p | grep -v empty`
if [ ! -z "$OUTBOX" ]; then
  echo $OUTBOX | wall
fi

```

this will write on all terminals every hour if there is email pending in postfix. This way if something goes wrong and you are not capable to send out email at least you will notice on the terminal.

also be sure to read this for additional useful info:
[http://www.davidgrant.ca/setting_up_postfix_to_send_outgoing_mail_on_ubuntu](http://www.davidgrant.ca/setting_up_postfix_to_send_outgoing_mail_on_ubuntu)

---

### Post by wlaurance on 2011-12-09
Thank you, This helped me out very much!:o

---

### Post by dpippin on 2012-01-08
Thank you it worked great.  However, I had a quick question. You said > from the box you will send emails from, login with your browser to:
[http://www.google.com/accounts/DisplayUnlockCaptcha](http://www.google.com/accounts/DisplayUnlockCaptcha)
and unlock your IP to allow you to send email from postfix if I don't have a static IP is this going to cause problems everytime my IP changes since I will have to redo the CAPTCHA?  If this is the case is there a way to fix it?  Thanks and thanks again for all your help.

Oh also as a side note I had to change the relayhost to [smtp.gmail.com]:587 which you did but it just wasn't in bold.

---

### Post by alfonso78 on 2012-01-08
> **dpippin said:**
> Thank you it worked great.  However, I had a quick question. You said  if I don't have a static IP is this going to cause problems everytime my IP changes since I will have to redo the CAPTCHA?  If this is the case is there a way to fix it?  Thanks and thanks again for all your help.

Oh also as a side note I had to change the relayhost to [smtp.gmail.com]:587 which you did but it just wasn't in bold.

I'm glad it helped.
I understand your question, but I don't have an answer. I don't have static IP. I imagine google is smart enough to account for that so you should be fine. Please report back if this is not the case to inform others!

> Oh also as a side note I had to change the relayhost to [smtp.gmail.com]:587 which you did but it just wasn't in bold.

thanks, I fixed it!

---


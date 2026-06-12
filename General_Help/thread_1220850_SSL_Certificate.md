---
title: "SSL Certificate"
date: 2009-07-15
forum: General Help
---

### Post by Chetan26 on 2009-07-15
Hi,
    Iam a new User to UBuntu server Edition 9.04.
    I have got a SSL certificate which I have applied on my
    server. I have my application  running on port 8443

   with URL  like [https://ubuntu:8443/wstore](https://ubuntu:8443/wstore)

   I want to apply a registered domain name  [www.xxx.com](www.xxx.com)
   to the application above.
   Can you please help me how to get the SSL certificate applied
   and get  the website domain up and running.


Many thanks
Chetan

---

### Post by BkkBonanza on 2009-07-15
Assumin you are using Apache you should be able to modify your apache config file to refer to your ssl cert for the related domain. There are quite a few tutorials around for this... use google.

Here is one: [http://www.digicert.com/ssl-certificate-installation-apache.htm](http://www.digicert.com/ssl-certificate-installation-apache.htm)
But there are many so if this one isn't close to your server config then try some others until you get one close that makes sense.

After you make the change you need to restart Apache before it will work.

---

### Post by Chetan26 on 2009-07-20
Hi, 
   I work on Ubuntu 9.04 Server Edtion. I have generated a CSR and applied a SSL certificate on my server to host my Website.
But when I try to connect to the web site I get a message as

The certificate is untrusted , it is valid only for ubuntu.

How can I  Make it generic certificate and avoid this error message.

Please provide help.


Many thanks
Chetan

---

### Post by bodhi.zazen on 2009-07-20
How did you generate your cert ?

---

### Post by wojox on 2009-07-20
You already created a generic certificate, that is why it's untrusted. If you want it trusted you need to use a Certificate Provider like Verisign or Thwate.

[http://www.sslshopper.com/ssl-certificate-not-trusted-error.html](http://www.sslshopper.com/ssl-certificate-not-trusted-error.html)

---

### Post by HermanAB on 2009-07-20
Howdy,

You can try to get a free SSL certificate from RapidSSL.  Their wizards are a hit or miss affair, though I managed to get one once. Since then, I buy certs from Godaddy.

---

### Post by Chetan26 on 2009-07-21
I have  generated a CSR  and obtained a SSL Certificate  from Godaddy.

I have applied the SSL from Godaddy.

But I get this error only when i use on windows?

Is there any diff way to apply these SSL certificates?



Thanks
Chetan

---

### Post by HermanAB on 2009-07-21
Godaddy SSL Certs are 'chained'. You need to install two certificates, not just one (one for you and another for Godaddy itself).  Usually, you can simply append them to the same certificate file.  Is that what you did, or is the Godaddy cert missing?

---

### Post by Chetan26 on 2009-07-22
Hi,
     Initially I installed the certificate using Apache 2  on ubuntu 9.01
     server edition. But I had to change  my application  to port 80  and stop the Apache 2 . So now how can I reisntall the certificate without   apache 2?

      
thanks
chetan

---

### Post by bodhi.zazen on 2009-07-22
What are you trying to do exactly ?  Windows or Linux ? server or client ? Apache or lighttpd or what ?

What have you done so far ? What how-to are you following ?

---

### Post by Chetan26 on 2009-07-23
Hi ALL,
       I want to apply  a SSL certificate  for my web site.
       The  problem is  my application is running on port 80.
       I assume apache also runs on port 80 , so Iam unable  to run
       both at the same time.
       Can you please tell me how I  can change the port for apache and
       Apply my SSL certificate.

        Many thanks

Regards
Chetan

---

### Post by _sluimers_ on 2009-07-23
What's the name of the application?

Apache should run on port 80. 
I mean, that's where you are hosting your webpages on aren't you? 
It's a bit annoying when users have to go to hxxp://www.mywebpage.com:8080/ instead of just hxxp://www.mywebpage.com to access your site.

Anyway, you'll probably have to edit some .conf file. I'm not sure, but /etc/apache2/ports.conf and change Listen 80 to a port between 1024 and 65536, preferably a high one, try doing that, restart apache and tell me if it works.

---

### Post by Chetan26 on 2009-07-23
Hi ,
     I tried  changing the port to 8181.
     and SSL port to  5443.
     But when I access my website  still Iam getting  Certificate is not trusted  It is valid only for Ubuntu.

    please provide some help , Iam really struck here.


Thanks
Chetan

---

### Post by wojox on 2009-07-23
Self-signed certificates always cause browser errors like that, it's a security measure. You should have an option to add an exception.

If you want it to be trusted you need to have it issued with Thwarte or Verisign.

---

### Post by Chetan26 on 2009-07-23
I have generated a CSR using OpenSSL  and  for the Same Godaddy issued me a SSL certificate.
But  when I apply the certificate it  says  its  not trusted

and it is  self signed.

How can I resolve this  error?


Many Thanks
Chetan

---

### Post by Chetan26 on 2009-07-23
Hi ,
     I have generated a CSR using Open SSL  and sent it to  GOdaddy.
     They have issued me a SSL certificate [www.abc.com.crt](www.abc.com.crt).
     But when I apply this certificate  to my web site it says
     this is an untrusted certificate valid only for Ubuntu?

      Can you please help me how the ccertificate  can be made  trusted
      applied  successfully.


Thanks
Chetan

---

### Post by Chetan26 on 2009-07-23
Hi ALL,
        I have a web application running on Port 80 .
        I want to apply a  SSL certificate  to the web application.
        
        I have installed Apache2  and tried to  do the installation.
        I setup  all the virtua l  hosts for the SSL installation.
        But Iam facing conflict  on port 80  as both  apache and my app server  both cannot run on the same port.

 I changed the  apache ports to  8181 and SSL port to 1443.

But Still the Certificate cannot e applied and it says  its a Untrusted Certificate.


Iam totally confused  does SSL certificate deal with port or server?


If any  body has faced a similar problem or know the answer pls help me.


Iam deeply  struck and  lost a lot of time applying certificates .


pls  help me.

Thanks
Chetan

---

### Post by bodhi.zazen on 2009-07-23
Is this a self signed cert ?

And what are you doing with it ? https is port 443

---

### Post by cdenley on 2009-07-23
> **bodhi.zazen said:**
> Is this a self signed cert ?

And what are you doing with it ? https is port 443

Apparently it is a signed certificate from godaddy.
> **Chetan26 said:**
> Hi ,
     I have generated a CSR using Open SSL  and sent it to  GOdaddy.
     They have issued me a SSL certificate [www.abc.com.crt](www.abc.com.crt).
     But when I apply this certificate  to my web site it says
     this is an untrusted certificate valid only for Ubuntu?

      Can you please help me how the ccertificate  can be made  trusted
      applied  successfully.


Are you using the correct domain when connecting. If you connect using [https://abc.com/](https://abc.com/) or your IP when your certificate is for [www.abc.com](www.abc.com), then you will get a warning like that. Did you set SSLCertificateChainFile correctly in your apache config?
[http://httpd.apache.org/docs/2.2/mod/mod_ssl.html#sslcertificatechainfile](http://httpd.apache.org/docs/2.2/mod/mod_ssl.html#sslcertificatechainfile)

Can you post your domain here?

---

### Post by bodhi.zazen on 2009-07-23
I merged 5 threads in 3 forms and put them into general help.

@ Chetan26 please do not start multiple threads on the same topic as it causes confusion and duplication of effort.

Simply stating over and over that something is not working is not the best way to get help.

Please tell us what how to you are following and what yo have done to set up the certificate.

[https://help.ubuntu.com/community/OpenSSL](https://help.ubuntu.com/community/OpenSSL)

---

### Post by Chetan26 on 2009-07-24
Hi,
       Iam really  sorry for the multiple threads.
       Let me clearly explain you  my problem.

       I have  got a Ubuntu 9.04 Server  on which my web application is
       hosted on port 80.

       In order to secure my website I generated a CSR using OpenSSL 
       And obtained  SSL certificates and intermediae certificate from
       Godaddy.

       I installed apache2  for SSL installation  . But later on I found that  My application also runs on port 80  so I need to change the  port conf  for  Apache . I changed  listen port t0 8181  SSL port to  1443.

in the /apache2/sites-avaliable/default,default-ssl   files

I added  SSL Certificate and chain file paths  

I restarted  Apache.

When I access the  website from ubuntu  its  fine, but when I access it from WIndows  I get the below  error messages.

The certificate your using is untrusted. It is valid only for Ubuntu.

I tried to contact godaddy  for help , they simply  said this is an Ubuntu Issue  we cannot provide any help.

I thank Ubuntu forum for all the help and guidance.

Please  provide me some guidance  to resolve this Issue.


Regards
Chetan

---

### Post by cdenley on 2009-07-24
> **Chetan26 said:**
> 
The certificate your using is untrusted. It is valid only for Ubuntu.

That is literally what it said? Did you use "Ubuntu" for the Common Name in the certificate. Can you either provide step-by-step how you got your SSL certificate including the commands and input used to generate the CSR, or give us your domain?

---

### Post by bodhi.zazen on 2009-07-24
> **cdenley said:**
> That is literally what it said? Did you use "Ubuntu" for the Common Name in the certificate. Can you either provide step-by-step how you got your SSL certificate including the commands and input used to generate the CSR, or give us your domain?

+1

How did you generate the cert ? 

You do understand ssl does not secure you server ? It simply encrypts traffic.
You do understand the ssl uses https on port 443, not 80 ?

---

### Post by BkkBonanza on 2009-07-24
If you got your certificate from godaddy then it is not "self-signed". They should only have provided you with a certificate matching the domain name you requested and have control over, as specified in the "common name" field of your csr.

The certificate is not tied to a specific port but you need to access your web page on the port that you configured in apache. Hence if you configured port 1443 then you need to access your page via that port, eg. [http://www.abc.com:1443](http://www.abc.com:1443)

Ubuntu or not should have no bearing. You access a web page via a browser like Firefox or IE. Firefox and IE have different handling of certificates that may cause different messages even from the same certificate. All of this behaviour depends on the details so the only way for people to help you is by providing as much detail as possible.

We need exact detail of the common name used to get the certificate, the domain name you are accessing the page on, how you configured your apache to use the certificate and port number it listens on for the domain in question. And also any error messages in the apache error log file. Apache may have restarted fine but not enabled correctly your ssl functionality for that domain. If so it would emit messages into the log giving an indication what is wrong. 

There are situations where misconfiguration could cause it to work for Firefox but not IE. For example, you have mistakenly configured a certificate that has been accepted previously by Firefox but not IE.

Be as specific with details as possible and people here can help you. Right now there is just a lot of vague info that makes it hard to understand what you have done so far.

---


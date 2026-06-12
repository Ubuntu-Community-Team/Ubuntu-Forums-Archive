---
title: "Apache - SSL question"
date: 2006-06-02
forum: General Help
---

### Post by Ronbo on 2006-06-02
I am running a Dapper Lamp server with SSL for an intranet site at work, there are multiple departments in the county but want only one department to be able to access the site.  I have setup SSL, so each time someone accesses the site it issues the certificate to them to encrypt the traffic over the network, if they don't already have it.  I kind of want to have it work in reverse, I want to have the certificate already on the client computer in order to gain access, and if the certificate is not there I don't want it to be issued just to deny the connection to the directory and site.  After a bit of searching I have added the following to my 'httpd.conf' file:

SSLVerifyClient require
SSLVerifyDepth 1
SSLCACertificateFile /etc/apache2/ssl/apache.pem

But even if the certificate has been saved on the computer from a previous connection it still won't allow access.  Does the certificate have to be saved in another location on the client and if so whereabouts?  95% of the clients are XP computers and at least half of them use IE and the others use Firefox, so I actually am looking for how to configure each.  Any help or direction of where I may find some help would be greatly appreciated.

---

### Post by nemesa on 2006-06-03
Uhhh...

I'm not sure that I understand everything clearly... but I think that's not the right way to close specified clients from reaching a site.

I think SSL serves to encrypt the data between the clients and the server. You need a certificate for your domain, to make clients sure of who you are.

I don't think that's easy (or even possible) to make an SSL key based authentication...

You should try to enable a Basic password authentication for your site, and specify a group of IP addresses which can reach the site without password.

Or just deny anybody else who is not in your trusted list...

ie.:
```

Order deny,allow
Deny from all
Allow from 192.168.1.102
Allow from 192.168.1.192
...

```

If you are using Apache2:
[http://httpd.apache.org/docs/2.0/howto/auth.html](http://httpd.apache.org/docs/2.0/howto/auth.html)

If you are using Apache:
[http://httpd.apache.org/docs/1.3/howto/auth.html](http://httpd.apache.org/docs/1.3/howto/auth.html)

---

### Post by Ronbo on 2006-06-04
From what I've read the 'mod_ssl' package has the ability to verify a certificate on the client machine before providing access to the site.
  
> 
Client Authentication and Access Control

    * How can I authenticate clients based on certificates when I know all my clients?    [L]

      When you know your user community (i.e. a closed user group situation), as it's the case for instance in an Intranet, you can use plain certificate authentication. All you have to do is to create client certificates signed by your own CA certificate ca.crt and then verifiy the clients against this certificate.

      	  httpd.conf   	
      	
      			
      	

      #   require a client certificate which has to be directly
      #   signed by our CA certificate in ca.crt
      SSLVerifyClient require
      SSLVerifyDepth 1
      SSLCACertificateFile conf/ssl.crt/ca.crt


      	

    * How can I authenticate my clients for a particular URL based on certificates but still allow arbitrary clients to access the remaining parts of the server?    [L]

      For this we again use the per-directory reconfiguration feature of mod_ssl:

      	  httpd.conf   	
      	
      			
      	

      SSLVerifyClient none
      SSLCACertificateFile conf/ssl.crt/ca.crt
      <Location /secure/area>
      SSLVerifyClient require
      SSLVerifyDepth 1
      </Location>

Found this at:
[http://www.modssl.org/docs/2.8/ssl_howto.html]("http://www.modssl.org/docs/2.8/ssl_howto.html")

I might be confused though, am I reading this wrong?  If you could take a look and let me know what you think they are saying it would be appreciated.

---

### Post by nemesa on 2006-06-04
Everytime I learn something... Sorry... I don't know about this. You were right.

This is a great howto on this subject...
[http://www.garex.net/apache/](http://www.garex.net/apache/)

By the way, I don't know why do you want this in such a hard way, but good luck. ;)

---


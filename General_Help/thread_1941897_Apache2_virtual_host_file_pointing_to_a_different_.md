---
title: "Apache2 virtual host file pointing to a different server"
date: 2012-03-16
forum: General Help
---

### Post by spindler on 2012-03-16
I have a webserver on my network that hosts my production websites.  I want to add a development webserver and host my websites that on in development. 

I opened port 8080 for this development webserver but I cannot seam to be able to access the websites on the development server.   When i type the domain name into a web browser my default production website shows up.

Is there a way to create a virtual host file on my production website so that it points to a different server?

How would I do that?

Can you point me to a wiki?

---

### Post by Bobhuber on 2012-03-16
> **spindler said:**
> I have a webserver on my network that hosts my production websites.  I want to add a development webserver and host my websites that on in development. 

I opened port 8080 for this development webserver but I cannot seam to be able to access the websites on the development server.   When i type the domain name into a web browser my default production website shows up.

Is there a way to create a virtual host file on my production website so that it points to a different server?

How would I do that?

Can you point me to a wiki?
Is this a separate machine on the same network set up as a server or the same machine that your trying to access different files from. The easiest way to do what your trying to do is to set up a separate directory on your primary server (I.E /var/www/production)with a separate index file.To access it http:<mydomain-name>/production

---

### Post by spindler on 2012-03-16
My development server is a different server.   I need this because the webserver crashes while I am developing the site. 

So I want to separate the high risk websites ( development  sites ) from the stable sites. 

I must have a second server.  I opened port 8080 so as to access the site but I want to use domain extensions to remotely access the development site.

I think the issue I have is that the development site does not capture the request for the website.  I am not sure how to fix this.

The other way I thought I could solve this is to have my production server manage all of the requests but then redirect to the development server when need.

---


---
title: "Need Help with Dante SOCKS Server"
date: 2012-02-07
forum: General Help
---

### Post by hadi2 on 2012-02-07
Hi,
Dante server itself offers absolutely no support in terms of forums and such and I thought maybe I could get help from here.
Bottom line I want to setup a SOCKS proxy server with GSSAPI authentication. Here is what I did: I installed Dante Server and krb5kdc on Computer A and Dante Socksify program on Computer B ( Ubuntu's Dante server package doesn't have GSSAPI support and I had to compile Dante myself ) , I created a principal for the client and a service principal for Dante server with the following command in kadmin.local :
```
addprinc rcmd/<myhostname>@<myrealm>
ktadd -k /etc/sockd.keytab rcmd/<myhostname>@<myrealm>
```and then fired up the kdc server. 
To test the installation issued : 
```
socksify arora
```on the client, waited a minute or two and nothing happens but apparently socksify was able to get service tickets from the server and output of klist command on client shows the client principal and dante's rcmd tickets. Is this the correct way to do it?  Do I have to anything else to server configuration? 
Any help would be much appreciated I really need this .

---


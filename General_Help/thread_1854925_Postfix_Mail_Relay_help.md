---
title: "Postfix Mail Relay help"
date: 2011-10-05
forum: General Help
---

### Post by cgauvin on 2011-10-05
I am experiencing an issue with remote users in our company and I am looking for some help in configuring Postfix (or perhaps another mail server program if one would work better..)

The basic problem is that in order to send mail through outlook we need to use our ISPs SMTP server.   It will only allow mail sent mail from trusted IP addresses at our main office.   Remote users are able to get mail, unable to send.

What I am looking to do is set up a simple server using postfix to relay mail from those users to the ISPs SMTP.   I want the Untuntu server to authenticate users not at the local office then relay their mail over to the ISP.  I understand that I have to configure our router to port those requests to the server, that is not a problem.  Right now I am just looking to see how to set up the Ubuntu server so that it is securely sending mail along to the ISP.

*note*  I am not sure if there is a more specific category that this should be in.  Sorry if it is in the wrong spot, new to the forums.

---

### Post by SeijiSensei on 2011-10-05
It might make more sense to avoid the ISP altogether by renting a virtual server from a provider like [Linode]("http://www.linode.com/").  For $20/month you can build the server out in the "cloud" where all your users can access it.  You'll also get a static IP address with configurable reverse DNS resolution to improve the chances your mail will be accepted by remote servers.

I don't work for Linode, but I've been running a server there now for over a year.  Works like a charm, with competent and helpful tech support people as well.

---

### Post by cgauvin on 2011-10-05
> **SeijiSensei said:**
> It might make more sense to avoid the ISP altogether by renting a virtual server from a provider like [Linode]("http://www.linode.com/").  For $20/month you can build the server out in the "cloud" where all your users can access it.  You'll also get a static IP address with configurable reverse DNS resolution to improve the chances your mail will be accepted by remote servers.

I don't work for Linode, but I've been running a server there now for over a year.  Works like a charm, with competent and helpful tech support people as well.

Eventually we are going to be bringing an exchange server in house.  This is a stop gap until we get to that point.  I am not interested in signing up for additional services at this time.  

I am also curious if something like this is possible as I have never done it before and I would like to get more familiar with Postfix.

---

### Post by cgauvin on 2011-10-05
Bump?

---

### Post by dcstar on 2011-10-06
> **cgauvin said:**
> 
.........
What I am looking to do is set up a simple server using postfix to relay mail from those users to the ISPs SMTP.   I want the Untuntu server to authenticate users not at the local office then relay their mail over to the ISP.  I understand that I have to configure our router to port those requests to the server, that is not a problem.  Right now I am just looking to see how to set up the Ubuntu server so that it is securely sending mail along to the ISP.

*note*  I am not sure if there is a more specific category that this should be in.  Sorry if it is in the wrong spot, new to the forums.

Do a web search for "LAMP server" setup as this sort of thing should be possible.

The traditional way is to set up port 587 for authenticated logins and then allow relaying for the users.

---

### Post by cgauvin on 2011-10-06
Awesome thank you.

---

### Post by cgauvin on 2011-10-06
> **dcstar said:**
> The traditional way is to set up port 587 for authenticated logins and then allow relaying for the users.

You wouldn't happen to know where I could find a manual/faq/guide on how to do this?  I've got the LAMP components installed, now I just need figure out how to set up the relay.

---


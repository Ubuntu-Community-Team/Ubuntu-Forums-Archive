---
title: "Evolution mail"
date: 2009-09-19
forum: General Help
---

### Post by chaotzu on 2009-09-19
When I try to send mail I'm getting an error "Error while performing operation. Welcome response error: imp10 smtp.charter.net MTYxLjEzMC4xMzEuNDg= You must connect from Charter IP space. E1110."

Any have suggestions on how to fix the problem? Thanks

---

### Post by Bachstelze on 2009-09-19
You're trying to use the Charter SMTP server, which can only be used by Charter users.

---

### Post by chaotzu on 2009-09-19
What should I use instead?

---

### Post by solidblu on 2009-09-19
yeah it looks like Charter doesn't allow mail to be sent through that IP unless it is on a known list.  

You probably need to change your out going SMTP server to whatever ISP you have for internet access.  

As an example if you had comcast you would probably use smtp.comcast.net



Companies/Universties/Normal people with mail servers do thing like this to help fight SPAM by not letting people forge fake email going out their servers.

---

### Post by chaotzu on 2009-09-19
hmmmm I get my internet through my university, I'll try a few different things. Thanks for the help, I'll let you know if I figure it out.

---

### Post by chaotzu on 2009-09-19
My university mail isn't letting me send because I'm not sending as my university mail. The university is my ISP and it's called TigerNet, is there anyway I can use this or does it look like I'm out of luck?

---

### Post by solidblu on 2009-09-19
hmmm well try

telnet smtp.charter.net 25

What this does is just opens port 25 (SMTP port) to see what it says.

I personally instantly got that error message and it closed the port.
Normally you can type commands etc.



If so I would do a /sbin/ifconfig find your IP address (unless you are behind a router then you might need to login to the router and find it's ip ) and call the university's helpdesk

It looks like charter.net isn't your university because it is its own company.   


so you should do a google search for outgoing smtp  site:YOURUNIVERSITYSITE.edu   to see if you can find the settings.

---

### Post by chaotzu on 2009-09-19
I do get the same error and disconnected. I searched google but i can't find anything.

Actually I think I just figured it out. I go to Mizzou so I tried smtp.missouri.edu with my student login and password and it sent it. Yaaay! I'll send myself a message to see if I get it, thanks for the help guys.

---


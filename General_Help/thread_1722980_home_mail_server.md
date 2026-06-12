---
title: "home mail server"
date: 2011-04-06
forum: General Help
---

### Post by tiercel on 2011-04-06
I want to run a simple mail server.  By "simple" I mean I want something that I, myself, can install and configure without having to pull out more of what remains of my hair.  The number of users will be very small (2-4), I will not have to dynamically allocate new users who, for example, don't already have user accounts on the machine.  I would also prefer the email server to not be a major system hog since I will be running a web server and more importantly number-crunching software whose results the web server will be serving.

I want to be able to send emails out into the world and receive them at [email]myname@myhost.com[/email], and to be able to do so from the command line so I can send them out automatically when I complete number-crunching software runs.  Being able to connect a very simple mail client (e.g. pine/mutt/whatever) to make incoming emails easy to read would be nice.

Obstacles include the fact that, since I am running the machine at home, I am doing so from behind a DSL router and using DynDNS to route traffic to/from my dynamic IP.  

I have DynDNS's Custom DNS Service set up, I have MX records, I have SendLabs Gateway (formerly MailHop I guess) aiming at a custom port number to circumvent any residential port 25 blocking.  I am running Ubuntu Server 10.04LTS, LAMP suite (Apache+PHP+SQL), and will be running a web server and invoking local number crunching software via PHP and sending out results via email.

What frustrates me to no end is that if I want to serve web pages, a package install of Apache *starts serving web pages*.  Yes, there are a lot of things to consider and configure and secure depending on what I want my web server to *do* (e.g. SSL certificates etc), but it *works*.  Email seems to be this mysteriously quantum jump in difficulty in that it seems either nigh-impossible to get to work at all (e.g. Postfix+7000 dwarves+an infinite number of manual configuration files), or if it comes as a "plug and play" suite, it has a bunch of bells and whistles I don't necessarily need -- which might be OK in itself, since I might use them down the line, except for the part where it makes it hard to figure out how to configure anything (e.g. Citadel, where I had to search *these* forums just to find out which ports I need to open & forward because the documentation is not very clear, and I'm not even clear where the SMTP configuration even takes place).

I am getting very frustrated, having tried Postfix, more recently Citadel.  Does anyone have any suggestions for how I can get a simple email server up and running that I can configure to work through DynDNS so that I can just send and receive email and go back to banging my head against designing a web site that does what I want?

Thanks.

---


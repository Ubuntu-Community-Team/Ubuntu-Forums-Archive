---
title: "Newbie and Mail Server Help"
date: 2009-08-14
forum: General Help
---

### Post by fusion1275 on 2009-08-14
Hi there,

I have just joined this forum as I am totally stuck and have no idea how to carry on with my home project.

I would like to set up a mail server but I have no idea or rather I am confused how to...

I have an Ubuntu server in my cupboard and around the house I use windows with Thunderbird.

Can someone confirm if this is the correct route for a mail server:

1) mail is sent to my ISP servers from the outside world
2) Fetchmail installed on my server retrieves from my ISP servers
3) Dovecot delivers the new mail to a mailbox configured
4) Spam Assassin filters the rubbish from the good
5) Mozilla Thunderbird connects to server (somehow) and retrieves or views the new mail

Is that right?

also I am a bit confused when I need to put in my "server mail domain name" in some of these applications.

I have 2 websites with registered domains that I paid for but im not using them for any email. I have them set up in the /etc/hosts file like this for apache2:

192.168.0.6 website1.com  website1
192.168.0.6 website2.com  website2

But what do I put in the mail settings for my setup? 

my servers hostname is sapphire.. can I use that? Can I choose anything/any name? Or do I have to buy a registered domain for this?

Sorry about the amount of questions.. its a learning curve for me

I hope someone can give me an idiots guide/explanation :)

---

### Post by Rich-Newbie on 2009-08-14
Hi

Its seems alot of us are all trying to achieve the same thing. I have found a couple of very use-full tutorials.

This is a good one, if you want to host multiple accounts on multiple domain. [http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu9.04](http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu9.04)


Citadel ([www.citadel.org]("http://www.citadel.org")), and Zimbra are ones that have been recommended for ease of use. According to on of the posters in the form's he reckons you can have a e-mail server up and running within 20 minutes, as oppose to doing it the manual way, which could take 2 weeks, or longer if your a newbie.

This is another tutorial I came across about setting up a mail server in Linux: [http://www.alepe.com/about_computers/about_linux/setting_up_a_mail_server_in_ubuntu.html](http://www.alepe.com/about_computers/about_linux/setting_up_a_mail_server_in_ubuntu.html)

Another place to read through is the Admin manual, which helped me get a better understanding of how the mail system works.

Good luck, I will keep updating the post I created with my progress, so others can benefit. I am also a linux/Ubuntu Newbie, I want to try and go the route of setting up the mail server from scratch, based on a variety of tutorials and help files.

Richard

---

### Post by fusion1275 on 2009-08-14
Thanks for your help Rich!

Yeah looks like we are all in the same boat here :)

I think I will be using these packages:

ISP => Fetchmail => Spam Assassin => Dovecot => Home client/Web portal

So do you think I will still need to set up a virtual domain name for this?

---

### Post by alphacrucis2 on 2009-08-14
> **fusion1275 said:**
> Hi there,

I have just joined this forum as I am totally stuck and have no idea how to carry on with my home project.

I would like to set up a mail server but I have no idea or rather I am confused how to...

I have an Ubuntu server in my cupboard and around the house I use windows with Thunderbird.

Can someone confirm if this is the correct route for a mail server:

1) mail is sent to my ISP servers from the outside world
2) Fetchmail installed on my server retrieves from my ISP servers
3) Dovecot delivers the new mail to a mailbox configured
4) Spam Assassin filters the rubbish from the good
5) Mozilla Thunderbird connects to server (somehow) and retrieves or views the new mail

Is that right?

also I am a bit confused when I need to put in my "server mail domain name" in some of these applications.

I have 2 websites with registered domains that I paid for but im not using them for any email. I have them set up in the /etc/hosts file like this for apache2:

192.168.0.6 website1.com  website1
192.168.0.6 website2.com  website2

But what do I put in the mail settings for my setup? 

my servers hostname is sapphire.. can I use that? Can I choose anything/any name? Or do I have to buy a registered domain for this?

Sorry about the amount of questions.. its a learning curve for me

I hope someone can give me an idiots guide/explanation :)

If you already own a domain then just add an MX record pointing at the IP address of your mail server. If it doesn't have a public IP address then you would point the MX record at the public address of your router (you would probably need to get your ISP to allocate you a static one) and you would then configure your router to port forward smtp/smtps from your router to your mail server. If you do this, then you don't use your ISP's mail servers at all for mail pertaining to <youremailaddress>@<yourowndomainname>.

 Mail clients such as Thunderbird use either POP or IMAP protocol to receive/view mail from the mail server. Like most mail clients, Thunderbird can support multiple mail servers based on which servers are supporting which email addresses. So you can configure it to receive <youremailaddress>@<ispdomain> from the ISP's server and <youremailaddress>@<yourowndomainname> from your own server. For outgoing mail you can configure one or more SMTP servers. Don't forget to match the correct outgoing server to the associated mail account. Your ISP probably wont allow you to forward mail from a domain other than their own through their server.

---


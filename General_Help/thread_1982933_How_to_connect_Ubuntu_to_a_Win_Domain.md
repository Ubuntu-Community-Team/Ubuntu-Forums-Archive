---
title: "How to connect Ubuntu to a Win Domain?"
date: 2012-05-19
forum: General Help
---

### Post by Kalma on 2012-05-19
Hi there,

I'm fed up of my company laptop since it has Windo$ installed. It is slow and crashes from time to time. I have installed Ubuntu 12.04 as Dual Boot, but I have found two problems in order to work inside the corporate LAN:

1. I don't know how to configure the proxy, because I should use  an automatic configuration (based on a configuration pac file [http://whatever.pac](http://whatever.pac)). I have configured this on firefox and the General Proxy Settings, so I can browse the Internet, but apt-get doesn't work, so I can not install or update programs.
2. I can not access the shared folders because I should join the corporate domain. I don't know how to do this in Ubuntu. I have googled around and many posts advice to use likewise-open but, when I try to install it using a .deb package, it arises a bunch of incompatibilities. I do not know if this is beacuse of the new distro or because of the proxy problem... Is there any other way to join a Windows Domain?

I hope you can help me.

---

### Post by 3Miro on 2012-05-19
Look at the top-right corner and the wi-fi/wired networking applet icon. From the networking applet, you can select "edit connection" and enable proxy globally for all programs (including apt-get).

I can see shared windows folders by just opening the file manager and selecting "Browse Network" in the lower left corner. It used to be case that you had to install a bunch of additional programs, but now it should just work by default. (I may be wrong on this one).

---

### Post by Kalma on 2012-05-21
Thanks a lot for your reply, 3Miro. The problem is that I can not find where to indicate the proxy settings wihtin the Netowrk Settings Manager... I clicked on "Edit Connections", then I choosed the Wired Connection, and then "Edit", but I don't see where to set the proxy on none of the four sections (Wired (or WiFi) / Security / Ipv4 / Ipv6).

Thanks again.

---

### Post by Kalma on 2012-05-21
Sorry, I forgot the second part. I am able to access those Windows folders which have been shared using samba, but not some others that are just the Corporate ones, and I suspect they used the Domain services to share them. I believe I have first to join the Domain in order to access those folders.

---

### Post by Cheesemill on 2012-05-21
If it's a company laptop then talk to the IT department, they will be able to talk you through setting it all up if they support Ubuntu.

If they don't support Ubuntu then it's probably against company IT policy for you to be installing it on the laptop in the first place.

---

### Post by Kalma on 2012-05-21
It's option B, I mean... Fully illegal. This is why I like it so much. The Administrators must not know, but I expect to be able to "defeat" windo$ in this as well... It's the only battle remaining against the "dark side" and thus I will be able to not to use it any more... As I said, it is slow and produces many crashes.

---

### Post by Cheesemill on 2012-05-21
> **Kalma said:**
> It's option B, I mean... Fully illegal. This is why I like it so much. The Administrators must not know, but I expect to be able to "defeat" windo$ in this as well... It's the only battle remaining against the "dark side" and thus I will be able to not to use it any more... As I said, it is slow and produces many crashes.

Is it really worth risking your job over?

I've worked in places where staff have been let go for repeatedly breaking the IT policies that I put in place.

---

### Post by Dave_in_MD on 2012-05-21
> **Kalma said:**
> It's option B, I mean... Fully illegal. This is why I like it so much. The Administrators must not know, but I expect to be able to "defeat" windo$ in this as well... It's the only battle remaining against the "dark side" and thus I will be able to not to use it any more... As I said, it is slow and produces many crashes.

I am a Win network admin, you will not be able to join, nor unjoin the domain without a domain admin password.  I was reading this as if I get my home network, win and Ubuntu, running correctly, next will be trying to join a Ubuntu machine to to the domain.  I showed a VM running on my machine at work to the director of education and he had his interest peaked in some of the software packages.

---

### Post by Kalma on 2012-05-22
Well, I don't think it's going to be so drammatic...

I'm aware Administrators are very reluctant to allow using things they don't control (or, simply, they don't know) but, on the other hand, I'm not trying to do anything criminal, like cracking, sniffing or hacking anything, just using my laptop in a faster, safer way. My intention is to follow every single corporate rule, but just using a different OS...

If it is impossible, do you think it is feasible to have Win on Virtualbox, then using this Win to access the corporate folders and Ubuntu for all the other local tasks?

---

### Post by Cheesemill on 2012-05-22
> **Kalma said:**
> If it is impossible, do you think it is feasible to have Win on Virtualbox, then using this Win to access the corporate folders and Ubuntu for all the other local tasks?
You still need a Windows Domain Administrator password to attach a machine to the domain, whether it's running Ubuntu or Windows.

---

### Post by Kalma on 2012-05-22
Okay. I will remain on :( Winddo$ :( or...

I could use Ophcrack to get the Administrator password!!!

It's a joke!!! it's a joke!!! :P

Thank you anyway.

---

### Post by Cheesemill on 2012-05-22
> **Kalma said:**
> Okay. I will remain on :( Winddo$ :( or...

I could use Ophcrack to get the Administrator password!!!

It's a joke!!! it's a joke!!! :P

Thank you anyway.

Even if it wasn't a joke, ophcrack would only give you the local machine admin password not the domain admin password :)

---

### Post by Dave_in_MD on 2012-05-22
> **Kalma said:**
> 
If it is impossible, do you think it is feasible to have Win on Virtualbox, then using this Win to access the corporate folders and Ubuntu for all the other local tasks?

I don't know about joining an Ubuntu machine to the domain, yet, but you can indeed join a virtual win 7 to the domain, (again you need a domain administrator password), I use one as a honeypot, connected to the network but not joined to the domain,  and one as a test bed that is joined to the domain.
If you worked with me, I would be working with you to see where we could take this. I can see benefits for the students.

---

### Post by Mark Phelps on 2012-05-23
> **Kalma said:**
>  ... on the other hand, I'm not trying to do anything criminal, like cracking, sniffing or hacking anything, just using my laptop in a faster, safer way. My intention is to follow every single corporate rule, but just using a different OS...


By trying to install something NOT provided by your IT department, you are likely NOT following "every single corporate rule".

Your intentions don't matter -- your actions DO.

In some companies (like several I know), even trying to do this is enough to get you fired.

Your job ... your decision.

---

### Post by Kalma on 2012-06-13
Well, I'm Affraid every single Administrator in this forum will enter this thread to fire me immediately :)

Again, I don't think it's going to be so drammatic... In fact, in my company all corporate services are on-line. I usually access from my home PC when working from home. Furthermore, they are considering to let every PC to be maintained by its user, by its own, so they will not have to worry about the local apps maintenance any more. They will save a lot of money. We use web apps and Citrix to access all corporate apps. Many times, I access from my own home PC when I want to work at home.

They have started a Pilot with a small number of users, but their idea is to extend that model to all users. In that scheme, my choice (I expect) will be Ubuntu. The only reason to connect to the Domain is to work faster (not entirely relying on the web connection when I am at the office).

I would not want to polemize, but I would like to say: "Open your minds".

Once said this, I finally got to access the Corporate Proxy from all apps (including synaptic, apt-get and, of course, the web browser). I did it by using cntlm. It is quite easy:
- Install cntlm
- Run cntlm -I -M 
- copy the resulting Auth and Passxxxx entries into the cntlm.conf file. Be sure to comment all other Auth and Passxxxx entires in the file and save it.
- Modify /etc/environment, /etc/apt/apt.conf, /etc/apt/apt.conf.d/02proxy and /.bashrc files, setting http:127.0.0.1:3128 (or the listening port you set in the cntlm.conf file) as proxy.
- Restart cntlm

It should work fine.

I have been very busy, but now I will get some little time to experiment with likewise-open to access the Domain folders.

Regarding Virtualbox, it is my last option. I have successfully installed a Windows XP on Virtualbox, and it works fine, but it is not exactly whar I am looking for.

---


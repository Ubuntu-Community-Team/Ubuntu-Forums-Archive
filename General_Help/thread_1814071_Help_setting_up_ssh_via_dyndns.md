---
title: "Help setting up ssh via dyndns"
date: 2011-07-28
forum: General Help
---

### Post by imhotep531 on 2011-07-28
I'm running Ubuntu Server 10.04.2 LTS.  I'm in the very beginning stages of setting this up and have little experience.  It's my first linux project.  For starters I'd like to be able to remote into the server from anywhere using putty.

Right now my server connects to the internet via an ASUS WL-520GU router which is connected to my cable modem.

So far I have setup my dyndns account and I have installed ssh using this tutorial:

[http://mexpolk.wordpress.com/2008/01/29/ubuntu-gutsy-dyndns-client-setup/](http://mexpolk.wordpress.com/2008/01/29/ubuntu-gutsy-dyndns-client-setup/)

Everything in that tutorial worked perfectly.  I can successfully remote in from a Windows 7 laptop using PuTTy and get the following output:

Using username "imhotep531".
imhotep531@datahaus's password:
Linux datahaus 2.6.32-28-server #55-Ubuntu SMP Mon Jan 10 23:57:16 UTC 2011 x86_64 GNU/Linux
Ubuntu 10.04.2 LTS

Welcome to the Ubuntu Server!
 * Documentation:  [http://www.ubuntu.com/server/doc](http://www.ubuntu.com/server/doc)

  System information as of Thu Jul 28 20:54:40 EDT 2011

  System load:  0.0               Temperature:         40 C
  Usage of /:   1.5% of 70.33GB   Processes:           107
  Memory usage: 3%                Users logged in:     1
  Swap usage:   0%                IP address for eth0: 192.168.1.6

  Graph this data and manage this system at [https://landscape.canonical.com/](https://landscape.canonical.com/)

Last login: Thu Jul 28 20:27:03 2011

Now if I want to remote into the server from anywhere on the web, what is the next step?  To reiterate I already have a Dyn Standard DNS account and the ddclient setup and configured. I'm not clear on what the next step is.  Do I need to configure my router?

Thanks for your help.

---

### Post by stands2reason on 2011-07-28
> 
I'm not clear on what the next step is. Do I need to configure my router?


I have DynDNS and regularly use SSH to a home computer. As long as the name resolution is working all you need to do is port forward (in your router) the default SSH port to your computer's internal, static IP address and then you can just connect as you normally would. 

You need to make sure you have good passwords, since after opening the port you will be opening up your computer to the world.

---

### Post by imhotep531 on 2011-07-28
Ok I have setup port forwarding on the ASUS WL-520GU router.  I am forwarding port 22 to the server's internal IP.

My domain is [www.curtsplace.com](www.curtsplace.com) (registered via Dotster and used in my dyndns account).  So should I be able to enter 'curtsplace.com' into the putty connection dialog and specify port 22 and that's it?  I tried this and the connection times out.  Would it instead be [email]user@curtsplace.com[/email] on port 22?

Please set me on the right track.  Thanks for your help.

---

### Post by pqwoerituytrueiwoq on 2011-07-28
1. set stat ip address on computer
2. enable port forwarding (post 22 nad the address you just set your computer to) 
3. make sure your dyndns ip address is up to date (i let my router do this)
4. you can't login using your dyndns with out using someone else's Internet (i cant use my lapotp to ssh into my desktop going though the Internet when both computers are accessing the Internet under the same address)

---

### Post by imhotep531 on 2011-07-29
1. set stat ip address on computer - [COLOR=Red]DONE[/COLOR]

2. enable port forwarding (post 22 nad the address you just set your computer to)  - [COLOR=Red]DONE[/COLOR]

3. make sure your dyndns ip address is up to date (i let my router do this) - [COLOR=Red]well I configured ddclient on the server itself, not on my router.  I guess I should check somehow that ddclient is updating properly.  How can I do this?[/COLOR]

4. you can't login using your dyndns with out using someone else's Internet (i cant use my lapotp to ssh into my desktop going though the Internet when both computers are accessing the Internet under the same address) - [COLOR=Red]thanks I should have known that.  I'm leaving the server running and I'll try to remote in from work.[/COLOR]

---

### Post by imhotep531 on 2011-07-29
Ok at first I was able to remote into my server from an external computer with putty only if I used my router's IP (which is dynamic via my ISP).  I was not able to connect using the hostname.

Turns out my dyndns service was inactive and I didn't know it.  I didn't know I had to manually set the delegations in my Dotster account to match the required delegations of Dyndns.  This is now done and my Dyndns summarys hows the new delegations.

I'm a rookie with putty and feel certain I'm doing something stupid.  I can't figure out how to connect via putty using my hostname.  Again, I can access the server with the router's IP, but if I try to connect using my hostname of curtsplace.com the connection just times out.  What am I missing?

---

### Post by imhotep531 on 2011-07-29
Apparently I needed to wait a couple of hours for those changes to persist.  Now I can login with putty remotely.

Thanks for the help guys.

---

### Post by linfidel on 2011-08-06
FWIW, I set up a dyndns account using one of their domain names, and it works perfectly, no fuss, no wait.  It was so good, I registered for the premium service, only $15/year.  

For that, you get a lot more domain names to choose from, with more than one available at the same time, plus you can monitor the frequency of your IP changes online.

I have a web server running, for development, and I can connect to multiple sites using a subdomain.  You can have automatic subdomains for any chosen domain, so there's no external configuration to add a web site, just the local Apache setup.  And that can be done remotely via ssh.

They have domains like <yourname>.homelinux.com/net, or things like <yourname>.from-CA.com -- every state is available.  Then they have names like <yourname>.is-a-good-guy,or something similar.

I love it, as now I can do things like show clients a site in progress without uploading it, or check the html/css of a local site, etc.

---


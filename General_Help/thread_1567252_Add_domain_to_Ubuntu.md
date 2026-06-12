---
title: "Add domain to Ubuntu"
date: 2010-09-03
forum: General Help
---

### Post by Manifest on 2010-09-03
I have apache installed and I installed BIND(If thats right lol) but Its really complicated looking at tutorials
So basicly How do I add a domain to that looong complicated IP Address :)

---

### Post by Manifest on 2010-09-03
bUmP^
          |

---

### Post by Manifest on 2010-09-04
Anyone?:-s

---

### Post by Manifest on 2010-09-04
*bump*

---

### Post by JedMeister on 2010-09-04
What are you trying to do? The fact that you have apache installed suggests to me that you are trying to run a web server. Now you have installed BIND which provides local DNS, but I'm not really sure why you've done that?

I could be wrong but I'm guessing perhaps you're trying to get a domain name like example.com to point to your web server? If so thats not the way to do it. Give me a bit more info and I can hopefully head you in the right direction.

If on the other hand, you just want to use a name to access your web server from the LAN then you are on the right track. Although to be honest, unless you have a fairly large network, there are probably easier ways of doing it (without using BIND).

Regardless, no one will be able to help you without more info about what you are trying to achieve and a basic rundown of your current setup/network.

---

### Post by Manifest on 2010-09-04
> I could be wrong but I'm guessing perhaps you're trying to get a domain  name like example.com to point to your web server?.Yup

---

### Post by Manifest on 2010-09-04
Oh come on. I expected better support than this

---

### Post by DarthScape on 2010-09-04
> **Manifest said:**
> Oh come on. I expected better support than this

Calm down dood.

First, have you purchased a domain name? or are you just trying to get other computers on your private network to connect to this server via domain name?

---

### Post by Manifest on 2010-09-04
First,my Server is accessible publicly
So to put it simply I want to go on a computer somewhere else and type in [http://mydomain.com](http://mydomain.com) and it would go to my servers public ipaddress

---

### Post by JedMeister on 2010-09-05
> **Manifest said:**
> Oh come on. I expected better support than thisThat my friend is plain and simple **rude**! 99% of the people on here are volunteers who have real lives. They take time out from their partners/families/friends/etc to help people for no payment other than a little thanks and to know that they are doing good in the world. 

I know it can be frustrating waiting for help when you're not sure what to do next to acheive your aims, but just remember how much you've paid for Ubuntu! (Unless you've been rorted it cost exactly $0 - in fact if you ordered a CD it actually cost Ubuntu money to get you involved). If you want to whinge about support I suggest you buy a support contract from Canonical (or someone else). I think you'll find that they start around $700 for low level email support, or go to Windows and see how much support from MS you get for your ~$300. Bottom line - pay for it or pull your head in and be patient! 

Besides, if you'd provided enough info in your initial post your question would already be answered by now! Either I would've in my previous post or possibly someone even sooner!

OK now I've had my rant...> **Manifest said:**
> First,my Server is accessible publicly
So to put it simply I want to go on a computer somewhere else and type in [http://mydomain.com](http://mydomain.com) and it would go to my servers public ipaddressFirstly you may as well uninstall BIND as thats of zero use to you.

You will need to buy your domain name from somewhere and get them to add your server's IP to their nameservers. And that's it! That will all be straighforward as long as you have a static IP. 

If you aren't too worried about what domain you have and/or want a free one and/or don't have a static IP, then there are a number of service providers who can help you out there. Off the top of my head is [DynDNS]("http://www.dyndns.com") and [No-IP]("http://www.no-ip.com") but there's plenty of others.

Hope that's helpful and sorry for my rant (but it really bugs me when people expect something for nothing!)

---

### Post by dcstar on 2010-09-05
> **JedMeister said:**
> 
...........
Hope that's helpful and sorry for my rant (but it really bugs me when people expect something for nothing!)

Especially when the issue has little (or nothing, really) to do with Ubuntu.

Some people seem to expect others to do work for them for free that people in the real world have to pay good money for.

---

### Post by Manifest on 2010-09-05
> **JedMeister said:**
> That my friend is plain and simple **rude**! 99% of the people on here are volunteers who have real lives. They take time out from their partners/families/friends/etc to help people for no payment other than a little thanks and to know that they are doing good in the world. 

I know it can be frustrating waiting for help when you're not sure what to do next to acheive your aims, but just remember how much you've paid for Ubuntu! (Unless you've been rorted it cost exactly $0 - in fact if you ordered a CD it actually cost Ubuntu money to get you involved). If you want to whinge about support I suggest you buy a support contract from Canonical (or someone else). I think you'll find that they start around $700 for low level email support, or go to Windows and see how much support from MS you get for your ~$300. Bottom line - pay for it or pull your head in and be patient! 

Besides, if you'd provided enough info in your initial post your question would already be answered by now! Either I would've in my previous post or possibly someone even sooner!

OK now I've had my rant...Firstly you may as well uninstall BIND as thats of zero use to you.

You will need to buy your domain name from somewhere and get them to add your server's IP to their nameservers. And that's it! That will all be straighforward as long as you have a static IP. 

If you aren't too worried about what domain you have and/or want a free one and/or don't have a static IP, then there are a number of service providers who can help you out there. Off the top of my head is [DynDNS]("http://www.dyndns.com") and [No-IP]("http://www.no-ip.com") but there's plenty of others.

Hope that's helpful and sorry for my rant (but it really bugs me when people expect something for nothing!)
Sorry, I respect that they do this as a hobby in their spare time.It's just that I've made about 3 other support topics and all 3 were answered within 5 minutes but this topic I've had to bump 3 times.
Anyway i have a free .co.cc domain  and when I add my servers ip to NS1 and press Enter
it says
 Please use only letters, numbers, dashes (-) or periods (.) followed by the appropriate.

Web extension such as .com, .net, .org. Do not enter spaces or other punctuation.
So what do you suggest? and once again im sorry

---

### Post by mendhak on 2010-09-05
Configure Apache, give it a VirtualHost.


# Listen for virtual host requests on all IP addresses
    NameVirtualHost *:80
    
    <VirtualHost *:80>
           DocumentRoot /path/to/files
      ServerName [www.example1.com](www.example1.com)
      
      </VirtualHost>


Then you'll want to add your IP address to your .CO.CC control panel.  I haven't used .co.cc but you probably want the DNS configuration section where it should allow you to enter an IP address.

---

### Post by Manifest on 2010-09-05
Sorry could you explain that clearer?

---

### Post by mendhak on 2010-09-05
Well, there's two parts to this.  The first is pointing your domain.com to your machine.  The second bit is getting your machine to understand and process that URL.  So the first bit is something you'll have to figure out in the .co.cc control panel, or use dyndns or some similar service.

The second bit is telling Apache that it should expect an incoming URL called mydomain.co.cc.  So the instructions to do that are [here](http://httpd.apache.org/docs/2.0/vhosts/examples.html).

---

### Post by JedMeister on 2010-09-06
> **mendhak said:**
> Well, there's two parts to this.  The first is pointing your domain.com to your machine.  The second bit is getting your machine to understand and process that URL.  So the first bit is something you'll have to figure out in the .co.cc control panel, or use dyndns or some similar service.Or see if .co.cc have a support forum or FAQ or something. I would imagine that something as fundamental as this should be documented somewhere. Google may even turn something up?

[update] I was feeling generous so I had a quick look for you: co.cc's FAQ can be found [here]("http://www.co.cc/faq/faq.php"), a quick browse suggests that many (if not all) of your questions should be answered there. If you struggle to understand what they are trying to tell you, please feel free to post back here, but it probably useful to also provide that feedback to them so they can improve their FAQs. Their Support ("Help") email contact is [email]hlp@co.cc[/email] or "Comments": [email]comments@co.cc[/email] (both found [here]("http://www.co.cc/qa_board/qa_board_list.php")). I also came across a YouTube vid that whilst not identical to your situation probably still contains some relevant info [here]("http://www.youtube.com/watch?v=EGw33qTPgAY") (I didn't actually watch it so I can't say for sure). FYI all this info was from the first 2 links from a a google search for "setting up website free co.cc".

---

### Post by Manifest on 2010-09-11
Yes! 
I got my .co.cc domain to connect to my server but how do i get my server to accept that domain(Please explain it simple):p

---

### Post by Manifest on 2010-09-11
> **Manifest said:**
> Yes! 
I got my .co.cc domain to connect to my server but how do i get my server to accept that domain(Please explain it simple):p
bUmP

---

### Post by JedMeister on 2010-09-11
In my experience if you can access your website externally using a IP address - which it seems you were able to do (going by your thread [here]("http://ubuntuforums.org/showthread.php?t=1547152")).

**And** you have your domain name pointing to that IP address, then just with default apache settings it should just work. In my experience if you only have one site, Apache will accept any domain. Although I have only used Hardy so perhaps things have changed with later versions and you need to set up virtual hosts for each domain (even if there's only one). What errors are you getting?

If you wish to setup virtual hosts then follow the instructions that you have been given already (directly and a link to read). Unfortunately they don't get anymore straight forward than that without doing it for you (you just need to add some lines to a config file). For the record here is [another link]("https://help.ubuntu.com/community/ApacheMySQLPHP#Virtual%20Hosts") to info for you.

You're so close I think... Are you sure you have a static IP? (Most residential plans have dynamic ones & that will cause issues with your current setup as I understand it).

Also it may be a bit late but you may wish to have a look at a project that I'm quite involved in: [Turnkey Linux (TKL)]("http://www.turnkeylinux.org/"). They are preconfigured appliances based on Ubuntu Server (current stable release based on Hardy/8.04 - new beta based on Lucid/10.04 expected some time within the next few months). Currently there are 40+ appliances such as LAMP stack (ie webserver using Linux, Apache, MySQL & php) and WordPress. They are free and ready to install to VM, bare metal or to the cloud. As well as their specific function they all have SFTP (secure FTP), SSH (secure shell) and Webmin (Web based Admin UI) preconfigured and ready to go. As I say it may be a little to late for you but a great option IMO.

---


---
title: "I want to know how to host my own website with 8.04 hardy desktop computer"
date: 2009-07-28
forum: General Help
---

### Post by jcm1107 on 2009-07-28
Hi, I have 8.04 hardy on my computer and I want to know how to host my own website from it. I have found a little about it but it was for different ubuntu version and in a forum that was not solved. I know everyone says its not the best idea but I feel I know enough that I could do it and I want to learn how. I already found a site that has a lot of html coding and I learned how to use that pretty good in about half an hour. I know it good enough that if I want to put something on a page that I can figure out how to do it. So now I just need to know how to get a page on the internet! I am just doing this to try to learn on my own how it works so I want to do it for free for now. Thanks.

---

### Post by Hobgoblin on 2009-07-28
Install apache via synaptic package manager.

Put your document in /var/www (or a subfolder of /var/www)

Give it read all access.

go to [http://localhost/](http://localhost/)*whatever folder and file you created*

---

### Post by jcm1107 on 2009-07-28
> **Hobgoblin said:**
> Install apache via synaptic package manager.

Put your document in /var/www (or a subfolder of /var/www)

Give it read all access.

go to [http://localhost/](http://localhost/)*whatever folder and file you created*

Ok, I installed that and now have a www folder and it already had a it works sample page in it so now if I put my page in there I need to know how to make it on the web? I would like to try to see it just with my other computer on my lan until I get my page made. I don't have a domain name or anything I would buy one after I learn some more about how to do this.Thanks:P

---

### Post by credobyte on 2009-07-28
It's already on the web and can be accessed trough your IP ( if you have a firewall, don't forget to open ports ). For local testing, I would simply block 80 port - it'll become unavailable for the public ( only from localhost ).

---

### Post by jcm1107 on 2009-07-28
> **credobyte said:**
> It's already on the web and can be accessed trough your IP ( if you have a firewall, don't forget to open ports ). For local testing, I would simply block 80 port - it'll become unavailable for the public ( only from localhost ).

Thanks, could you tell me a little more about how to find my page? like how to find my local ip? I know the ip adress of my computer and router but it is the standard 192...... number I know you probably mean the ip of the cable modem I could find it but I would have to look around a bit. And could you tell me a little about geting a domain name? I think you have to register one, or buy one? if I did then I could host my page at that?

---

### Post by QIII on 2009-07-28
Be aware that when you open a port,  you open your door.

Play with it without exposing yourself first.

Then read up thoroughly on security before opening a port exposed to the web.

Also, your ISP may have restrictions on whether you can host from your home computer.  You need to research that as well.

---

### Post by jcm1107 on 2009-07-28
I was wondering about security too! but it is hard to read up on the internet because everything just says you should not do it yourself. I just want to learn about it and then I want to make a site.

---

### Post by credobyte on 2009-07-28
> **QIII said:**
> Be aware that when you open a port,  you open your door.

Play with it without exposing yourself first.

Then read up thoroughly on security before opening a port exposed to the web.

Also, your ISP may have restrictions on whether you can host from your home computer.  You need to research that as well.

Come on, you can't really do anything with a port witch is already in use ( in this case, 80 port will communicate with Apache ).

---

### Post by Hydrid on 2009-07-28
jcm1107 said "I already found a site that has a lot of html coding and I learned how to use that pretty good in about half an hour."

I am very thrilled if you learnd html in half an hour REALY I AM ASTONISHED! If its like you say you are a wonderboy/girl!

To our subject.Well you must install a web page maker program (dreamweaver,expression studio,they run extremely well under crossover or wine)and there's information on using Wine (including HowTo-type stuff) here:
[http://www.winehq.org/](http://www.winehq.org/)

Secondly you must buy a name from a domain name provider (example: dnhost and million others like it).When you do that

You install and configure an apache server to your linux/ubuntu/ pc/machine!

You upload your site there and everything is ready to go.If you have done everything right when you will put your url to the browser it will show you your site.( dont care about security cause i think you dont have goverment secrets,so just try to make it RUN FIRST !!!

---

### Post by jcm1107 on 2009-07-28
OK, My page shows up on the other computer on my lan when my ip adress is typed in I don't think it could show up outside of my lan though because my ip adress is probably pretty common 192.168.1.103 so how would I be able to see it outside of my lan? I have cable internet so maybe you would type the ip adress of the modem followed by mine? Sorry I just want to see how all this works! it is so cool! or I am a computer geek one of the two.

---

### Post by credobyte on 2009-07-28
If you are behind a router, you need to set up port forwarding ( Google for it .. it's damn easy ) :)

---

### Post by jcm1107 on 2009-07-28
> **credobyte said:**
> If you are behind a router, you need to set up port forwarding ( Google for it .. it's damn easy ) :)

I know which port is open so what do I do then?

---

### Post by Sub101 on 2009-07-28
Your router should have a function called port forwarding, or virtual servers. You need to set this up to allow port 80 traffic, which is html, to be directed towards the local ip of the box where you are hosting your website.

Otherwise you will just be greeted by either your router config page, or more generally a server not found error when accessing the site externally.

---

### Post by credobyte on 2009-07-28
> **jcm1107 said:**
> I know which port is open so what do I do then?

Google for it by yourself or tell us what type ( model ) of router you have there :p

---

### Post by QIII on 2009-07-28
> **credobyte said:**
> Come on, you can't really do anything with a port witch is already in use ( in this case, 80 port will communicate with Apache ).

C'mon.  It's "which".

If he exposes an open port to the web, he has a door open.  He needs to take appropriate security measures.

---

### Post by credobyte on 2009-07-28
> **QIII said:**
> C'mon.  It's "which".

If he exposes an open port to the web, he has a door open.  He needs to take appropriate security measures.

Talking about the security with someone who's a complete newbie ( I hope he'll forgive me this :p ) is nonsense.
If you open Firefox, you open a port ( theoretically ) - should I consider it as a security measure ?

---

### Post by jcm1107 on 2009-07-28
> **credobyte said:**
> Google for it by yourself or tell us what type ( model ) of router you have there :p

I have a linksys wrt160n wireless router I can use my computer with it wirelessly or with a cable. I usually use wireless it seems faster don't know why. For some reason I can not log in to the setup screen I tryed. It used to be I type 192.168.1.1 in my browser and a prompt came up for my password and it comes up google this link appears to be broken! I don't know why it would have changed. I am the only one with access to setup and I didn't change it unless someone hacked it.

---

### Post by credobyte on 2009-07-28
Restarting might help to solve your router address problem. Anyway, check this: [http://www.pcwintech.com/node/226](http://www.pcwintech.com/node/226) ! Instead of adding port range, add a fixed port ( not sure if it's possible on Linksys - haven't used it ) and you should be fine :)

---

### Post by QIII on 2009-07-28
> **credobyte said:**
> Talking about the security with someone who's a complete newbie ( I hope he'll forgive me this :p ) is nonsense.
If you open Firefox, you open a port ( theoretically ) - should I consider it as a security measure ?

As a general measure, yes.  You should consider security even when doing that.  Don't you use a firewalled router?  The risk is certainly smaller for the surfer.

But a web page exposed to the web is certainly more of a glittery target than someone surfing, which does not flash quite so brightly and attract predatory fish.

If the guy is going to expose himself to the web, security should be one of his first considerations.  Will he expose the personal data of millions of clients?  No.  Will he risk losing millions of dollars? No.  Will he risk some Pimply Faced Youth peering into his private secrets.  Yes.  But probably not a likely scenario.

I read your profile.  I hope that security is one of the first things on your mind when you design web pages for your clients.

It certainly is of great concern to me when data on hundreds of thousands of people and billions of dollars of our clients' money might be breached.

It's a good habit to start off with.

---

### Post by jcm1107 on 2009-07-28
yes security is one of my concerns and I would like to learn more about that. But I am just doing this for myself I have no clients and don't plan on it yet. I am just doing this as a leaning experience. I got into my router now I had to reset it (don't know why it changed but it did) it is firewalled. I am just trying to simply learn about how all this works! everyone keeps saying that security is such a big concern so what exactly is someone going to be able to do if they can see a page that I made? Change it? big deal! it is going to be nothing important or special untill I can learn some more anyway!

---

### Post by jcm1107 on 2009-07-29
> **credobyte said:**
> Restarting might help to solve your router address problem. Anyway, check this: [http://www.pcwintech.com/node/226](http://www.pcwintech.com/node/226) ! Instead of adding port range, add a fixed port ( not sure if it's possible on Linksys - haven't used it ) and you should be fine :)

I don't see how I can add a fixed port, like port 80. But that link does have a pic of my router and is talking about forwarding but it means like for hosting a game to people that you know the ip address of I think. I have herd of installing LAMP what exactly is this? would it do what I want? and if so how would I do it?

---

### Post by credobyte on 2009-07-29
Game, web server, video streaming, etc. - everything requires you to open some ports. The link I gave you was just an example of how to set it all up.
LAMP for newbies: [http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies)

---

### Post by t4thfavor on 2009-07-29
Why go LAMP off the bat, apache2 is all you need to get started, and once you get the hang of configuring this kind of stuff,  you can add the LMP parts later. If were going for security, disabling the web servers scripting engine is usually the first place I start (once burned, twice shy).

---

### Post by jcm1107 on 2009-07-29
> **t4thfavor said:**
> Why go LAMP off the bat, apache2 is all you need to get started, and once you get the hang of configuring this kind of stuff,  you can add the LMP parts later. If were going for security, disabling the web servers scripting engine is usually the first place I start (once burned, twice shy).

well then could you tell me how to get my page to show on the net with just apache? please!!!I know my ip adress to my cable modem and also the adress to my computer on my lan and to my router so which do I need to tell someone to acess my page and what do I have to enable for them to see it? and also what about security, just what exactly could someone do if I host a page? I have nothing important to loose, if I did I have everything backed up and just reinstall no prob!!

---

### Post by jcm1107 on 2009-07-29
I forgot to say I can see my page with the other computer on my lan but my stepmom tried my ip adress and didn't see it.

---

### Post by jcm1107 on 2009-07-29
> **credobyte said:**
> Game, web server, video streaming, etc. - everything requires you to open some ports. The link I gave you was just an example of how to set it all up.
LAMP for newbies: [http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies)

I already found it and how to install it but nothing really says much aobut it, like what it does or how to use it. If you could just tell me if it does what I am wanting to do or not thats what I need to know.

---

### Post by credobyte on 2009-07-29
> **jcm1107 said:**
> I already found it and how to install it but nothing really says much aobut it, like what it does or how to use it. If you could just tell me if it does what I am wanting to do or not thats what I need to know.
 
LAMP is a "complete" web server - Apache, PHP, MySQL ( not sure about phpMyAdmin and mail server ), so .. yeah, "theoretically" you are looking for a LAMP setup. Indeed, as I already said, LAMP is not an application by itself, so - apache and php would be enough for a while ( once you get the basics, you'll have more understanding on what/how works ).

---

### Post by jcm1107 on 2009-07-29
> **credobyte said:**
> LAMP is a "complete" web server - Apache, PHP, MySQL ( not sure about phpMyAdmin and mail server ), so .. yeah, "theoretically" you are looking for a LAMP setup. Indeed, as I already said, LAMP is not an application by itself, so - apache and php would be enough for a while ( once you get the basics, you'll have more understanding on what/how works ).

Thanks that is what I was trying to find out!! I thought all of it is kind of what I wanted, but I am just going to install the php now until I get the hang of this. So what about my other questions? does anyone know?

---

### Post by Hobgoblin on 2009-07-29
> **Hydrid said:**
> 
To our subject.Well you must install a web page maker program 
Why?  I manage well enough with a text editor.

> Secondly you must buy a name from a domain name provider (example: dnhost and million others like it).

Why?  I use dyndns for mine.

---

### Post by Hobgoblin on 2009-07-29
> **jcm1107 said:**
> I forgot to say I can see my page with the other computer on my lan but my stepmom tried my ip adress and didn't see it.

Because you need to forward port 80 on your router to your local machine.  See [http://portforward.com](http://portforward.com) for instructions.

Your stepmom then connects you your external IP (this is the one which [http://www.whatsmyip.org/](http://www.whatsmyip.org/) will give you).

As for security, if you just have static pages with no input then there is little or no risk.  Once you start accepting input, especially if you are using a database such as mysql with your web pages, then you are opening up the possibility of a security risk.

---

### Post by jcm1107 on 2009-07-29
> **Hobgoblin said:**
> Because you need to forward port 80 on your router to your local machine.  See [http://portforward.com](http://portforward.com) for instructions.

Your stepmom then connects you your external IP (this is the one which [http://www.whatsmyip.org/](http://www.whatsmyip.org/) will give you).

As for security, if you just have static pages with no input then there is little or no risk.  Once you start accepting input, especially if you are using a database such as mysql with your web pages, then you are opening up the possibility of a security risk.

This is some awesome info!!! it is exactly along the lines of what I needed. I have already been to the whatsmyip.org site and know my every ip I could possibly need though I just need to know how I forward the port on my router then I guess. Thank you so much. I will read some of the portforward.com site tomorrow I am going to bed, but thanks so much!:P

---


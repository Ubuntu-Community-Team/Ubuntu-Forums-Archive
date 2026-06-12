---
title: "help on webserver setup"
date: 2012-08-30
forum: General Help
---

### Post by imnewbiehere on 2012-08-30
hi,

i'm a newbie at web admin and my really need your help guys on web server setup and installation.  you see my boss just assigned mo do these task and don't have that much idea.. i do have some basic knowledge on linux installation etc.., but there is this problem that i cant solve.

This is the problem:

We have an old website which is managed on our office server using the public IP provided to us by the ISP.  The old administrator just vanished and i was tasked to retrieve all the data on the website.  The problem is, there is no password.  So what i wanted to do is take down the site temporarily and setup an  "under maintenance" site.  The problem is, everytime i change the PC/server for the temporary site, the website's domain name is only accessible only for 1 day.  After that you can't access the website using its domain name but only by its IP address.  So for example after i change the PC the website "example.org" is accessible through its domain name, after the next day, you could only access the site through its IP address.

I'm using ubuntu for the temporary server and the old server is run on fedora.

My initial suspect is i need DNS setup.  I used nmap and detected the old server has DNS.   I already have setup bind9 but still it doesnt work.

does a webserver need a DNS server installed?(i mean for private servers)  is this required?


thank you very much for your help..

---

### Post by lordievader on 2012-08-30
I think installing a local DNS server won't help in this situation.

A little background on DNS, let's say you have a server with the domain "example.com" and a computer at home. The home pc is configured with the dns of the isp. When you go to "example.com", what happens is the following:

[LIST=1]
[*]The home pc asks the isp DNS where the .com root DNS server is. As reply it gets an IP.
[*]The home pc asks the .com DNS where example.com is. As a reply it gets the IP of the server that hosts "example.com"
[/LIST]
From what I gather you now have two servers, one with the "real" site and one with a maintenance site, correct? And the problem is changing the DNS record to the maintenance host?

---

### Post by greenpeace on 2012-08-30
> **imnewbiehere said:**
> My initial suspect is i need DNS setup.  I used nmap and detected the old server has DNS.   I already have setup bind9 but still it doesnt work.

does a webserver need a DNS server installed?(i mean for private servers)  is this required?

Hi, 

You're on the wrong track with DNS.  It sounds much more like you have a dynamic IP from your ISP, and that there is some software on that older server that's updating your domain's IP address with the IP address as it changes.

Check with your domain name registrar to see how you are keeping your IP address updated.  Normally there is a script running on the server to do this.  You will need to replicate that functionality on the new server... normally the domain hosting company's pages will have more advice on how exactly to do that.

Good luck!

---

### Post by jim_deadlock on 2012-08-30
> **imnewbiehere said:**
> everytime i change the PC/server for the temporary site

We need more details on exactly what you are doing to "change the PC" because that is what is breaking your DNS.

---

### Post by imnewbiehere on 2012-08-31
> **lordievader said:**
> I think installing a local DNS server won't help in this situation.

A little background on DNS, let's say you have a server with the domain "example.com" and a computer at home. The home pc is configured with the dns of the isp. When you go to "example.com", what happens is the following:

[LIST=1]
[*]The home pc asks the isp DNS where the .com root DNS server is. As reply it gets an IP.
[*]The home pc asks the .com DNS where example.com is. As a reply it gets the IP of the server that hosts "example.com"
[/LIST]
From what I gather you now have two servers, one with the "real" site and one with a maintenance site, correct? And the problem is changing the DNS record to the maintenance host?

yup.. i want to take down the old/real site to setup a maintenance site/server.  is there any probable configuration?  i tried removing the DNS, and still the issue is the same.

---

### Post by imnewbiehere on 2012-08-31
> **greenpeace said:**
> Hi, 

You're on the wrong track with DNS.  It sounds much more like you have a dynamic IP from your ISP, and that there is some software on that older server that's updating your domain's IP address with the IP address as it changes.

Check with your domain name registrar to see how you are keeping your IP address updated.  Normally there is a script running on the server to do this.  You will need to replicate that functionality on the new server... normally the domain hosting company's pages will have more advice on how exactly to do that.

Good luck!

the website uses public ip provided by the ISP. thanks for the reply.

---

### Post by lisati on 2012-08-31
> **imnewbiehere said:**
> the website uses public ip provided by the ISP. thanks for the reply.

It's possible that your ISP has given you a [dynamic IP]("http://whatismyipaddress.com/dynamic-static") which is changing from time to time, confounding your efforts to get things pointing to the right place.

---

### Post by imnewbiehere on 2012-08-31
> **jim_deadlock said:**
> We need more details on exactly what you are doing to "change the PC" because that is what is breaking your DNS.

i replaced the old server with the new server.

---

### Post by greenpeace on 2012-08-31
> **imnewbiehere said:**
> the website uses public ip provided by the ISP. thanks for the reply.

Ok, but is it [**static** or **dynamic**]("http://whatismyipaddress.com/dynamic-static")?  that is what you need to find out from your ISP.  :)

---

### Post by imnewbiehere on 2012-08-31
> **greenpeace said:**
> Ok, but is it [**static** or **dynamic**]("http://whatismyipaddress.com/dynamic-static")?  that is what you need to find out from your ISP.  :)

its static

---

### Post by greenpeace on 2012-08-31
> **imnewbiehere said:**
> its static

OK, and when you said:  > i replaced the old server with the new server.

How exactly are you replacing the server? can you detail the steps you take?

---

### Post by imnewbiehere on 2012-08-31
> **greenpeace said:**
> OK, and when you said:  

How exactly are you replacing the server? can you detail the steps you take?

I'm replacing the physical server.  I setup a new physical server and physical replace the old server.

---

### Post by imnewbiehere on 2012-09-01
hmmmmm.. my guess is non if you has not encountered this kind of issue before.. thanks anyways guys.. if any of you seem to encounter this in the future, a help would be greatly appreciated.  btw,  anybody of you dont understand the problem?

---

### Post by Tobeus on 2012-09-01
I would look at the domain registrar and see if it is pointing to a name server on the old server's box.  If it is, you could set it to use the registrar's name server and just use a couple of A Name records to point to the specific IP of your server.

This is only relevant if the registrar is pointing the name servers elsewhere though.  Don't forget to change the passwords on the registrar if the old admin has left either.  No need to have him/her gum up the website host name completely by transferring it to another registrar or something else like that.

---

### Post by imnewbiehere on 2012-09-03
> **Tobeus said:**
> I would look at the domain registrar and see if it is pointing to a name server on the old server's box.  If it is, you could set it to use the registrar's name server and just use a couple of A Name records to point to the specific IP of your server.

This is only relevant if the registrar is pointing the name servers elsewhere though.  Don't forget to change the passwords on the registrar if the old admin has left either.  No need to have him/her gum up the website host name completely by transferring it to another registrar or something else like that.

I think the DNS is installed on the old webserver PC because i saw it when i tried nmap.  But, if you ping the website it shows the static ip address of the website provided.   will try your option.. thanks tobs.

---


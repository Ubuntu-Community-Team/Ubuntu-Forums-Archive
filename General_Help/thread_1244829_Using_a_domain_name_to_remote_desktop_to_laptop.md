---
title: "Using a domain name to remote desktop to laptop"
date: 2009-08-19
forum: General Help
---

### Post by chaotixmonjuish on 2009-08-19
Suppose I own a domain name and I wanted to set it up such that I just typed in [www.domain.net](www.domain.net) and I ended up being able to remote desktop or just generally access a directory on my laptop.  How do I go about doing this?

---

### Post by SoftwareExplorer on 2009-08-20
What program or command are you using? It should be pretty easy, I use a domain name for ssh and VNC all the time.

---

### Post by SoftwareExplorer on 2009-08-20
By the way, welcome to ubuntu forums. :)

---

### Post by chaotixmonjuish on 2009-08-22
Thanks for the welcome.

Well I'm not sure what you mean about program but basically I own this domain.  I've had it for a long time because of a project I did for a college class.  I didn't know I have been autorenewing it for some time.  Anyway, basically I was wondering if I could tie that domain name, or any, like myarbitrarydomainname.com to my laptop so when I am about I can just connect to a directory by typing that into a browser.

---

### Post by fragos on 2009-08-23
Truth is, this probably more complicated than you may want to get. The device you want to connect to will need to be running perhaps a web server like apache, that server's IP will need to be known by a DNS server and that DNS server must be configured into the DNS of your domain registration company. One problem you have to overcome is the fact that your ISP gives you a different IP every time you connect. You might look into a dynamic DNS solution on the web. There's a lot more to this than meets the eye.

---

### Post by chaotixmonjuish on 2009-08-25
Do you mind pointing me in the direction of how to set this up?  I am willing to experiment...I'm just completely unsure where to start.

---

### Post by fragos on 2009-08-25
You say you want access files on your laptop. Where will it be and what will you access those files from? What is your server device? What useful application are you trying to accomplish?

---

### Post by SoftwareExplorer on 2009-08-29
Well, I think it might be possible. I would start by going to System->Administration-Synaptic Package Manager. Search for dyndns and mark it to be installed. Apply the changes. Next you will want to find a dynamic dns provider and sign up. Go ahead and google it if you like. I use afraid.org and dyndns.org has been mentioned by others. Once you've made it that far, post and I'll help you set up the dyndns program.

---


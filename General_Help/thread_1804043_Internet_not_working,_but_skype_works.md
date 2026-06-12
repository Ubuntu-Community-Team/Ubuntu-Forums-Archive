---
title: "Internet not working, but skype works"
date: 2011-07-14
forum: General Help
---

### Post by ttkk on 2011-07-14
Hi everyone,
 
I am new to Ubuntu and have strange problem...
 
I have Ubuntu 11.04, and yesterday i make updates by update-manager.
 
When my buntu updates, web pages in firefox and chromium stopped working, but skype works normal.
 
I dont know how to solve this problem.
 
I can ping IP adresses in terminal, but cant ping names of the sites, for example google.com.
 
But if i typed for example ip adress of google in to firefox, it is not working. If i typed name "google.com" in to firefox, not working.
 
What the hell is it? DNS problem? Dont know...
 
The problem is with Acer Aspire One netbook. My internet connection is from ISP to router, from router wifi to my acer aspire one. Before updates everything was working fine. I have PC connected by wire from the router, with WIN XP and it is working fine. Only my netbook connected by wifi is not working...
 
Thanks for help!

---

### Post by Peter09 on 2011-07-14
can you provide the output of the command
 
```
route
```

---

### Post by no2498 on 2011-07-14
in your browser look in file make sure its not set to work off line

---

### Post by ttkk on 2011-07-14
> **Peter09 said:**
> can you provide the output of the command
 
```
route
```

address 192.168.0.0
mask 255.255.255.0

---

### Post by androssofer on 2011-07-14
my friend had a similar problem... can you access:

[https://encrypted.google.com/](https://encrypted.google.com/)

she had a problem with port 80 being blocked... so skype etc still worked but not normal addresses. tht address is ssl and should use port 443... if it works it might suggest port 80 is being blocked...

---

### Post by gandaran on 2011-07-14
try backing up your firefox user profile (/home/'user'/.mozilla) rename the .mozilla folder to something else then start firefox to see if it works or install some other browser.

---

### Post by ttkk on 2011-07-14
> **gandaran said:**
> try backing up your firefox user profile (/home/'user'/.mozilla) rename the .mozilla folder to something else then start firefox to see if it works or install some other browser.
I think it is not problem of Firefox, because I try it in Chromium, and it is the same problem...

---

### Post by ttkk on 2011-07-14
> **androssofer said:**
> my friend had a similar problem... can you access:

[https://encrypted.google.com/](https://encrypted.google.com/)

she had a problem with port 80 being blocked... so skype etc still worked but not normal addresses. tht address is ssl and should use port 443... if it works it might suggest port 80 is being blocked...

It doesnt work

---

### Post by ttkk on 2011-07-14
I do not understand it and i am getting desperate

---

### Post by enimeizoo on 2011-07-14
Did you try other browsers? (opera, arora, midori, rekonq)

> I can ping IP adresses in terminal, but cant ping names of the sites, for example google.com.Like you said, this looks like a dns problem. The network manager should let you change that. 8.8.8.8 and 8.8.4.4 are google's dns server, you could try them. Also, the host command could help you check if you have a dns issue.

> But if i typed for example ip adress of google in to firefox, it is not  working. If i typed name "google.com" in to firefox, not working.Even thought that doesn't confirm a dns issue, that doesn't tell you dns is fine neither. 

Did you try to backup and remove your .mozilla folder, just in case? It would'nt cost a lot.

And what do you mean by 'not working'. What is the error you get from the browser?

---

### Post by ttkk on 2011-07-14
> **enimeizoo said:**
> Did you try other browsers? (opera, arora, midori, rekonq)

Like you said, this looks like a dns problem. The network manager should let you change that. 8.8.8.8 and 8.8.4.4 are google's dns server, you could try them. Also, the host command could help you check if you have a dns issue.

Even thought that doesn't confirm a dns issue, that doesn't tell you dns is fine neither. 

Did you try to backup and remove your .mozilla folder, just in case? It would'nt cost a lot.

And what do you mean by 'not working'. What is the error you get from the browser?

Changing DNS in resolv.conf doesnt help, resolv.conf automaticly after restart rewrite it back to 192.168.0.1 :-(

Its not Firefox problem, Chromium doesnt work too.

What does it mean doesnt work? "Page can not be displayed..." "Server not found" ....

---

### Post by enimeizoo on 2011-07-14
> Changing DNS in resolv.conf doesnt help, resolv.conf automaticly after restart rewrite it back to 192.168.0.1 I guess the network manager rewrites it on restart, that is why you should use it's interface instead of editing the file. As for the exact steps, I don't know since I don't use the default manager.

Other reasons to try other browser is that they might give you more useful error logs. I already had a problem where all browser gave me a timeout error, but only one told me where it was stuck. (the browser was links, and the timeout was because ssl negotiation never ended).

Reverting a browser config to default is not irrelevant either since you might have made changes in both regarding the network options. And even if you didn't, last update might have. You never know, and it is cheap. 

You can try to get more info about where it fails with traceroute. Try it with both the ip and the hostname to see if that makes a difference.
You can check the result of 'host [www.google.com]("http://www.google.com")'.

Also, do you get the same error when entering the actual ip of the website in a browser than when you use the domain name?

---

### Post by Keypel on 2011-07-14
DNS Problem.

Before assuming Ubuntu is causing the DNS problem, I would connect a different laptop to the wireless connection and see if the same problem persists.

You can also try Logging into your router and seeing if you have a DNS forward setting. Use 8.8.8.8 if you can find a DNS setting.

---

### Post by enimeizoo on 2011-07-15
I'm just wondering, would a dns problem alone prevent a browser from displaying websites by ip?

---


---
title: "Cannot update a new install or access internet"
date: 2012-03-25
forum: General Help
---

### Post by mikejn1 on 2012-03-25
Hi,

I looked around before posting this for a similar thread before posting this. I also did some detective work and I am unable to figure out what's going on. What I have done so far is the basic install, letting Ubuntu pick the partition sizes and defaulted the options. Prior to the install, I ran Ubuntu off of the CD and played with it to see how it would work on my laptop, everything seemed to work fine. After the install I went to use Firefox and I get a message that it had crashed, tried again, same thing. I then went to the Software Center to maybe download a different browser and see if that would help. I am unable to download anything from there. I get a message saying to check my internet connection. I am able to command line ping the router from the laptop. I hope I have given you enough information to go on.

If this issue has already been asked and resolved by someone, I apologize. I have over looked it and if you would please direct me to the thread.

Thanks

---

### Post by BertN45 on 2012-03-25
Start the Terminal program and type: ping 8.8.8.8. 
8.8.8.8 is an Google internet address. If that fails yo have no connection with the internet.

If it fails we need to know which type of internet connection you use wired or wireless and which controller you use. If you type: lspci in the terminal and copy paste the result here we can find it out.

Probably based on that data we can find others that solved the same problem.

---

### Post by mikejn1 on 2012-03-25
> **BertN45 said:**
> Start the Terminal program and type: ping 8.8.8.8. 
8.8.8.8 is an Google internet address. If that fails yo have no connection with the internet.

If it fails we need to know which type of internet connection you use wired or wireless and which controller you use. If you type: lspci in the terminal and copy paste the result here we can find it out.

Probably based on that data we can find others that solved the same problem.



Correct me if I am wrong, but 8.8.8.8.8.8.8.8 is not a valid address format. However, I did open up a command window and was able to ping google.com with no loss. I an connected wirelessly. However I don't think that seems to be the issue..

---

### Post by Mark Phelps on 2012-03-26
You said > I am able to command line ping the router from the laptop.
So clearly, telling you to PING, especially providing you an invalid address, is wasting your time!

Never cease to be amazed at how folks don't even seem to READ the post before they reply ...

Since you CAN ping, and you clearly are getting DNS service (since you entered a site name, not IP address) you ARE getting access to the Internet.

Are you connecting to your ISP using a cable modem, or using DSL?

If a cable modem, try connecting your PC directly the cable modem -- and see if it makes a difference.

---

### Post by mikejn1 on 2012-03-26
Mark, 

I woke up this AM and I guess sleep did me some good. I opened a terminal window and executed a sudo apt-get update as well as a sudo-apt-get upgrade. After grinding on it for a while I got back to a command prompt.. So I tried the internet. That now seems to work fine.. So I managed to fix part of my problem.. However, I still cannot download anything from the Software Center. It continues to tell me " Failed to download package files check internet connection"  I am not a total noob.. However I have a LOT to learn. Just to be sure everything was settled.. I rebooted after the updates and upgrades..

Thanks for your help..

---

### Post by gsgleason on 2012-03-26
> **Mark Phelps said:**
> You said 
So clearly, telling you to PING, especially providing you an invalid address, is wasting your time!

Never cease to be amazed at how folks don't even seem to READ the post before they reply ...

Since you CAN ping, and you clearly are getting DNS service (since you entered a site name, not IP address) you ARE getting access to the Internet.

Are you connecting to your ISP using a cable modem, or using DSL?

If a cable modem, try connecting your PC directly the cable modem -- and see if it makes a difference.

8.8.8.8 is a perfectly valid IP address to ping.  What are you talking about?

---

### Post by mikejn1 on 2012-03-26
> **gsgleason said:**
> 8.8.8.8 is a perfectly valid IP address to ping.  What are you talking about?

I apologize for questioning that.. I see now that the 8.8.8.8 and the second set of 8's were separate.. One was the ID and the other was saying what the IP belonged to.. I admit I was tired and maybe the pain meds and allergy meds were not helping with my cognitive thinking 

Again I apologize..

---

### Post by gsgleason on 2012-03-26
> **mikejn1 said:**
> I apologize for questioning that.. I see now that the 8.8.8.8 and the second set of 8's were separate.. One was the ID and the other was saying what the IP belonged to.. I admit I was tired and maybe the pain meds and allergy meds were not helping with my cognitive thinking 

Again I apologize..

You need not apologize.  I was really asking Mark.

Anyway, I'm glad it's working now.

---

### Post by mikejn1 on 2012-03-26
> **gsgleason said:**
> You need not apologize.  I was really asking Mark.

Anyway, I'm glad it's working now.

Well the internet is working.. However I cant download anything from the software center.. says failed to download package files and to check my internet connection..

I know the connection works as I can now browse..

---

### Post by Mark Phelps on 2012-03-26
> **gsgleason said:**
> You need not apologize.  I was really asking Mark.

Sorry ... I had forgotten that 8.8.8.8 was Googles public IP address.  You have my apologies for stating the address was invalid.

However ... given that the OP had already mentioned being able to ping using a NAME from the command line, that shows not only that they have (1) internet connectivity (for PING to work), and (2) DNS service (for resolving the NAME to an IP address).

So, telling them to ping 8.8.8.8 was largely redundant.

---

### Post by BertN45 on 2012-03-26
Reading your post very carefully :D, taking into account that the internet is working and that also the apt-get upgrade goes wrong, I would suggest to try to re-configure the "apt" package. In the terminal

sudo -s
dpkg-reconfigure apt 

and afterwards if it did not help:  Try apt-get install, upgrade -f, and then try apt-get install, upgrade again. Repeat as needed. This usually resolves most dependency problems 

apt-get install -f 
apt-get upgrade -f 

This attempts to fix dependencies while doing one of the above. Note that apt-get install -f does not require a <package> argument.

---

### Post by gsgleason on 2012-03-26
> **Mark Phelps said:**
> Sorry ... I had forgotten that 8.8.8.8 was Googles public IP address.  You have my apologies for stating the address was invalid.

However ... given that the OP had already mentioned being able to ping using a NAME from the command line, that shows not only that they have (1) internet connectivity (for PING to work), and (2) DNS service (for resolving the NAME to an IP address).

So, telling them to ping 8.8.8.8 was largely redundant.

Please point out where in his original post he stated he can ping anything by name.

The third post, after your quote, he says this, but not before BertN45 suggested pinging a public server that is known to respond to pings.

> **Mark Phelps said:**
> 
Never cease to be amazed at how folks don't even seem to READ the post before they reply ...

Right back at you.

Anyway, mikejn1, you can ping a public host on the internet and have working DNS.  That's good.

Please show the full output of the following, which will attempt to download the package information from your configured mirrors.
```
sudo apt-get update
```

---


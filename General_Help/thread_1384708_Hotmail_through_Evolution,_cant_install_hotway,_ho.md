---
title: "Hotmail through Evolution, cant install hotway, hotsmtp"
date: 2010-01-18
forum: General Help
---

### Post by Tsquad on 2010-01-18
Hello, i have seen many guides and websites saying i need to install hotway and hotsmtp to use my hotmail account on evolution. When i type sudo apt-get install hotway hot smtp in terminal i get this output:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package hotway

and when i do they singly, sudo apt-get install hotsmtp returns

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package hotsmtp

and sudo apt-get install hotway returns

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package hotway

just like the first command. This is all in ubuntu 9.10

what exactly is my E: drive? i didnt think linux had drive letters?

---

### Post by tom4everitt on 2010-01-18
E: simply means Error: 

The reason for it not being able to find your package is probably that you haven't activated the necessary respositories. Look for Software Sources or similar in the preferences menu or synaptics menu. 

Also run 

apt-get update

before you try again.

---

### Post by Tsquad on 2010-01-18
> **tom4everitt said:**
> E: simply means Error: 

The reason for it not being able to find your package is probably that you haven't activated the necessary respositories. Look for Software Sources or similar in the preferences menu or synaptics menu. 

Also run 

apt-get update

before you try again.

apt-get update was the first thing i did before i started this. I am in the software sources, now what do i do from here? what repositories am i looking for?

---

### Post by Ahadiel on 2010-01-18
> **Tsquad said:**
> Hello, i have seen many guides and websites saying i need to install hotway and hotsmtp to use my hotmail account on evolution. When i type sudo apt-get install hotway hot smtp in terminal i get this output:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package hotway

and when i do they singly, sudo apt-get install hotsmtp returns

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package hotsmtp

and sudo apt-get install hotway returns

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package hotway

just like the first command. This is all in ubuntu 9.10

what exactly is my E: drive? i didnt think linux had drive letters?

Correct me if I'm wrong, but doesn't Hotmail support POP3 now?
[http://lifehacker.com/5169684/hotmail-finally-enables-pop3-worldwide](http://lifehacker.com/5169684/hotmail-finally-enables-pop3-worldwide)

---

### Post by Tsquad on 2010-01-18
> **Ahadiel said:**
> Correct me if I'm wrong, but doesn't Hotmail support POP3 now?
[http://lifehacker.com/5169684/hotmail-finally-enables-pop3-worldwide](http://lifehacker.com/5169684/hotmail-finally-enables-pop3-worldwide)

Yes it does but you have to down load a special package to get it working on outlook 2007 so i would assume something would have to be installed for linux that would do a similar thing.

But lets say it didnt need that. How would i set it up then. Just open evolution and enter my info? Or do i still have to install/configure some packages?

---

### Post by Ahadiel on 2010-01-18
> **Tsquad said:**
> Yes it does but you have to down load a special package to get it working on outlook 2007 so i would assume something would have to be installed for linux that would do a similar thing.

But lets say it didnt need that. How would i set it up then. Just open evolution and enter my info? Or do i still have to install/configure some packages?

You would just need to setup a POP3 account in Evolution and enter the appropriate server/user information.

---

### Post by Tsquad on 2010-01-18
Yea thats the problem. I was not able to find the incoming/outgoing server info when i was trying to set it up on outlook, whats what that add on i had to install did.

---

### Post by Ahadiel on 2010-01-18
> **Tsquad said:**
> Yea thats the problem. I was not able to find the incoming/outgoing server info when i was trying to set it up on outlook, whats what that add on i had to install did.

So the info provided by that link I posted earlier doesn't work?

---

### Post by Tsquad on 2010-01-18
> **Ahadiel said:**
> So the info provided by that link I posted earlier doesn't work?

ok, so i followed that and it seems to be working fine, it took a few trys to send/receive all my messages, it kept giving an error message saying "failed at xx message of xxx" but it eventually got them all. Now the only problem is that it has pulled my messages and is displaying them all as unopened, the receive dates are all correct but they act like i have not read them yet, which i have. Im guessing i put a setting wrong during set up? but what one?

---

### Post by Headfirst on 2010-01-19
Actually I believe the messages are going to show up as unread in evolution because evolution doesn't know that you have read them on the server it is polling all the messages from the mail server for the first time. The same thing happened when I set up evolution for my gmail account.

---

### Post by Tsquad on 2010-01-19
ok, yea i just resorted to opening near 200 messages one by one.

---

### Post by tom4everitt on 2010-01-19
That's the main reason you want to use something that supports IMAP :)

With POP all mails are just downloaded to your computer. If, for example, you get a new mail to your hotmail that mail will show up in evolution, but if you read it in evolution it will still be unread online. 

With IMAP basically everything is synced continuosly. Read something locally and it will be marked as read online. Move something to a folder locally, and the mail will be moved to the same folder online etc etc.

Gmail supports IMAP....

---

### Post by tom4everitt on 2010-01-19
Oh, and about which respositories to add its usually 'third party-something' and maybe something else. I'm not at an ubuntu computer right now, but I think you should be able to guess which are relevant, its just checkboxes and its not a catastrophy if you check one too much/too less.

---

### Post by Tsquad on 2010-01-19
Yea, iv been wanting to switch my main email to gmail for a while but i use my hotmail account for work and i just cant afford to change it this late into the game. To many people have my address.

Also, you were saying that imap is better. When using my hotmail account through outlook on my vista pc it does exactly what you described. I have not had the chance to mess with evolution enough yet to see if it will do the same or not. Also, from the link provided above, i am unable to send emails from this hotmail account through evo. I used the given outgoing server of smtp.live.com and it gives me an unable to send message after trying for a good 5 min. any ideas?

---


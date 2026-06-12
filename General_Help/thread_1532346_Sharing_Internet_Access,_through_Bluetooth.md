---
title: "Sharing Internet Access, through Bluetooth"
date: 2010-07-16
forum: General Help
---

### Post by madmax.santana on 2010-07-16
[B][SIZE=3]Well, pals, I am back with another one!
Has anyone ever shared a network connection with another computer using Ubuntu/Linux?[/SIZE][/B]

[COLOR=Sienna]**Well, I got this problem**[/COLOR]. I have got a connection to the Local Area Network of my organization, but the problem is, it is only one. I have a laptop and I requested a connection for it, too. But the request was denied and one of the techs at IT department tipped me that I could create my own PAN on which my computer (which is a client on the organization LAN) would act as a server for my PAN and my laptop can access Internet if you choose to share your Internet access over the PAN...

**[COLOR=Sienna]I have no idea about networking and stuff[/COLOR]**. And that fella was too busy to lemme know how to set up this whole thing. Besides, he is a Microsoft Expert, probably never touched Linux.

**[COLOR=Sienna]The situation gets worse[/COLOR]**... I don't wanna spend money on a Wi-Fi router. Instead, I could use the built-in Bluetooth module on my laptop with another Bluetooth Blip which is connected to my computer on USB port. I know people do that fairly commonly over Windows, since I have googled and found many posts regarding sharing an Internet connection through a Bluetooth connection with another computer... And I am confident that if it's possible on Windows, it is possible in Linux...

With that explained, I shall move on and tell you what[COLOR=Green] **I already have**.[/COLOR]

[COLOR=Blue]**A fairly old computer**[/COLOR]
Intel Pentium IV 3.0GHz
1GB RAM
80GB HDD
External Bluetooth Device (Not sure about Specs)
Linux Ubuntu Lucid Linx (10.04)
Connected to Internet through a proxy server
I want to make this one my server for PAN

[COLOR=Blue]**A relatively modern laptop**[/COLOR]
HP HDX-16t
Intel Core2Duo 2.2GHz
2GB RAM
320GB HDD
Built-In HP Integrated Bluetooth Module
Windows Vista 64-bit Home Edition
No connection to Internet
I want to make it able to connect to Internet through PAN

---

### Post by madmax.santana on 2010-07-16
Well, no Linux Whiz to help me???

---

### Post by Mark Phelps on 2010-07-17
Just because it's possible in MS Windows does NOT mean automatically that it is possible in Linux as well.  Which may be why no one has responded to your post.

Also, I would be REALLY CAREFUL about doing this at your organization.  

My company has strict rules regarding internet access for personal use.  Your "IT Tech" is not going to save your job if Management finds out you're running a PAN at work -- and fires you as a result.  

You would do better trying to find out if what you want to do is permissable, first -- and don't ask IT folks, they don't set the policies, Management does that.

---

### Post by madmax.santana on 2010-07-17
It is permissible. I am sure. Because if it weren't, that person would never give me such a hint. He is at a reasonably responsible post in IT Department and I discussed all possibilities with him. I was thinking about using a "split-socket" to convert my one-line connection into two... THAT would be illegal, he told me. 

But setting up a PAN is alright. I have discussed with other people who have more than one machines in their possession. They happen to share connections using their own Wi-Fi routers. One of them even offered me to join his Wi-Fi network but his router has a small range and I can only use his connection while sitting in my window holding the laptop in a very dangerous position. :)

Secondly, I think it is possible in Linux. I have surfed Internet.
(Well about my statement "*And I am confident that if it's possible on Windows, it is possible in Linux..*." Being a Linux fan I like to assert such things, and most of the times such suppositions do fall correct.)

I did come up with a few threads which mentioned connection sharing through Bluetooth. But they do not work, or maybe they are for old versions... One was for Debian, as I remember, and the conf file it directed to edit doesn't exist in Ubuntu.

Whatsoever, I was under the impression that it is not that unusual a proposal and many people should have already done it. I still think someone WILL be able to help.

---

### Post by madmax.santana on 2010-07-18
Man, everyone is trying so hard to prove me wrong!

---

### Post by Mark Phelps on 2010-07-18
> **madmax.santana said:**
> It is permissible. I am sure. Because if it weren't, that person would never give me such a hint. He is at a reasonably responsible post in IT Department and I discussed all possibilities with him. I was thinking about using a "split-socket" to convert my one-line connection into two... THAT would be illegal, he told me. 
OK ... just didn't know if you had checked, first.

>  I can only use his connection while sitting in my window holding the laptop in a very dangerous position. :)
Talk to your fried about getting a range extender for his wifi network.  Then, you might not have to hold your laptop "in a very dangerous position" to get a good signal.

> I did come up with a few threads which mentioned connection sharing through Bluetooth. But they do not work ...
Not trying to dampen your enthusiasm, but what you have discovered so far should clue you into the possibility that this might be one of those rare things (and I do know some, for a fact) that MS Windows can do and Linux can not.

---

### Post by madmax.santana on 2010-07-19
> Not trying to dampen your enthusiasm, but what you have discovered so far should clue you into the possibility that this might be one of those rare things (and I do know some, for a fact) that MS Windows can do and Linux can not.
Oh man! You have to pay for a little happiness in life, after all. :P
> OK ... just didn't know if you had checked, first.
I checked today, officially. And it is permitted.
> Talk to your fried about getting a range extender for his wifi network. Then, you might not have to hold your laptop "in a very dangerous position" to get a good signal.
Hahaha! Do you really think he will buy a range extender just for me? Won't he tell me to buy my own Wi-Fi router if I was in such a dire need? :P

Anyway, I know it is quite difficult and rare. And I am postponing it for now and trying to go without internet access on my laptop for now... But why not leave this thread open and maybe someone will care to commit necromancy... :)

---

### Post by madmax.santana on 2010-07-21
Can I bump this post every few days?
Well, just until I have enough money to buy a Wi-Fi-Router... :)

---

### Post by madmax.santana on 2010-07-28
Nooops! No advance!

---

### Post by ograndedienne on 2010-08-03
Hello,
i've a similar "problem".
I would like to connect my laptop with my HTC Touch Cruise smartphone via bluetooth PAN, so i could share the mobile connection.

As far as i looked, there's no nice interface program to establish a bluetooth PAN :( (this is a sad lack for a modern operative system like ubuntu should be)

I found this post: [http://blog.myfenris.net/?p=604](http://blog.myfenris.net/?p=604) in which the author set a laptop as PAN client; anyway the article use **pand**program that is part of the old version of the bluetooth stack.

i'm looking for a Bluez 4 PAN method...

Hope it helps.

---

### Post by ograndedienne on 2010-08-03
Two other interesting posts:

[http://ubuntuforums.org/showthread.php?t=1433981](http://ubuntuforums.org/showthread.php?t=1433981)
[http://kempproject.blogspot.com/2009/08/bnep-pan-connections-with-bluez-4x.html](http://kempproject.blogspot.com/2009/08/bnep-pan-connections-with-bluez-4x.html)

---


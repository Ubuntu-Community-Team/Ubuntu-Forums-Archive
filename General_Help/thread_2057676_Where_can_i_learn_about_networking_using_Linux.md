---
title: "Where can i learn about networking using Linux"
date: 2012-09-14
forum: General Help
---

### Post by Mohan1289 on 2012-09-14
Hi guys where can i learn about the networking using linux and what command's we have to use for the operations??? are there any tutorials?? 


Thank you

---

### Post by zero2xiii on 2012-09-14
Hay.

"Networking using linux" is a HUGE subject.

Can you please be a LOT more specific?

Such as, what do you want to do? Set up a network, connect to a network, set up a server, what kind of server, and so forth?

Most of the commands you will use will use (in a possible order of most used to less used):

ifconfig
iw or iwconfig (depending on version of ubuntu, and hardware)
route

These are the most comon, some more advanced tasks will require some system files to be edited and other programs used. Also program specific commands is not uncommon such as if you were to run a FTP server, or APACHE (web) server and so forth.


Regards

---

### Post by Frogs Hair on 2012-09-14
Plenty more where these came from. 

[http://www.sitepoint.com/ubuntu-12-04-lts-precise-pangolin-networking-tips-and-tricks/](http://www.sitepoint.com/ubuntu-12-04-lts-precise-pangolin-networking-tips-and-tricks/)

[https://help.ubuntu.com/community/InternetAndNetworking](https://help.ubuntu.com/community/InternetAndNetworking)

[http://www.liberiangeek.net/2012/05/windows-7-vs-ubuntu-12-04-how-to-map-network-shares/](http://www.liberiangeek.net/2012/05/windows-7-vs-ubuntu-12-04-how-to-map-network-shares/)

---

### Post by Primefalcon on 2012-09-14
if you want to see the commands available

run the command echo $PATH

this will show you a bunch of directories.... look at the files names in these directories and run in the command line man <filename> or even info <filename>.

you will learn a lot doing this... though this will be time consuming

most of the command will be in /usr/bin and I just did a check to see how many files/commands there are in there and the count was over 3k!
```
primefalcon@blackbeard:~$ ls -l /usr/bin | wc -l
3236

```

---

### Post by Mohan1289 on 2012-09-25
Thank you Guys

---

### Post by Mohan1289 on 2012-09-25
> **zero2xiii said:**
> Hay.

"Networking using linux" is a HUGE subject.

Can you please be a LOT more specific?

Such as, what do you want to do? Set up a network, connect to a network, set up a server, what kind of server, and so forth?

Most of the commands you will use will use (in a possible order of most used to less used):

ifconfig
iw or iwconfig (depending on version of ubuntu, and hardware)
route

These are the most comon, some more advanced tasks will require some system files to be edited and other programs used. Also program specific commands is not uncommon such as if you were to run a FTP server, or APACHE (web) server and so forth.


Regards

Yes i agree That's a Huge Subject..

I want to learn upto how to solve any issue in networking ;) 

i wanna learn as max as possible. Time is not a problem i will learn slowly but surely

---

### Post by zero2xiii on 2012-09-25
> **Mohan1289 said:**
> Yes i agree That's a Huge Subject..

I want to learn upto how to solve any issue in networking ;) 

i wanna learn as max as possible. Time is not a problem i will learn slowly but surely

Hay,

hahaha :)... then I suggest start getting issues and solve them ;P hahaha...

There is no "how to solve all network related issues" book. Nor on any other subject for that matter. It takes time, research, improvisation and very good and deep understanding of linux to get to the point you wish to get to.

A good start might actualy be the forums. Do a search and read through the threads networking related. There a few issues here at the moment regarding wi-fi for example. Follow them, dig with the people (don't fall in the soup with stupid questions and so forth if it is NOT your thread please haha, some guys tend to do that). Also try and understand what they are doing. Using various methods including but not limited to google.

Let us take an example. Lets say you need to connect to a network that does not have DHCP. And you want to use linux. First you will need to get an IP from your administrator. Let us assume you have that, or its a home network.

Now you read you have to pop open a terminal and type:
```
ifconfig -s -a
```

and list all devices (example output might be)
```
Iface   MTU Met   RX-OK RX-ERR RX-DRP RX-OVR    TX-OK TX-ERR TX-DRP TX-OVR Flg
eth0       1500 0   1849733      0      0 0       1385587      0      0      0 BMRU
lo        16436 0    130422      0      0 0        130422      0      0      0 LRU

```

Now we see you have a eth0 device. Right to configure that with the ip 192.168.1.2 ie. You do the command:

```
ifconfig eth0 192.168.1.2
```

Easy. Your problem is solved but you have not learned anything. Now comes the part you have to put in the extra time to learn. Now you can go and find out more about that "ifconfig" tool used. There are options. The ubuntu man pages are excellent and all tools are listed in them.

Simply go: man ifconfig
and you will get a document opened in terminal explaining what it does and how the software works. also most flags such as the "-s -a" in the example.

This is a VERY basic example. But just as an example look [here]("http://manpages.ubuntu.com/manpages/lucid/man5/interfaces.5.html") for how much information there is on a single file, networking related. Now you might never have to touch that file. True, but it is just an example.

The short of the long is, you need to research what you see, to understand and use it better. No book, or forum can 'teach' you. Sure they can guide you and give you information, a starting point if you wish. However you will need to explore on your own. And this is where the forums come in handy, not for posting "hay how do I do this and that" the whole time because you "want to learn" but by using the search function and finding related issues and see how they were solved. Most break down into one of several very simple ideas. And once you understand these ideas, you are already winning most of the fight.

Good luck and have an excellent journey.
We can assist you when you REALLY get stuck and cant find the answer yourself (see there is it again, find it yourself first, the journey means more to you than the destination). So have fun and good luck :)

Cherz

---

### Post by Mohan1289 on 2012-09-25
Yeah Forums are best used for Discussions and gathering different ideas and different ways to solve the problem.

Helping each other by correcting one's mistakes and guiding them in correct path.

---


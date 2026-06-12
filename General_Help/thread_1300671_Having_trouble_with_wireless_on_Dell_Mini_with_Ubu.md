---
title: "Having trouble with wireless on Dell Mini with Ubuntu"
date: 2009-10-25
forum: General Help
---

### Post by frustratedcustomer on 2009-10-25
I am quite frustrated. I just purchased a dell mini netbook that features ubunto and I am used to windows but figured whatever. I do not find it easy to get around with and the internet connection is what kills me. It took me FOREVER to get the wireless connection up and running for my house. What happens now when I want to take my netbook on a road trip with free wireless? How do I get it to connect then? I had to type in all sorts of things just to get it to connect to my house wireless router. Will this always happen? With my hp laptop(broke so I replaced with this) when I took it away with me it just always noticed there was a new network available and connected me? Will this be the same case?

---

### Post by Vaphell on 2009-10-25
which version of the ubuntu you have installed? older ones had quite a few problems but recent versions connect easily to wifi with no hassle (assuming that drivers for wifi are ok - if dell sells it with ubuntu, they should be)

---

### Post by snowpine on 2009-10-25
Hi FrustratedCustomer, welcome to the forums! Two important things to note:

1. This is a community forum, so everyone here is a user like you... nobody here is paid, and we aren't "official" support for either Ubuntu or Dell... you should contact Dell directly if you need tech support or think you're having a hardware issue with the wireless card (or if you need a refund! ;))
2. If you are new to Ubuntu, you really need to take things step by step and pay attention to detail. I mention this because you mis-spelled "Ubuntu" and you are very vague about "I had to type in all sorts of things"... if you're going to get good results with these forums, you need to share exactly what you did so we can help you. :)

I have a Dell Mini 9, and I love it. I have never had any wireless problems with Ubuntu whatsoever. I would say that either you have defective hardware, or you have a simple problem that can easily be fixed (if you share more details about your problem and what you've tried so far to fix it). 

ps This site is a great resource for Mini owners: [http://www.ubuntumini.com/](http://www.ubuntumini.com/)

---

### Post by noelvh on 2009-10-25
Well a good friend of mine got one of the Dell mini 9's with Ubuntu oe it and it was not configured well. He spen many hours on the phone with Dell, only to find they had no clue how to work with Linux. He was forced to waite for the Linux support team to contact him. Well they never did. When he call them asking when they will contact him they pointed him to the forums to get help. 

Well He returned the mini 9 back to dell for a XP version.

This pisses me off beyond belief. How dose one sell a product and not support it???

As you go I would rethink the install that came with the laptop, and install the netbook remix your self. And there is a ton of community site and help forums for just this case.

Do not give up, as it will get better as you go.

Noel

---

### Post by nothingspecial on 2009-10-25
What exactly, is your problem?

It seems that your wireless is working and if so then yes, it will see any free wireless networks when you are on the road.

---

### Post by frustratedcustomer on 2009-10-25
Sorry I didn't mean to be so vague:) Yes dell does NOT provide support for ubunto. My first problem was the dell mini keeps powering itself off after 30 mins. No explanation and dell support do not speak english nor understand what the problem is. Then I asked them how to connect to my wireless router and they said they do not provide support and I had to contact verizon, my provider. Once I did I was up and running within minutes for the internet. Every single time I boot up the computer it does not connect me to the internet. I have to manually do it. It's becoming frustrating with that part. My hp automatically connected me. How do I find out which version of ubunto I am running and where can I download the new updates for it? Thanks.

---

### Post by snowpine on 2009-10-25
> **frustratedcustomer said:**
> Sorry I didn't mean to be so vague:) Yes dell does NOT provide support for ubunto. My first problem was the dell mini keeps powering itself off after 30 mins. No explanation and dell support do not speak english nor understand what the problem is. Then I asked them how to connect to my wireless router and they said they do not provide support and I had to contact verizon, my provider. Once I did I was up and running within minutes for the internet. Every single time I boot up the computer it does not connect me to the internet. I have to manually do it. It's becoming frustrating with that part. My hp automatically connected me. How do I find out which version of ubunto I am running and where can I download the new updates for it? Thanks.

You are probably running the special "Dellbuntu" 8.04 that comes preinstalled... it has a special "launcher" interface that looks like this:

[http://www.automaticable.com/wp-content/uploads/2009/03/dell-ubuntu-desktop.png](http://www.automaticable.com/wp-content/uploads/2009/03/dell-ubuntu-desktop.png)

I personally am not a big fan of the Dellbuntu, so I replaced it with the current stable version of Ubuntu, 9.04 Jaunty Jackalope. (A new release, 9.10 Karmic Koala, is coming out next week.) If you decide to upgrade to a newer release, you'll find easy instructions at that dellmini.com website I linked to in my previous post.

Anyways, my point is, since I don't personally use the Dellbuntu 8.04, I can't really help with your problems... but there are lots of Dell Mini users on this forum, so I'm sure someone will drop by who knows the answer. In the future, if you use a descriptive title for your threads, it increases the odds that someone who knows the answer will read them. :) We also have a separate Dell-specific sub-forum [http://ubuntuforums.org/forumdisplay.php?f=342](http://ubuntuforums.org/forumdisplay.php?f=342) and a Search feature (top right corner of your screen).

---

### Post by P4man on 2009-10-25
ubunt**u**

---

### Post by Vaphell on 2009-10-25
assuming there are normal menus somewhere in the system

go to System Monitor in System->Administration
or launch terminal:
**cat /etc/*-release**


either way you should try installing newer version, it's not a rocket science, really :-)

---

### Post by frustratedcustomer on 2009-10-25
i don't understand what that meant? Please confirm. Thanks.

---

### Post by Matt__ on 2009-10-25
Dells still ship with 8.04 as did my mini10v a month ago.

wireless works faultlessly and has greater range than my main laptop which cost three times as much. I did however dump Dell netbook remix including their recovery partition and re-installed UNR8.04.

as for autoconnect...right clickwireless icon/edit connections/select your wireless/edit/check box 'automatic connect'


I suggest you download this Ubuntu new user guide too...free...[http://www.ubuntupocketguide.com/download_main.html](http://www.ubuntupocketguide.com/download_main.html) 
(UNR == Ubuntu netbook remix)

---

### Post by Vaphell on 2009-10-25
i assumed that your system is somewhat similar to default ubuntus, so there should be a menu when you can check stuff or get the answer from terminal
after that i read snowpine's post and it apparently looks nothing like default ubuntu i use.
Btw, i had similar problems with autoconnecting to wireless routers in 8.04. I don't know if dell solved it in their version.

If you have patience and will to learn something you could try to install new version manually, just find some tutorials how to install Ubuntu Netbook Remix or some other netbook distro - directions are in the snowpine's post. If not - well you can return it and buy version with XP :-)

---

### Post by MrCanuck on 2009-10-25
I installed Ubuntu on my Acer Laptop, it detected the wireless card on installation and as soon as it turned on for the first time it came up and showed my wireless connection (putting vista or XP on this means downloading drivers from my other computer and then transferring them here in-order to get any internet).  

I am an Ubuntu noobie, but i did see a lil box that said "auto connect" or something along that lines, look for that, i bet you its unchecked.

---

### Post by wcutrombonekid on 2009-10-25
i have never used the dellubuntu version.  sounds like i don't want to.  but switching versions to something line Ubuntu netbook remix or any other disto seems like a good idea.  you'll get a whole lot more support from it because more people are using it.  

linux can be hands on at times, which turns many people away.  but keep with it, its a good os.

---

### Post by gdonwallace on 2009-10-25
I agree. I just recently setup a wireless at home and was running 9.04 and the wireless setup was a breeze.  The first thing I would check is the version that you are on.  From system menu go to adminstration and then launch the system monitor.  On the first tab it will tell you what version of Ubuntu is installed on your mini.  If it is 9,04 then you are in a good spot.  If not, I would download the netbook bersion and install that one.  

If it is 9.04, make sure network manager is installed.  From the administration menu, go down to Synaptic Package Manager.  Launch that and enter your login password.  In the search box at the top of the screen type in "network manager" (without the quotes).  If the box in front of that program is not green, right click the box and select install.  Once installed it will put an icon in your upper panel.  Right click that icon and it will show all available wireless networks.  (I generally find my neighbors as well as my own)  Just click on yours and your good to go.  The next time you boot, Ubuntu will auto connect to your network.  

Do the same thing any time you want to connect to a wifi network anywhere else.

---

### Post by frustratedcustomer on 2009-10-25
ok i cannot seem to set up the evolution mail? Can someone please explain that? I cannot get ahold of ubuntu support.

---

### Post by wcutrombonekid on 2009-10-26
> **gdonwallace said:**
> I agree. I just recently setup a wireless at home and was running 9.04 and the wireless setup was a breeze.  The first thing I would check is the version that you are on.  From system menu go to adminstration and then launch the system monitor.  On the first tab it will tell you what version of Ubuntu is installed on your mini.  If it is 9,04 then you are in a good spot.  If not, I would download the netbook bersion and install that one.  

If it is 9.04, make sure network manager is installed.  From the administration menu, go down to Synaptic Package Manager.  Launch that and enter your login password.  In the search box at the top of the screen type in "network manager" (without the quotes).  If the box in front of that program is not green, right click the box and select install.  Once installed it will put an icon in your upper panel.  Right click that icon and it will show all available wireless networks.  (I generally find my neighbors as well as my own)  Just click on yours and your good to go.  The next time you boot, Ubuntu will auto connect to your network.  

Do the same thing any time you want to connect to a wifi network anywhere else.

i don't think his desktop works that way though, its the dell version so they've moved some things around

---

### Post by intruderukr on 2011-12-10
It means that you must open the terminal and type, (or  paste) the following:
cat /etc/*-release

---


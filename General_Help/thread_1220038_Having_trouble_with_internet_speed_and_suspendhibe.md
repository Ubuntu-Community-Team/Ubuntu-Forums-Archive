---
title: "Having trouble with internet speed and suspend/hibernate in Ubuntu 8.10"
date: 2009-07-22
forum: General Help
---

### Post by vmanisme on 2009-07-22
The first problem (and the main) is the internet speed.  On Windows 7 my speed averages out about 65000kbps... On Ubuntu when I do I speed test I never get anything above 4500kbps.... Same with upload speeds.... I have Verizon FiOS so having those speed is funny...

The second problem (I had this exact problem with Ubuntu 8.10) is that I cannot hibernate or suspend my computer... Running at 1200watts I cant use Ubuntu if I cant put my computer to sleep...
- I tried the following articles to try and fix this. 
[http://ubuntuforums.org/showthread.php?t=1058144](http://ubuntuforums.org/showthread.php?t=1058144)
[https://answers.launchpad.net/ubuntu/+question/68469](https://answers.launchpad.net/ubuntu/+question/68469)


GUYS I LOVE UBUNTU BUT THESE ARE MAJOR PROBLEMS I WISH I COULD USE IT AS EVERY-DAY OS PLEASE HELP ME FIX THIS I DONT WANT TO GO BACK TO WINDOWS...

---

### Post by Ashish Meena on 2009-07-22
try upgrading to 9.04, might resolve the issue

---

### Post by vmanisme on 2009-07-22
> **Ashish Meena said:**
> try upgrading to 9.04, might resolve the issue

I am on 9.04... same problems.  I love Ubuntu but I'm gonna have to go back to Windows because I've reported this in 8.10 nobody replied or even try to help me fix this... This problem is ALL OVER Google and no moderator or admin forwarded this to the big guys, that just makes me sad that such a good OS has such a bad team...

I'm getting my wireless issue fixed in another section but I cant afford to use Ubuntu without suspend of hibernate...

---

### Post by piratebill on 2009-07-22
how big is your swap partition?  if it is smaller than your RAM size then hibernate wont work

---

### Post by vmanisme on 2009-07-22
> **piratebill said:**
> how big is your swap partition?  if it is smaller than your RAM size then hibernate wont work

I gave 50GB to Ubuntu.  And kept 590GB to windows..

---

### Post by michy99 on 2009-07-22
> **vmanisme said:**
> I gave 50GB to Ubuntu.  And kept 590GB to windows..

But do you have a swap partition? What does this show?```
sudo fdisk -l
```

---

### Post by piratebill on 2009-07-22
> **vmanisme said:**
> I gave 50GB to Ubuntu.  And kept 590GB to windows..

The swap partition is something different than that.  

EDIT:
previous poster beat me to it

---

### Post by vmanisme on 2009-07-22
> **piratebill said:**
> The swap partition is something different than that.  ```
sudo fdisk /dev/sda
```

then type p to get a listing of your partition tables.  what is the output?

Is there anyway to change it can you give me the code because I think that is my problem right there... Im on Windows 7 right now working with some C++ stuff so I'm kind of busy.  So if theres a code to change SWAP please share the code and make me a happy Ubuntu user :D

---

### Post by hibliss on 2009-07-22
You can suspend to ram without a swap partition, but cannot hibernate without one. My guess if you do not know what a swap partition is is that you do not have one and that is your issue there.

As far as internet speed, I too have FiOS and it is the same in Intrepid, Jaunty, Fedora, Win XP, Win Vista, Win 7, etc. Where are you getting these speed readings? Are you running speedtests on a website like [http://speedtest.net]("http://speedtest.net")?

---

### Post by dk06 on 2009-07-22
> **vmanisme said:**
> I am on 9.04... same problems.  I love Ubuntu but I'm gonna have to go back to Windows because I've reported this in 8.10 nobody replied or even try to help me fix this... This problem is ALL OVER Google and no moderator or admin forwarded this to the big guys, that just makes me sad that such a good OS has such a bad team...

I'm getting my wireless issue fixed in another section but I cant afford to use Ubuntu without suspend of hibernate...
________________________________________________

Hibernation:
[http://ubuntuforums.org/showthread.php?t=417964&page=2](http://ubuntuforums.org/showthread.php?t=417964&page=2)
[http://www.ubuntugeek.com/fix-for-suspend-and-hibernation-problem-for-laptops.html](http://www.ubuntugeek.com/fix-for-suspend-and-hibernation-problem-for-laptops.html)
[http://www.linuxquestions.org/questions/ubuntu-63/hibernate-ubuntu-355177/](http://www.linuxquestions.org/questions/ubuntu-63/hibernate-ubuntu-355177/)
_________________________________________________
WiFi:
Download the XP driver from the manufacturer's website
& use the '.inf' file with Ndisgtk (GUI for Ndiswrapper)
*You may be using a generic wifi driver

---

### Post by piratebill on 2009-07-22
> **vmanisme said:**
> Is there anyway to change it can you give me the code because I think that is my problem right there... Im on Windows 7 right now working with some C++ stuff so I'm kind of busy.  So if theres a code to change SWAP please share the code and make me a happy Ubuntu user :D

I thought you needed a swap in ubuntu.  If you have the swap partition, gparted will let you resize it.  it will take a while so let the program finish.  if you resize your windows partition, make sure you defrag it first.

---

### Post by hibliss on 2009-07-22
Ubuntu can be run with no swap partition, you just can't hibernate and depend entirely on your ram. Ubuntu also has the ability to use a swap file like Windows does.

---

### Post by vmanisme on 2009-07-22
Can someone explain or give me a tutorial on that whole SWAP portion thing...?  And also who ever was asking about my internet problems heres the link to the topic:
[http://ubuntuforums.org/showthread.php?t=1220061](http://ubuntuforums.org/showthread.php?t=1220061)

---

### Post by piratebill on 2009-07-22
> **hibliss said:**
> Ubuntu can be run with no swap partition, you just can't hibernate and depend entirely on your ram. Ubuntu also has the ability to use a swap file like Windows does.

I did not know that.  I am so getting rid of it for my next install.  thanks :)

---

### Post by hibliss on 2009-07-22
> **piratebill said:**
> I did not know that.  I am so getting rid of it for my next install.  thanks :)

I did not say there was no benefit in have a swap partition ;)

OP, your internet issues are strange. I live in your area and have FiOS as well, though you seem to have a package that I did not even know existed if you are getting 83 down, I thought their top package was 50/50.

Anyway, from the other thread it seems that you are using a USB WiFi adapter? RTL8187B?

What kind of speeds do you get with the Ethernet cable plugged in? Seems like the issue may be your WiFi drivers.

---

### Post by oxf on 2009-07-22
> **hibliss said:**
> You can suspend to ram without a swap partition, but cannot hibernate without one. My guess if you do not know what a swap partition is is that you do not have one and that is your issue there.

As far as internet speed, I too have FiOS and it is the same in Intrepid, Jaunty, Fedora, Win XP, Win Vista, Win 7, etc. Where are you getting these speed readings? Are you running speedtests on a website like [http://speedtest.net](http://speedtest.net)?

Am I understanding you correctly that websites such as speedtest are unreliable?

---

### Post by vmanisme on 2009-07-22
> **hibliss said:**
> I did not say there was no benefit in have a swap partition ;)

OP, your internet issues are strange. I live in your area and have FiOS as well, though you seem to have a package that I did not even know existed if you are getting 83 down, I thought their top package was 50/50.

Anyway, from the other thread it seems that you are using a USB WiFi adapter? RTL8187B?

What kind of speeds do you get with the Ethernet cable plugged in? Seems like the issue may be your WiFi drivers.

With wire I hit 150k.  The FiOS guy told me that it was their record nobody even gotten speeds like mine but he said that it was okay as long as I pay my bills on time they don't care.

---

### Post by QIII on 2009-07-22
I peg Speakeasy's speed tester in Vista, Jaunty and Karmic.

I don't think it's the OS, per se.

Not at my Ubuntu machine right now, but if I can get back here later, I'll see how my eth0 is configured.


BTW -- I won't use Verizon.  They dug a trench through my front yard to lay their fiber in my neighborhood.  The trench was on MY SIDE of the utility right of way, they wrecked my sprinkler system, cut my cable and then said "Too bad" when I complained.

---

### Post by vmanisme on 2009-07-22
> **QIII said:**
> I peg Speakeasy's speed tester in Vista, Jaunty and Karmic.

I don't think it's the OS, per se.

Not at my Ubuntu machine right now, but if I can get back here later, I'll see how my eth0 is configured.

I tried verizon's on-router test same thing

---

### Post by hibliss on 2009-07-22
> **oxf said:**
> Am I understanding you correctly that websites such as speedtest are unreliable?

No, not sure how you read that from what I posted, they are fine. Just wondering where the OP was getting the speed numbers.

@OP, what is the wireless driver you are using for your adapter? You get good speeds when plugged in via Ethernet?

---

### Post by vmanisme on 2009-07-22
I'm not using Vista im on Windows 7

---

### Post by bob-linux-user on 2009-07-22
I have had problems getting hibernate to work on Jaunty and have not found a working solution anywhere, BUT if you use the EXT4 file system you will find your PC will boot from cold a lot more quickly anyway. How much time would you save even if hibernate was working properly? It can't be more than a few seconds. Can someone who HAS got hibernating working properly give us us some actual comparative timings here please?

---

### Post by hibliss on 2009-07-22
> **bob-linux-user said:**
> I have had problems getting hibernate to work on Jaunty and have not found a working solution anywhere, BUT if you use the EXT4 file system you will find your PC will boot from cold a lot more quickly anyway. How much time would you save even if hibernate was working properly? It can't be more than a few seconds. Can someone who HAS got hibernating working properly give us us some actual comparative timings here please?

Hibernate works fine. On my Eee, about 9 seconds to wake up from hibernation to a fully working desktop.

---

### Post by bob-linux-user on 2009-07-22
Hibliss. Thanks for the info. Out of curiosity how long does it take to boot from cold after previously being completely shut down please?

---

### Post by hibliss on 2009-07-22
Almost a full minute including entering the password for keyring to log on to the WiFi.

---

### Post by izizzle on 2009-07-22
@OP:

For your internet issues: have you tried disabling IPV6 in Ubuntu/Firefox?

---

### Post by vmanisme on 2009-07-23
> **izizzle said:**
> @OP:

For your internet issues: have you tried disabling IPV6 in Ubuntu/Firefox?

Yep, nothing changed..

---

### Post by hibliss on 2009-07-23
Did you look in to what driver you are using for the WiFi card? That is likely the issue. I live in the DC Metro area (I saw you do to from your speedtest). I can come to your house and show you Ubuntu utilizing your full connection both wired and wireless on my notebook.

---

### Post by bob-linux-user on 2009-07-24
@hibliss (post #25) looks like my theory was wrong. Sorry. Obviously your computer shows a massive speed improvement comparing booting from hibernate to booting from cold.

---


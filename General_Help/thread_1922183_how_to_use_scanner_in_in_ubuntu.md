---
title: "how to use scanner in in ubuntu"
date: 2012-02-08
forum: General Help
---

### Post by Fayaz427 on 2012-02-08
hai eveyone....
iam using ubuntu 11.10...
i have hp deskjet 1050(printer,scanner,copier)...
how to make use of hp deskjet 1050(printer,scanner,copier) in ubuntu 11.10...
please help me as iam new to ubuntu...

---

### Post by raja.genupula on 2012-02-08
[https://help.ubuntu.com/community/HpAllInOne](https://help.ubuntu.com/community/HpAllInOne)

---

### Post by ajgreeny on 2012-02-08
Make sure you have both hplip and hplip-gui installed and it will probably work immediately.  The hplip-gui package gives you a terrific configuration and control application, better even than I remember from my Windows XP days.

---

### Post by jamesisin on 2012-02-08
I use XSane with my HP scanner.  Works great (and is way better than the XP software which originally came with it).

---

### Post by Fayaz427 on 2012-02-09
when i tried to install hplip from ubuntu software centre...
i came across aerror stating that "failed to download package files check your internet connection" and another error as "requires inatallation of untrusted packages..
Not only hplip software...foe other softwares also the arror message is same...
and my internet connection is perfect..
what might be the problem??

---

### Post by raja.genupula on 2012-02-09
open your terminal and type ```
sudo apt-get update
``` and paste the output here .

---

### Post by dannyboy79 on 2012-02-09
> **Fayaz427 said:**
> when i tried to install hplip from ubuntu software centre...
i came across aerror stating that "failed to download package files check your internet connection" and another error as "requires inatallation of untrusted packages..
Not only hplip software...foe other softwares also the arror message is same...
and my internet connection is perfect..
what might be the problem??it sounds like you're repositories are not setup correctly IF you're on the internet posting in the forum BUT you can't install software. Also, IF it's warning you of untrusted packages you may be using an untrusted repository.

HP printers are about the only ones that pretty much can be FULLY used within linux (as far as I am aware) so it does work BUT it sounds like you have other issues. GOod luck

---

### Post by Fayaz427 on 2012-02-09
Thank you evey one for supporting me...
Everything is Fine... :)

---

### Post by jamesisin on 2012-02-10
Of course you should probably let everyone know your solution(s) in case anyone following along after might have the same problem.

---

### Post by thopepype on 2012-02-10
I was recommended this website by my cousin. I am not sure whether this post is written by him as no one else know such detailed about my trouble. You're wonderful! Thanks! [garage door repair](http://www.vansity.com/cgi-bin/yabb/YaBB.cgi?board=General;action=display;num=1326348742;start=0#3)

---

### Post by Fayaz427 on 2012-02-10
i have used command which is stated below
sudo apt-get update
and then installed hplip from ubuntu software centre... 
now iam able to use printer,scanner and copier......

---


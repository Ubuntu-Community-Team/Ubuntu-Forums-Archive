---
title: "Ubuntu Software Center is very unresponsive and slow"
date: 2012-07-02
forum: General Help
---

### Post by ubnewbie2 on 2012-07-02
Ubuntu Software Center is painfully slow to use, and at times the whole system slows almost to a halt. Running 'top' as root in a console window shows update-apt-xapi hogging cpu and bogging down the whole system.

Normal?

---

### Post by Lyfang on 2012-07-02
Have you tried Synaptic (package manager)?

---

### Post by GreatDanton on 2012-07-02
What is your system requirements. I usualy had problems if I run package manager with low specification computer.

---

### Post by ajgreeny on 2012-07-02
See this thread, [http://ubuntuforums.org/showthread.php?p=6935368](http://ubuntuforums.org/showthread.php?p=6935368) post #8 in particular, which shows how to make the update-apt-xapian-index "nicer" so it hogs fewer resources when you are trying to do other things.

Also worth a look through this googlubuntu search which shows how this has been along term problem, though it does seem to have solutions.
[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=update-apt-xapi&as_qdr=all&sa=Google+Search&lang=en]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=update-apt-xapi&as_qdr=all&sa=Google+Search&lang=en")

---

### Post by vasa1 on 2012-07-02
> **ubnewbie2 said:**
> Ubuntu Software Center is painfully slow to use, and at times the whole system slows almost to a halt. Running 'top' as root in a console window shows update-apt-xapi hogging cpu and bogging down the whole system.

Normal?

To my mind, update-apt-xapi should run once a day. I'm not sure that it's in anyway related to the act of opening the Ubuntu Software Center other than coincidence.

But I do agree that the Ubuntu Software Center is a bit on the heavy side for those who have limited computing resources.

Edit:
See  /etc/cron.daily/apt

---

### Post by ubnewbie2 on 2012-07-02
> **vasa1 said:**
> To my mind, update-apt-xapi should run once a day. I'm not sure that it's in anyway related to the act of opening the Ubuntu Software Center other than coincidence.

But I do agree that the Ubuntu Software Center is a bit on the heavy side for those who have limited computing resources.

Edit:
See  /etc/cron.daily/apt

Well, update-apt-xapi stopped running as soon as I closed Ubuntu Software Center. I think it must be triggering it.  

Funny thing is that, Synaptic runs fine, despite from what I've just read, it is involved in speeding up searches in Synaptic as well.  Has to be Software Center problems.  I guess I'll just stop using it - pity as Ubuntu seem to be making a big thing of it.

---

### Post by vasa1 on 2012-07-02
> **ubnewbie2 said:**
> Well, update-apt-xapi stopped running as soon as I closed Ubuntu Software Center. I think it must be triggering it.  
...

Is it correct that each time you open the Ubuntu Software Center, you see update-apt-xapi run? Even if it's repeatedly on the same day?

Edit: I don't see that.

---

### Post by ubnewbie2 on 2012-07-02
> **vasa1 said:**
> Is it correct that each time you open the Ubuntu Software Center, you see update-apt-xapi run? Even if it's repeatedly on the same day?

Edit: I don't see that.

No, that's not quite what I meant to say. It is either a huge coincidence that, running Software Center and installing a new program after the computer has been running ALL day, just happened at the same time as update-apt-xapi was running, or else, as I suspect, maybe it, hadn't run for a while and that just triggered it to run then.

Even when it isn't running, Software center and the associated processes it runs, just runs BOTH cpus to near 100% for the duration, so I am going to steer clear of it in future.  I hope Ubuntu isn't going in for bloatware :)

---

### Post by dino99 on 2012-07-02
also see :

 software-center (5.3.3.1) quantal; urgency=low

  * fix apt-xapian-index plugin (LP: #1019581)

---

### Post by vasa1 on 2012-07-02
> **ubnewbie2 said:**
> ...
Even when it isn't running, Software center and the associated processes it runs, just runs BOTH cpus to near 100% for the duration, so I am going to steer clear of it in future.  I hope Ubuntu isn't going in for bloatware :)
Well, that certainly is your prerogative but I feel something isn't quite right about "BOTH cpus to near 100% for the duration". I don't see that and I haven't come across similar complaints here or over at askubuntu.com.

---

### Post by vasa1 on 2012-07-02
> **dino99 said:**
> also see :

 software-center (5.3.3.1) quantal; urgency=low

  * fix apt-xapian-index plugin (LP: #1019581)

Not really the point here. I very much doubt OP is on QQ although details of the OS and CPU and RAM are awaited.

---

### Post by ubnewbie2 on 2012-07-02
> **vasa1 said:**
> although details of the OS and CPU and RAM are awaited.

Sorry, I meant to agree earlier that my system is not hugely fast.  That's the reason I switched to Ubuntu from Windows 7. :)

Anyway, it's an Intel Atom 1.6GHz x 2 , with 2GB ram, running 12.04.

---

### Post by dino99 on 2012-07-02
> **ubnewbie2 said:**
> Sorry, I meant to agree earlier that my system is not hugely fast.  That's the reason I switched to Ubuntu from Windows 7. :)

Anyway, it's an Intel Atom 1.6GHz x 2 , with 2GB ram, running 12.04.

so better to use synaptic

sudo apt-get install synaptic

---

### Post by ubnewbie2 on 2012-07-02
> **vasa1 said:**
> Well, that certainly is your prerogative but I feel something isn't quite right about "BOTH cpus to near 100% for the duration". I don't see that and I haven't come across similar complaints here or over at askubuntu.com.

No?  I thought someone earlier in the thread said it has been a long term problem.

Anyway, SOMETHING is making Software center a real bear to use - too painful by far, and when I see the first 2 lines in 'top' showing Software Center, and the install processes running at 90+% cpu, I tend to think that I am correct in thinking it's Software Center causing it.

btw. should I be trying to use askubuntu, or these forums, for these types of queries?

---

### Post by ubnewbie2 on 2012-07-02
> **dino99 said:**
> so better to use synaptic

sudo apt-get install synaptic

Yep!  (already got it)

---

### Post by vasa1 on 2012-07-02
> **ubnewbie2 said:**
> No?  I thought someone earlier in the thread said it has been a **long term problem**.
...
btw. should I be trying to use askubuntu, or these forums, for these types of queries?
I think the long term problem mentioned [here]("http://ubuntuforums.org/showpost.php?p=12068954&postcount=4") relates to the "update-apt-xapian-index" business and not to the Ubuntu Software Center. I [asked about it]("http://askubuntu.com/questions/79481/is-100-cpu-usage-harmful-while-update-apt-xapi-runs") as well when I noticed my CPU shooting up every day.

Where you ask is your preference but wherever you choose to ask, the more detail and background you provide, the more likely it is that someone will be able to help.

---

### Post by vasa1 on 2012-07-02
While Synaptic is certainly handy to have around, an even lighter solution is the command line.
If it's just a matter of updates, then
sudo apt-get update
and sudo apt-get upgrade
should do it.
You can read more about [apt-get]("https://help.ubuntu.com/community/AptGet/Howto/") here and I doubt you can get lighter than that. (And now the aptitude folk will chime in.)

---

### Post by ubnewbie2 on 2012-07-02
> **vasa1 said:**
> While Synaptic is certainly handy to have around, an even lighter solution is the command line.
If it's just a matter of updates, then
sudo apt-get update
and sudo apt-get upgrade
should do it.
You can read more about [apt-get]("https://help.ubuntu.com/community/AptGet/Howto/") here and I doubt you can get lighter than that. (And now the aptitude folk will chime in.)

I do occasionally use apt-get yes.

Where I was coming from was, I wanted to try the Ubuntu Unity experience - hence I tried the "standard" way new users are expected to use Unity.  In fact, the same idea was why I decided to give Unity itself a try instead of reverting to the more familiar gnome desktop of previous versions.  By doing this, I have, in fact, decided to keep using Unity. It actually works quite well when you lose your preconceptions.

As Software Center was part of that, I gave it a try.  Even on a fast computer, I think I would prefer Synaptic.  I like seeing what dependencies are needed, and seeing what the total size is, of the app I am adding.

---

### Post by vasa1 on 2012-07-02
> **ubnewbie2 said:**
> I do occasionally use apt-get yes.

Where I was coming from was, I wanted to try the Ubuntu Unity experience - hence I tried the "standard" way new users are expected to use Unity.  In fact, the same idea was why I decided to give Unity itself a try instead of reverting to the more familiar gnome desktop of previous versions.  By doing this, I have, in fact, decided to keep using Unity. It actually works quite well when you lose your preconceptions.

As Software Center was part of that, I gave it a try.  Even on a fast computer, I think I would prefer Synaptic.  I like seeing what dependencies are needed, and seeing what the total size is, of the app I am adding.

For anything, something with an elaborate GUI versus a minimal GUI, it's no surprise  which will be lighter.

The ornamentation of USC reminds me of Mozilla's add-ons site and Chrome's web store. To my mind, many of the extensions one wishes to download end up being smaller (kB) than the page itself.

Anyway, I came to this thread because I was intrigued by the title and some of the experiences described that would certainly be of concern if I were to experience them.

---

### Post by Cardale on 2012-07-02
Gnome is coming out with an App Store maybe that will help.

---


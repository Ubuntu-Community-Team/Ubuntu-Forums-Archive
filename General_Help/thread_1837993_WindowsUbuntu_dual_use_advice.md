---
title: "Windows/Ubuntu dual use advice"
date: 2011-09-02
forum: General Help
---

### Post by thaumx on 2011-09-02
Let me start out by saying that after using Ubuntu 11.04 exclusively at  home for the last several weeks, I've found myself really enjoying the  experience. Best of all, Ubuntu has provided a great solution for the  family computers. My wife and daughter (who's just now old enough to use  a computer herself) are able to use Ubuntu without any issues. Since  they aren't very knowledgeable about computers, security had been a  constant worry on my end. (not to mention a lot of extra work!) 

They  like the Unity desktop (especially my daughter) and my wife was even  able to troubleshoot a skype/netbook microphone issue herself. So Ubuntu  is going to be remaining in our household for the foreseeable future.  But here's the rub... As much as I'd like to use Ubuntu exclusively on  my computer, it hasn't really worked out. PC games and creative software  like CS5 really aren't working out like I want in Linux.

I know I  can dual boot into both, but the last time I tried that (6 or 7 years  ago now!) I ended up using windows pretty much all the time because of  the hassle of rebooting to switch OSes. Lately I've been looking into  perhaps using virtualbox to run a Ubuntu guest on a windows host. I'd  use linux for most things, but then be able to drop back to the host for  games and art. My system isn't lacking for power, so I don't see an  issue with doing everything but gaming and art in the virtual machine. 

A few questions:
1) does using Ubuntu in a virtual machine make it less secure?
2) It it persistent/stable enough to use as a "primary" OS even though it's run in a virtual machine?
3)  Outside of sharing files between host and guest, how likely is it that  if I surf to a bad page in ubuntu, malware gets on windows? (because  internet/data flows through host to guest, right?)
4) how  difficult/inconvenient is it to have access to media in the virtual  machine? (If I put it all into the guest Ubuntu, will I still be able to  access it from windows or visa versa without setting up a huge shared  folder?) 
5) for data backup purposes will data backup be possible  from the guest side? is it possible/likely to lose everything in my  guest OS if windows/virtualbox has a hiccup?
6) If I'm forced to  share my data between OSes via a shared folder for movies/pictures/etc,  how vulnerable does this make the host windows OS?

Thanks a lot for your help/advice!

---

### Post by JC Cheloven on 2011-09-02
Hi, and welcome to the forums!

Nowadays, it's difficult to say what's NOT possible :)
I think no one would dare to assure anything about this kind of vulnerability, but rather to confirm whether something is in fact known to have happened or not.

Regarding your question, it seems that this kind of attack over the host via a VM [seems to have happened]("http://www.zdnet.co.uk/news/security-threats/2009/06/09/virtual-machine-exploit-lets-attackers-take-over-host-39661637/"). 

Anyway, I think it makes little sense to use into a VM the system you want to use as your primary operating system. If you're a gamer in the heart, you should use windows, because gnu-linux isn't really up to par in that. If you want to use ubuntu for almost anything else, dual booting is the way. A virtual machine is only advisable 1) for exploring and testing a new OS, or 2) when you have to do something particular which has to be done in the other OS, but what you seldom need.  3) oh, almost forgot, to test web pages, pdf docs, and other stuff you generate and want to check how it's seen in the win2 world. Just my opinion though.

(EDIT: perhaps you'd better chances to get more qualified answers in the security subforum?)

Best
JC

---


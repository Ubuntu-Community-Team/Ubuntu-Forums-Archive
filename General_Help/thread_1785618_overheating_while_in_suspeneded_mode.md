---
title: "overheating while in suspeneded mode"
date: 2011-06-18
forum: General Help
---

### Post by heron7 on 2011-06-18
Hi,
 I have noticed that the Acer Travelmate '10.04 netbook', is heating up while bringing it out of suspended  mode,that's when it does'nt decide to turn off the whole machine instead. 
 
Should 'nt it be asleep?.. I would use hibernate but that surely does'nt come back on. I stopped trying so I used suspend instead. but the temp must be around 48° .
I removed a usb mouse that fed off the power supply and still left  a usb in ,but that shouldnt prevent it from goin to bed ,right?..
Windoze doe'nt like it ,emm does't do it , Not notsleep ... 
help anyone, please 
:KS

---

### Post by heron7 on 2011-06-21
I just turned the machine back on from suspens mode and remebered I asked about it here, so I came to look If anyone else using an Acer or any other machine has such a problem 'bug' whatever . I am NOT blaming Mr. Linus. 
ok?.
thanks?
[http://en.wikipedia.org/wiki/Notebook_processor](http://en.wikipedia.org/wiki/Notebook_processor) :
[http://www.intel.com/support/processors/sb/CS-028869.htm](http://www.intel.com/support/processors/sb/CS-028869.htm) :

---

### Post by heron7 on 2011-06-27
I can't help myself coming back to look for any replies aver the hibrenation or suspend modes that Linux seem to have a Big problem with. 
Every time i return to my Acer TM & either see that it's Not warming up while on Win7 even without setting it to sleep or hibernate but On Netbook 10.04 it just heats up ,even the areas that are not above the cpu . like the side where the usb's are either or the usb port for the wifi. 

I wanna know if its damaging the pc. I mean it's more than possible that either some drivers or some other layer '(noobtalk) sorry'.. is not fully integrated, bug ?... butterfly loose whatever?..
but apparently I am the only one having this problem .
Or . the forum is moved else where & only a few zombies that can't read or write..

I come here over a year & half and if i had three decent replies in all this time ,To half a dozen questions i desperately needed at the time. well than The Foss Community can do without me. 

'no **** they can'; buddy.
don't the door hit your sorry *** on the way out; mmuhhaha :popcorn:

thanks folks,
they think it's all over; it is now!

case Unsolved 
Mystery butt_ner_fly in thz machine of ich :~(

---

### Post by pqwoerituytrueiwoq on 2011-06-27
after waking up the maching does not go into ondemand mode but instad it goes to performance that has happened to me on my laptop
add the cpu scaling applet to your panel so yuo can set it to ondemand or conservative
1 applet per core and make sure each applet is set for its own core
to set it co conservative at boot do this
gksudo gedit /etc/init.d/ondemand
edit line 27:
        echo -n ondemand > $CPUFREQ
to this:
        echo -n conservative > $CPUFREQ

---

### Post by heron7 on 2011-07-12
This is a brand new machine ; you know Acer Timeline ; and you're suggesting a 1.3 Ghz cpu dual is over heating because it goes in overdrive ,when befor waking up it senses i'm going to disturb i's NOT so asleep mode & fights back?... i open the lid and it's warm directly which is because he never went in suspend mode to begin with,so it should not goin over to catch up fast..?.. the thing never went still ;it's next to my pillow i can hear the fan through the night ... am i supposed to go tune a brand cpu ?.. and then when i do want to use the machine with Window7 ,what is it gonna make of it,?? or is the setting exclusive to Ubutnu??.. 
You know , before coming here again today i did another search ;'Is Linux not only Ubuntu overrated' ?... I can't seem to forget what a techei once said that it was experimental /in constant devel os's NOT for stable working ,know not much about pc's kind of people ; and I have noticed that recently  alot less posts ,articles about Linux distros in general on the web , hense my search too. 
I'm have to admit Ive learn alot since I first posted where' is Mr's sudo i don't see him anywhere?...
but i still have yet to be convinced of the major benefits one gets by using FOSS. I think  it's an uphill battle because you're caught in a jam with the 'proprietary' (what a word) hardware. Sure you can hack it , **** you?.. But also Windows7 improved alot and now 8 coming out ,people came looked some liked and stuck around but still have a dual boot ..you know ?.. even the hardest core of Linuxers I think still has a version of XP pro somewhere... possibly even Vista .. wow that'll shock me too ; ) 
I'm ranting again ant i ??... well lucky for you i dont come here often ; i wonder why..
Am i slipping away or is Ubuntu gone ahead without me...?..


they think it 's allover .. it's sure looking that way : (
& now i'm asking myself what's the point of me sending this post out ?...
it's not gonna fix the pc ... 
ah ;well ... i'm known for being tongue first and  thought later ,so i'll live up to that defucktoo ...

---


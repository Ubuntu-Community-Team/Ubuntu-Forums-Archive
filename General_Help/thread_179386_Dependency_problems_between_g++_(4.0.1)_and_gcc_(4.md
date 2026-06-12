---
title: "Dependency problems between g++ (4.0.1) and gcc (4.0.2)"
date: 2006-05-19
forum: General Help
---

### Post by rwestgeest on 2006-05-19
I cannot install build-essentials due to dependency problems between g++ and gcc. 

I am a keen advocate of apt. I really like it. However my situation leaves me very surprised. For some ruby extension (does not matter) I need g++. So i tried 

[FONT="Courier New"]apt-get install build-essential[/FONT]

As a result I got:

[FONT="Courier New"]The following packages have unmet dependencies:
  build-essential: Depends: g++ (>= 4:4.0) but it is not going to be installed
[/FONT]

So in an attempt to find out why i tried 

[FONT="Courier New"]apt-get install g++-4.0[/FONT]

with this demotivating result:

[FONT="Courier New"]The following packages have unmet dependencies:
  g++-4.0: Depends: gcc-4.0-base (= 4.0.1-4ubuntu9) but 4.0.2-5 is to be installed
           Depends: gcc-4.0 (= 4.0.1-4ubuntu9) but 4.0.2-5 is to be installed
           Depends: libstdc++6-4.0-dev (= 4.0.1-4ubuntu9) but it is not going to be installed[/FONT]

It appeared that my currently installed gcc is 4.0.2-5. I tried several things ao:
[LIST]
[*]downgrade gcc and everything that depended on it to 4.0.1-4ubuntu9 but that leads to uninstalling gnome and quite a few other packages i would not want to live without. 
[*][get a clean sources.list]("http://www.psychocats.net/ubuntu/sources")as hinted in another thread but that did not help.
[/LIST]

I refuse to believe that the breezy ubuntu archives has such a broken dependency, it must be my specific situation. What i do not understand is: how cat an ubuntu installation get such a broken dependency (except for 'by messing up the sources list')? And how can i fix it? 
 
I hope someone can help me out here. Similar issues have been posted on one of these forums before but none of them are exactly the same and none of the solutions worked for me.

---

### Post by rwestgeest on 2006-05-28
am i on the wrong forum - or is this a very difficult problem ?

---

### Post by rwestgeest on 2006-05-28
Hi ubuntu forum - thanks for being my rubber duckling. I found the solution myself. As it might be of use in another equal but different situation, ill post it here. 

I am not sure of the cause of my problem but i had some new 4.0.2-5 versions of gcc-4.0-base installed. All standar apt-get tricks for resolving broken packages did not work, because i did not  have broken packages installed, Apt just dit not want to install g++-4.0 due to dependency problems with gcc-4.0 and gcc-4.0-base.

Appearently i installed a newer version of gcc (and possibly other packages) using a faulty (i.e. non standard ubuntu) apt-source. 

I got very scared when, in an attempt to downgrade gcc-4.0-base to gcc-4.0-base=4.0.1-4ubuntu9 apt showed my a huge list of packages to uninstall ***including apt itself***. That was where i stopped and posted the message above..

**The solution**
The solution was to carefully downgrade a collection of dependent packages (so not only gcc-4.0-base). Appearently apt is clever but not clever enough to understand that if i say

```
apt-get install gcc-4.0-base=4.0.1-4ubuntu9
```

it guesses that all dependent packages should download to the same kind of version level.

So i typed:

```
apt-get install gcc-4.0-base=4.0.1-4ubuntu9 gcc-4.0=4.0.1-4ubuntu9 libstdc++6-4.0-dev=4.0.1-4ubuntu9 cpp-4.0=4.0.1-4ubuntu9 libstdc++6=4.0.1-4ubuntu9
```

now i got a shorter list of packages (not including apt) to remove. 

Then i tried pasting all the packages in the remove list in the apt-get install command line. This is where i found the troublemaker. The cpp and gcc showed dependency problems. And an apt-cache show of both packages showed that two versions where available. Step by step i changed the (huge) apt-get install commandline to explicitly include the older (corrent breezy-) versions of packages that had dependency problems and after some time it just worked.

the troublemakers (in my case) where:
[LIST]
[*]cpp downgraded to 4:4.0.1-3
[*]gcc  downgraded to 4:4.0.1-3
[*]libgcj6 downgraded to 4.0.1-4ubuntu9
[*]gij-4.0 downgraded to 4.0.1-4ubuntu9
[/LIST]

I still don't know where i got the wrong cpp and gcc versions from. (and i still don't know if i have posted this on the right list).

Cheers
Rob

---


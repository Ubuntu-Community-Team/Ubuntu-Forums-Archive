---
title: "again, what is the best way to run IE on Ubuntu"
date: 2009-11-09
forum: General Help
---

### Post by zhangweiwu on 2009-11-09
Hi. I believe this question has to be asked and discussed twice a year, because things changes, e.g. wine 1.0 release and ubuntu 9.10 release, and crossover releases new version once a while too.

I want to repeat this question, only to get answers from nowadays:
[http://ubuntuforums.org/showthread.php?t=611676](http://ubuntuforums.org/showthread.php?t=611676)
Quote it here to save you from a click:
> three possible answers;

A) Install Wine then install IE 6.0 from wine
B) Install Crossover and then install IE 6.0
C) Install IE4Linux 
Which way is stable and functional?

And plus a few new questions:
- How do you feel running ie6 on Ubuntu 9.10, is it better than on 9.04? Please be specific in which of the A, B, C that you work with.
- How do you generally prefer?

I have to deploy for the office IE as all Chinese governmental websites requires so, and I do this sololy for these sites, because no other websites that we *have to* access *require* Internet Explorer. They are: foreign expert working in China registration site, web site mandantory registertion site (that gives your website a license like a car licese), labor registration website, tax office website and all other public service website offered by Beijing and China government. (I treat you roasted duck in &#20415;&#23452;&#22346; if you found a single public service website of Beijing / Chinese government that involve web form processing AND works with anything other than IE. I am really curious to know one. The only one really worked with non-IEs so far from the government is the national defence, which do not offer any public service.)

Once deployed, it is difficult to change, thus I want to be careful, more people feeding back testing result helps! I also believe many people would come from google to visit feedback on this thread.

---

### Post by zhangweiwu on 2009-11-09
I provide my feedback first. A pilot deployement of ie4lin and Ubuntu 9.04 (updated to the latest, 2 hours ago) suffers from high CPU usage.

wine-server at 50% and IEXPLORER.EXE at 40% averagely, xorg 30%, taking up together 120%, from top(1). The computer is Intel duel-core at 1.73GHz. The CPU usage reproducibly goes higher and higher and crash the machine after about 1 hour.

---

### Post by PaulInBHC on 2009-11-09
I read a thread like this one

[http://ubuntuforums.org/showthread.php?t=1293122&highlight=ies4linux](http://ubuntuforums.org/showthread.php?t=1293122&highlight=ies4linux)

or search for ies4linux

You must have the cabs installed. ies4linux was very slow on my system but did work from a terminal command.

---

### Post by zhangweiwu on 2009-11-09
Perhaps I wasn't clear on my first feedback post.

- I can install wine successfully
- I can install ie4lin successfully
- I also run it successfully, and use it for googling etc OK
- And PC become very slow, after 1 hour opening IE while working on daily office documents, it freezes. The load keep going up.

So I guess I am not missing any cab file, right?

---

### Post by PaulInBHC on 2009-11-10
Correct, you have cab, wine, and ies4linux installed. Yes, it is very slow. Sorry, no better solution.

Edit, maybe try Sun Virtual Box to run windows on Ubuntu, but you need windows install disc.

---

### Post by zhangweiwu on 2009-11-10
I provide my second feedback:

A pilot deployement of cross-over linux professional 8.00 and Ubuntu 9.04 (updated to the latest, 8 hours ago) suffers from high CPU usage.

In the beginning cpu usage is lower than that of ie4lin, 2 hour later the computer 'crashed', hardly possible to move mouse button thus require a hardware reset. The computer is Intel duel-core at 1.73GHz. The user is working on the computer all the time during this, mostly editing openoffice documents and using thunderbird. After reset I do not try to start IE and she uses the computer for a whole afternoon without any problem. She also reports no 'crash' problem happened before, until I try get IE running.

---

### Post by MelDJ on 2009-11-10
i would say install through xp in virtualbox

---

### Post by zhangweiwu on 2009-11-10
Right. Virtual box with IE would be my last resort. It is not preferred because this is done as part of Linux deployement plan of the office, with the goal to *dump* windows, thus enclosing Windows would sound silly and make people question the reason to launch the project (if Win.. were not replaciable, why do you do it?)

I provide my 3rd feedback. With Ubuntu 9.10 and ie4lin, after running it for 1 hour, I was luck enough to be able to save the computer from crashing by, at the edge of crushing, killed wineserver that occupied 800MB memory. It started small though. Note that user closed IE, the only Windows application, in 30 minutes and winserver keep growing memory size until it almost crash the computer in 1 hour. I guess I hit the same situation as [http://ubuntuforums.org/archive/index.php/t-1006367.html](http://ubuntuforums.org/archive/index.php/t-1006367.html) with my wine-1.0.1-0ubuntu8

I was thinking of setting /etc/security/limits.conf to prevent any process taking more than 50% memory. This should be safe because I observed on this 1GB-physical-memory notebook firefox at maximum takes less than 30% memory and no other application uses higher memory than firefox. If only I knew how to set /etc/security/limits.conf. Need manual digging.

---


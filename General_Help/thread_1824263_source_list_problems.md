---
title: "source list problems"
date: 2011-08-13
forum: General Help
---

### Post by beacon on 2011-08-13
I don't know what I have done, but suddenly I am unable to use synaptic package manager and can't do much else. When I log in I get the following message: 

An Error Occurred
E: Type ‘Uncomment’ is not known on line 40 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report.

I have read posts all day and tried a number of things, including a re-install and can get nowhere. Please can someone help.

---

### Post by haqking on 2011-08-13
> **beacon said:**
> I don't know what I have done, but suddenly I am unable to use synaptic package manager and can't do much else. When I log in I get the following message: 

An Error Occurred
E: Type ‘Uncomment’ is not known on line 40 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report.

I have read posts all day and tried a number of things, including a re-install and can get nowhere. Please can someone help.

can you post your sources.list file so we can see what problem is

---

### Post by TeoBigusGeekus on 2011-08-13
```
gksu gedit /etc/apt/sources.list
```
Post us line 40.

---

### Post by beacon on 2011-08-13
Thanks for the quick responses. They have helped to calm me down. I am using Natty and get the following when I ask for the list. I have underlined line 40:
[LEFT] 


# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007.1)]/ maverick main restricted[/LEFT]
            [LEFT]deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty main restricted[/LEFT]
    [LEFT]deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty main restricted[/LEFT]
        [LEFT]## Major bug fix updates produced after the final release of the[/LEFT]
    [LEFT]## distribution.[/LEFT]
    [LEFT]deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates main restricted[/LEFT]
    [LEFT]deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates main restricted[/LEFT]
        [LEFT]## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu[/LEFT]
    [LEFT]## team. Also, please note that software in universe WILL NOT receive any[/LEFT]
    [LEFT]## review or updates from the Ubuntu security team.[/LEFT]
    [LEFT]deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty universe[/LEFT]
    [LEFT]deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty universe[/LEFT]
    [LEFT]deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates universe[/LEFT]
    [LEFT]deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates universe[/LEFT]
        [LEFT]## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu [/LEFT]
    [LEFT]## team, and may not be under a free licence. Please satisfy yourself as to [/LEFT]
    [LEFT]## your rights to use the software. Also, please note that software in [/LEFT]
    [LEFT]## multiverse WILL NOT receive any review or updates from the Ubuntu[/LEFT]
    [LEFT]## security team.[/LEFT]
    [LEFT]deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty multiverse[/LEFT]
    [LEFT]deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty multiverse
[/LEFT]
    [LEFT]deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates multiverse[/LEFT]
    [LEFT]deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates multiverse[/LEFT]
        [LEFT]_## Uncomment the following two lines to add software from the 'backports'_[/LEFT]
    [LEFT]## repository.[/LEFT]
    [LEFT]## N.B. software from this repository may not have been tested as[/LEFT]
    [LEFT]## extensively as that contained in the main release, although it includes[/LEFT]
    [LEFT]## newer versions of some applications which may provide useful features.[/LEFT]
    [LEFT]## Also, please note that software in backports WILL NOT receive any review[/LEFT]
    [LEFT]## or updates from the Ubuntu security team.[/LEFT]
    [LEFT]# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse[/LEFT]
    [LEFT]# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse[/LEFT]
        [LEFT] Uncomment the following two lines to add software from Canonical's[/LEFT]
    [LEFT]'partner' repository.[/LEFT]
    [LEFT] This software is not part of Ubuntu, but is offered by Canonical and the[/LEFT]
    [LEFT]## respective vendors as a service to Ubuntu users.[/LEFT]
    [LEFT]## deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner[/LEFT]
    [LEFT]# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner[/LEFT]
        [LEFT]## This software is not part of Ubuntu, but is offered by third-party[/LEFT]
    [LEFT]## developers who want to ship their latest software.[/LEFT]
    [LEFT]# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main[/LEFT]
        [LEFT]deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted[/LEFT]
    [LEFT]deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted[/LEFT]
    [LEFT]deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe[/LEFT]
    [LEFT]deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe[/LEFT]
    [LEFT]deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse[/LEFT]
    [LEFT]deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse[/LEFT]
        [LEFT]


[/LEFT]

---

### Post by TeoBigusGeekus on 2011-08-13
> Uncomment the following two lines to add software from Canonical's
'partner' repository.
 This software is not part of Ubuntu, but is offered by Canonical and the

Change this to

> ##Uncomment the following two lines to add software from Canonical's
##'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the

The 40th line is not what you've underlined; it's further down.

---

### Post by beacon on 2011-08-13
Thanks very much. I have done as you said, and now I get a message that there is a problem with line 58. However, according to the line counter in the bottom right-hand corner, line 56 is the last.

---

### Post by beacon on 2011-08-13
I thought I would just paste the latest message in case it helps.

                       [LEFT]E: Type &#8216;sudo&#8217; is not known on line 58 in source list /etc/apt/sources.list[/LEFT]
    [LEFT]E: The list of sources could not be read.[/LEFT]
    [LEFT]Go to the repository dialogue to correct the problem.[/LEFT]
    [LEFT]E: _cache->open() failed, please report.[/LEFT]

---

### Post by Elfy on 2011-08-13
The only lines in your source list without a # should start deb or deb-src.

Edit the file so that that is all you have #, deb or deb-src

Though you must have done something after post #4 here as there's no sudo in there :)

---

### Post by TeoBigusGeekus on 2011-08-13
> **forestpiskie said:**
> The only lines in your source list without a # should start deb or deb-src.

Edit the file so that that is all you have #, deb or deb-src

Though you must have done something after post #4 here as there's no sudo in there :)
This.

Can you please post the file again?

---

### Post by beacon on 2011-08-14
I got too tired and left the problem overnight, which accounts for the delay in a further response. I thank all of you for your messages. They were quick and very helpful. 

Following the suggestions of Forestpiskie the problem seems to have been solved. it was correct to say that there was another line. There was a space at the bottom before another line 'sudo apt-get update' which I missed; and that was line 58 which I eliminated, and things now seem to work properly. 

I'm not sure I understand yet about 'comment' and 'uncomment' or the difference between one # and two. I'll do what I can to find out now.

Again, many thanks.

---

### Post by Elfy on 2011-08-14
comment = with #

uncomment = without #

---

### Post by beacon on 2011-08-14
Thanks again forestpixie.

beacon

---


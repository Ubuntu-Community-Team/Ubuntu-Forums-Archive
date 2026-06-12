---
title: "Google Chrome downloading problems"
date: 2012-06-02
forum: General Help
---

### Post by Dragyrn1456 on 2012-06-02
Greetings fellow humans who probably know what to do better than I.

I just installed Ubuntu 12.04, and I was attempting to download Google Chrome, but every time I select a package, it goes to the thank you page and nothing happens. When I click on retry, it says:

> /tmp could not be saved, because an unknown error occurred.

Try saving to a different location.I've set up Firefox to ask me where to download things, but nothing else comes up, besides a blank window that closes after a second or two. What am I/Google doing wrong?

---

### Post by mörgæs on 2012-06-03
Why do you want Chrome and not Chromium?

---

### Post by vasa1 on 2012-06-03
> **mörgæs said:**
> Why do you want Chrome and not Chromium?

Re. OPs problem: ...
 Could it be that OP has some adblocker or NoScript running that prevents Chrome from being downloaded? I wonder if OP would have problems trying to download Chrome when Firefox is run in safe mode with all add-ons temporarily disabled?

Slightly off-topic, but many people want the latest and greatest Chromium but there seems to be [some issues]("http://askubuntu.com/questions/105102/does-someone-know-why-the-chromium-daily-package-isnt-build-anymore").

So for people who want the latest Chromium builds, where would they get it from?
(I'm happy with Chrome.)

---

### Post by mörgæs on 2012-06-03
I'm asking because often people have heard of Chrome but are unaware of Chromium.

I have not tried installing the daily build of Chromium myself, just the regular version:

```
sudo apt-get install chromium-browser
```

---

### Post by vasa1 on 2012-06-03
> **mörgæs said:**
> I'm asking because often people have heard of Chrome but are unaware of Chromium.

I have not tried installing the daily build of Chromium myself, just the regular version:

```
sudo apt-get install chromium-browser
```

Using that code with -s, we get:
```
 apt-get install -s chromium-browser
NOTE: This is only a simulation!
      apt-get needs root privileges for real execution.
      Keep also in mind that locking is deactivated,
      so don't depend on the relevance to the real current situation!
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  chromium-browser-l10n chromium-codecs-ffmpeg
The following NEW packages will be installed:
  chromium-browser chromium-browser-l10n chromium-codecs-ffmpeg
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Inst chromium-codecs-ffmpeg (18.0.1025.151~r130497-0ubuntu1 Ubuntu:12.04/precise [i386]) []
Inst chromium-browser (18.0.1025.151~r130497-0ubuntu1 Ubuntu:12.04/precise [i386])
Inst chromium-browser-l10n (18.0.1025.151~r130497-0ubuntu1 Ubuntu:12.04/precise [all])
Conf chromium-codecs-ffmpeg (18.0.1025.151~r130497-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf chromium-browser (18.0.1025.151~r130497-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf chromium-browser-l10n (18.0.1025.151~r130497-0ubuntu1 Ubuntu:12.04/precise [all])

```In other words, Chromium is one version behind. Chrome is at v 19.

And, from what I understand, Google targets Chromium at developers and testers who try the latest builds and provide data back to Google to build a better Chrome.

---

### Post by Dragyrn1456 on 2012-06-06
SO NOW

I've since figured out the problem, Firefox wouldn't download the file because  nothing could download anything on my system at the time. Something was wrong with my hard drive, and I'm currently getting it replaced. 

To those of you asking why I don't use Chromium, I once used Chromium, and as said, it seems to be more of a testing browser than anything else, and I also have no clue as to if Chromium accesses my account browser settings for Chrome.

Thanks for being here :D

---

### Post by Kr0nZ on 2012-06-06
Have you tried the latest chromium?
I was a google-chrome fan, but since it hasnt been included in the repos in 12.04 I gave chromium a try, and its pretty much identical to google-chrome.
All my addons and games that I had in google-chrome still work great in chromium.

---

### Post by Dragyrn1456 on 2012-06-06
To be honest I haven't used Ubuntu for very long, I had a problem with Windows (Also due to my hard drive), so I went in and wiped it and installed 12.04. The problem came up a half hour later, and then the next day Ubuntu wouldn't load. I'll try out Chromium (Giving into peer pressure FTW), but I'm still a teeny bit skeptical.

Quick question, can you get your account settings in Chromium, or do you need to find all of your addons all over again?

---

### Post by Kr0nZ on 2012-06-06
Yes account settings work in chromium,
In 10.10 I was using google chrome, had it setup with addons, bookmarks, history, games, apps... etc
then when I installed chromium on 12.04 it was all there, I never had to reinstall a single thing.
It was a fresh install of 12.04 so I wasn't reusing my home partition.

---

### Post by Dragyrn1456 on 2012-06-06
Alright, I'll give that a look. Thanks for the suggestion.

---


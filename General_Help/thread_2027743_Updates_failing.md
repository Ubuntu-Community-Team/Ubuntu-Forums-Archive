---
title: "Updates failing"
date: 2012-07-16
forum: General Help
---

### Post by brad1138 on 2012-07-16
For the last week and a half I have been getting this message when running update manager;

[IMG]http://i544.photobucket.com/albums/hh359/brad3d/Screenshotfrom2012-07-16192137.png[/IMG]

Seems a bit long for a server to be down, anyone else getting this message?

---

### Post by Dngrsone on 2012-07-16
Try opening a terminal and entering the following:

```
sudo apt-get update
```

You will have to enter your password.  After it has finished updating, try running Update again.

---

### Post by brad1138 on 2012-07-17
> **Dngrsone said:**
> Try opening a terminal and entering the following:

```
sudo apt-get update
```

You will have to enter your password.  After it has finished updating, try running Update again.

Thanks,

OK, did that, still get same error.

---

### Post by jmfal on 2012-07-17
In the Update Center>> Other software tab >> Remove checks from lines wait a few seconds and put checks back, leaving top two for CD empty.

Then try to update.

---

### Post by claracc on 2012-07-17
It seems this ppa artfwo is not supported in 12.04 : [https://answers.launchpad.net/ubuntu/+source/indicator-cpufreq/+question/197732](https://answers.launchpad.net/ubuntu/+source/indicator-cpufreq/+question/197732), so better you remove it from sources.list

---

### Post by brad1138 on 2012-07-17
> **claracc said:**
> It seems this ppa artfwo is not supported in 12.04 : [https://answers.launchpad.net/ubuntu/+source/indicator-cpufreq/+question/197732](https://answers.launchpad.net/ubuntu/+source/indicator-cpufreq/+question/197732), so better you remove it from sources.list

Thank you, I will. Although just like one of the posters in that link, I wonder why it all the sudden stopped working. I too have a clean install of 12.04. Why were they added in the first place and why did they all of the sudden stop working last week?

I guess I don't really care, now that I have the answer, but it is curious. 

Brad

---


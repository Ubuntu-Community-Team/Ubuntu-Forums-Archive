---
title: "Fire fox opening multiple windows"
date: 2010-02-18
forum: General Help
---

### Post by denzykabzy on 2010-02-18
Hi there guys.
Im having a problem with firefox that I hope someone could help me fix. I left firefox running overnight  yesterday only to wake up to a totally unresponsive karmic. Everything was frozen and i couldn't get anything to run. I restarted the ubuntu and everything seemed to be ok until I tried to open firefox. Almost immediatly the first window opened it was followed by what looked like fifty more. It kept opening windows until ubuntu crashed. I restarted karmic again and did a couple of google searches using opera and found out that it might be a adware problem. Can anyone tell me where to begin fixing this problem? I have thought of getting rid of my cookies but i do not know whether that will help. I would like to have a permanent solution.
Thanks in advance
Denzykabzy

---

### Post by viralmeme on 2010-02-18
> **denzykabzy said:**
> .. Im having a problem with firefox that I hope someone could help me fi ..
The simplest solution is to delete the Firefox profile in your home directory, totally uninstall FF and then reinstall ..

---

### Post by wojox on 2010-02-18
Bleachbit is an option as well. It will clean up Firefox

```
sudo apt-get install bleachbit
```

Just don't check the Places or it'll delete all your bookmarks.

---

### Post by denzykabzy on 2010-02-18
Thanks alot guys. I ran clamtk and found that I had two viruses in my opera and firefox cache respectively. I quarantined and deleted them. Then I installed and ran bleach it and deleted whatever other cache files and cookes that were present in both. Everything seems to be running just fine now. If this problem reoccurs I'll have to uninstall and reinstall firefox . 
I would still like to know how something in the cache memory would cause firefox to behave so unpredictably.
Denzykabzy

---

### Post by driekus on 2010-02-18
Sorry to hijack your thread, but I also have a similar problem. It appears intermittent and makes firefox unusuable. 
The interesting difference is that when I do not have firefox open it causes multiple openings of the ubuntu help to the point that the system is unusable (100's of windows) The system has been running stably for 6 months now. 

I will run a virus scan tonight and see if that is a problem, not sure though.

---

### Post by denzykabzy on 2010-02-18
> **driekus said:**
> Sorry to hijack your thread, but I also have a similar problem. It appears intermittent and makes firefox unusuable. 
The interesting difference is that when I do not have firefox open it causes multiple openings of the ubuntu help to the point that the system is unusable (100's of windows) The system has been running stably for 6 months now. 

I will run a virus scan tonight and see if that is a problem, not sure though.

please let me know how things turn out with the scan. I would really like to know what is going on so that i can prevent it from happening again. Thanks for your post

---

### Post by lovinglinux on 2010-02-19
To prevent future problems, install [NoScript](https://addons.mozilla.org/en-US/firefox/addon/722).

---

### Post by viralmeme on 2010-02-19
> **denzykabzy said:**
> .. I would still like to know how something in the cache memory would cause firefox to behave so unpredictably.
Denzykabzy
So would I like to know. What exactly were these 'viruses', why the need to 'quarantine' or run 'bleach' on these files. Why nor just delete them.

---

### Post by denzykabzy on 2010-02-19
> **lovinglinux said:**
> To prevent future problems, install [NoScript]("https://addons.mozilla.org/en-US/firefox/addon/722").
Thanks alot lovinglinux realy appreciate the advice. Will get noscript ASAP.

---


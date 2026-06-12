---
title: "Software Center - No paid apps or reviews"
date: 2012-05-06
forum: General Help
---

### Post by T_W on 2012-05-06
Hello all,

I have a newly installed precise system and for some reason, Software Center is not showing any paid apps or reviews.  For example, multiwinia shows up in the banner, however if I click on it I get the message:  

> Not found
There isn’t a software package called “multiwinia” in your current software sources.

If I run Software Center from the command line I get the following:

```
2012-05-06 21:57:57,870 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'http://localhost:8080/'
2012-05-06 21:57:57,880 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2012-05-06 21:57:58,142 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2012-05-06 21:57:58,516 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
2012-05-06 21:57:58,643 - softwarecenter.backend.spawn_helper - WARNING - exit code 1 from helper for '['/usr/share/software-center/piston_generic_helper.py', '--datadir', '/usr/share/software-center/', 'RatingsAndReviewsAPI', 'review_stats']'
2012-05-06 21:57:58,643 - softwarecenter.backend.spawn_helper - WARNING - got error from helper: 'WARNING:__main__:connecting to http://reviews.ubuntu.com/reviews/api/1.0: 
'
2012-05-06 21:58:04,261 - softwarecenter.db.application - WARNING - no version information found for 'multiwinia'
2012-05-06 21:58:04,295 - softwarecenter.db.application - WARNING - no version information found for 'multiwinia'
2012-05-06 21:58:04,296 - softwarecenter.db.application - WARNING - no version information found for 'multiwinia'
2012-05-06 21:58:04,300 - softwarecenter.db.application - WARNING - no version information found for 'multiwinia'
2012-05-06 21:58:04,308 - softwarecenter.db.application - WARNING - no version information found for 'multiwinia'
2012-05-06 21:58:04,643 - softwarecenter.backend.spawn_helper - WARNING - exit code 1 from helper for '['/usr/share/software-center/piston_generic_helper.py', '--datadir', '/usr/share/software-center/', 'SoftwareCenterRecommenderAPI', 'recommend_app', '{"pkgname": "multiwinia"}']'
2012-05-06 21:58:04,644 - softwarecenter.backend.spawn_helper - WARNING - got error from helper: 'WARNING:__main__:connecting to https://rec.ubuntu.com/api/1.0: 
'
2012-05-06 21:58:04,644 - softwarecenter.db.categories - WARNING - Error while accessing the recommender service: WARNING:__main__:connecting to https://rec.ubuntu.com/api/1.0: 

2012-05-06 21:58:04,645 - softwarecenter.ui.gtk3.widgets.recommendations - WARNING - Error while accessing the recommender agent for the details view recommendations: WARNING:__main__:connecting to https://rec.ubuntu.com/api/1.0: 
```

If I use a **sudo** to run software-center then it **works** fine.

I have already tried to reinstall software-center and to delete my .cache/software-center and .config/software-center directories.

Any ideas?

---

### Post by ontaiwolf on 2012-06-02
Yep, same problem here. The USC cannot find the humble bundle packages

---

### Post by ts3 on 2012-06-02
> **ontaiwolf said:**
> Yep, same problem here. The USC cannot find the humble bundle packages

Had the same problem yesterday, updating the system fixes it.  I did it by running 

```
sudo apt-get update && sudo apt-get upgrade
```

Apt-get update by itself will probably be sufficient :)

---

### Post by ontaiwolf on 2012-06-02
No, it doesnt help. This could be probably a bug which should be fixed already but it isnt for me...

[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/982567](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/982567)

---

### Post by Frogs Hair on 2012-06-02
I received a software center upgrade via proposed updates and while the humble bundle is not in the repository it is advertised in top top pane with the web site address. I also that see software recommendations are optional and I don't know if this is new or not . This update may be included recommended updates soon.

---

### Post by ontaiwolf on 2012-06-02
Your Software Center ist fine. When I start mine I just see the orange screen with favorite apps or something but no new games or apps. Recommendations don't work for me too.

---


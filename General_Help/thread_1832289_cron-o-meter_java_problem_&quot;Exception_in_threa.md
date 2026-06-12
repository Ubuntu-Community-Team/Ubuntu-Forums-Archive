---
title: "cron-o-meter java problem &quot;Exception in thread &quot;TaskBar&quot;&quot;"
date: 2011-08-24
forum: General Help
---

### Post by interia on 2011-08-24
I am a newbie and am having problems succeeding with installing Cron-o-meter version 0.9.8 (the Mac OS zip) on Ubuntu 10.04 LTS. Not sure which Java version I am running and don't know how to find out either.

Launching the Cron-o-meter from the terminal results in the start-up screen coming up, but it never goes any further. The message in the terminal is:

"Exception in thread "TaskBar" java.lang.NullPointerException
    at ca.spaz.cron.datasource.JarXMLFoodDataSource.initialize(JarXMLFoodDataSource.java:24)
    at ca.spaz.cron.datasource.Datasources.initialize(Datasources.java:34)
    at ca.spaz.cron.CRONOMETER$SplashScreenTask.run(CRONOMETER.java:456)
    at ca.spaz.task.TaskBar$3.run(TaskBar.java:105)
    at java.lang.Thread.run(Thread.java:636)"

What am I missing?

---

### Post by Azdour on 2011-08-25
Hi,

Is the problem similar to this one that was reported some time ago:

[http://sourceforge.net/tracker/?func=detail&aid=2997404&group_id=136481&atid=735996](http://sourceforge.net/tracker/?func=detail&aid=2997404&group_id=136481&atid=735996)

Having looked at the sourcecode in v0.9.8.1 at line 24, I'm guessing that is looks like the map has not have been initialised, therefore calling map.size() results in the NullPointerException. Why the map is null maybe something to do with the food.index file not being found. When you run the application it only creates the map when it finds food.index, otherwise map remains null.

---

### Post by interia on 2011-08-25
Thank you for your reply and your explanation. My problem is identical to the one described in the link you posted. I come to the conclusion that the problem is due to the code and not my making any mistakes when installing?

---


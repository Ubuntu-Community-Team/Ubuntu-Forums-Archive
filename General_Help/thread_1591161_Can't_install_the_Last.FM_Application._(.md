---
title: "Can't install the Last.FM Application. :("
date: 2010-10-08
forum: General Help
---

### Post by TheNerdAL on 2010-10-08
So I got into Last.fm and I like it more than Pandora now and I would like to download the application but it says the dependencies don't work or something like that. :( Help. :( 

Thanks.

---

### Post by markh789 on 2010-10-08
What are the dependencies?

---

### Post by oldos2er on 2010-10-08
```
sudo apt-get update && sudo apt-get install lastfm
```

---

### Post by hrickh on 2010-10-08
> **TheNerdAL said:**
> So I got into Last.fm and I like it more than Pandora now and I would like to download the application but it says the dependencies don't work or something like that. :( Help. :( 

Thanks.
WTF is "something like that"?

Seriously, you have 830 "beans" and have been around here for a year. You should know how to explain yourself by now.

R.
==

---

### Post by TheNerdAL on 2010-10-09
> **oldos2er said:**
> ```
sudo apt-get update && sudo apt-get install lastfm
```

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 lastfm : Depends: libqt4-sql (>= 4:4.5.3) but it is not installable
E: Broken packages

```

---

### Post by oldos2er on 2010-10-09
You do have all repositories enabled? libqt4-sql is in the main repository, so I'm not sure why you're getting that error. Or you can get it here: [http://packages.ubuntu.com/maverick/libqt4-sql](http://packages.ubuntu.com/maverick/libqt4-sql)

---

### Post by TheNerdAL on 2010-10-09
> **oldos2er said:**
> You do have all repositories enabled? libqt4-sql is in the main repository, so I'm not sure why you're getting that error. Or you can get it here: [http://packages.ubuntu.com/maverick/libqt4-sql](http://packages.ubuntu.com/maverick/libqt4-sql)

How do I enable them?

---

### Post by oldos2er on 2010-10-09
Open Synaptic, Settings, Repositories, make sure all the boxes are checked.

---

### Post by TheNerdAL on 2010-10-09
> **oldos2er said:**
> Open Synaptic, Settings, Repositories, make sure all the boxes are checked.

That worked! Thanks! :D

---


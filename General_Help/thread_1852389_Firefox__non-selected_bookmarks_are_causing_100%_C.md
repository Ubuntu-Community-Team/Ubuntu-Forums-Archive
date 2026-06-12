---
title: "Firefox:  non-selected bookmarks are causing 100% CPU!"
date: 2011-09-30
forum: General Help
---

### Post by held7over on 2011-09-30
Ubuntu 10.10  Firefox 3.6.23

Trying to look at web pages or to down load something, say a picture or two, or even clicking on a menu item or QUIT causes Firefox to alternately use 100% CPU for extended lengths of time.....leaving the browswer unusable while virtually no internet access activity is happening at all!

If I create a new firefox profile and launch firefox everything is fine. However, if I then copy my bookmarks database ( places.sqlite ) from my old profile to my new profile and launch firefox, the problem is transferred to my new firefox instance. I don't have to activate a single bookmark for this problem to start happening while I am trying to work with firefox. It even happens if firefox is just setting there doing nothing!

I have a ton of bookmarks! I hate to just throw them all away. Does anyone have an idea how to figure out which bookmark is causing the problem or do you think this is some kind of bug with firefox scripting for the sqlite database itself and really has nothing to do with the bookmarks?

Thanks for your thoughts! :P

---

### Post by An Sanct on 2011-09-30
I had such problems when accessing really huge homepages in japanese and/or russian, the UTF8 massive pages killed the whole browser. I'm talking *really large* pages here, whole threads of certain forums etc. (like hundreds of A4 pages of UTF8 japanese).

Also note, that certain scripts "run in circles". You are given a choice to stop those scripts after a while, but normally people do not wait that long.

My suggestion would be, to use NoScript along with AdBlockPlus.

---

### Post by lovinglinux on 2011-09-30
> **held7over said:**
> Ubuntu 10.10  Firefox 3.6.23

Trying to look at web pages or to down load something, say a picture or two, or even clicking on a menu item or QUIT causes Firefox to alternately use 100% CPU for extended lengths of time.....leaving the browswer unusable while virtually no internet access activity is happening at all!

If I create a new firefox profile and launch firefox everything is fine. However, if I then copy my bookmarks database ( places.sqlite ) from my old profile to my new profile and launch firefox, the problem is transferred to my new firefox instance. I don't have to activate a single bookmark for this problem to start happening while I am trying to work with firefox. It even happens if firefox is just setting there doing nothing!

I have a ton of bookmarks! I hate to just throw them all away. Does anyone have an idea how to figure out which bookmark is causing the problem or do you think this is some kind of bug with firefox scripting for the sqlite database itself and really has nothing to do with the bookmarks?

Thanks for your thoughts! :P


Most likely that your *places.sqlite* is full of left overs and need to be optimized. There a few add-ons that can do that, but I prefer to use sqlite3 from command line, since it can optimize all databases. 

The commands would be:

```
sudo apt-get install sqlite3
```

```
sqlite3 $HOME/.mozilla/firefox/yourprofile/places.sqlite "vacuum"
```

Don't forget to replace *yourprofile* with the profile folder name.

For more info and a script, see [http://www.webgapps.org/tutorials/firefox/optimization/database-optimization](http://www.webgapps.org/tutorials/firefox/optimization/database-optimization)

---

### Post by An Sanct on 2011-09-30
> **lovinglinux said:**
> Don't forget to replace *yourprofile* with the profile folder name.

Also don't forget to make a backup first, in case anything goes wrong. ;)

---

### Post by held7over on 2011-10-01
An Sanct  --  When I mentioned scripts, I meant the firefox programming itself might have a bug somewhere in the coding causing this...(but probably not).  The problem happens even without surfing the web while it is just setting there.


lovinglinux -- The sqlite3 command, didn't change anything that I can tell. The problem persists.

---

### Post by lovinglinux on 2011-10-01
> **held7over said:**
> An Sanct  --  When I mentioned scripts, I meant the firefox programming itself might have a bug somewhere in the coding causing this...(but probably not).  The problem happens even without surfing the web while it is just setting there.


lovinglinux -- The sqlite3 command, didn't change anything that I can tell. The problem persists.

Make a backup of *places.sqlite*, export your bookmarks to html using the Bookmark Manager, close Firefox, delete the file *places.sqlite*, import the html file.

---

### Post by held7over on 2011-10-01
WOW! Firefox is blazingly fast again! 

Thanks lovinglinux! That seems to have purged whatever the problem was.

---

### Post by lovinglinux on 2011-10-01
> **held7over said:**
> WOW! Firefox is blazingly fast again! 

Thanks lovinglinux! That seems to have purged whatever the problem was.

You are welcome.

---

### Post by held7over on 2011-10-01
Any idea what could have possible been wrong with my original sqlite bookmark database, that converting the contents to html and then back to sqlite would have purged out??

---

### Post by lovinglinux on 2011-10-02
> **held7over said:**
> Any idea what could have possible been wrong with my original sqlite bookmark database, that converting the contents to html and then back to sqlite would have purged out??

I am not sure, but I have noticed this problem in some user profiles after upgrading Firefox to 6 or 7. Exporting an importing makes sure that only useful data is stored in the database.

---

### Post by cookiecruncher on 2012-02-11
I deleted the entire 'firefox' directory under '.mozilla', downloaded the latest Firefox (10.0), extracted the Firefox contents back into .mozilla and still the cpu usage after quitting Firefox is 100% on one of the cores, ie. without importing any bookmarks, etc. yet.  Unable to sort out this problem. :(

---


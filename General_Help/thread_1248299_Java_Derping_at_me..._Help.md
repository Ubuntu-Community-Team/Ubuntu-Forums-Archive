---
title: "Java Derping at me... Help?"
date: 2009-08-24
forum: General Help
---

### Post by Xavier Aliatos on 2009-08-24
Alright, so I've recently started using Jaunty Jackalope, and I've been okay figuring out how stuff is starting to work. The only thing I'm having trouble with, is getting java to work!
I've tried all the different stuff I've seen on other forums, but nothing works.

Main attempts to use Java include [http://www.whirled.com](http://www.whirled.com) and the Deviantart Chat Client: dAmn ( [http://chat.deviantart.com](http://chat.deviantart.com) )

[U][B]Newbie can haz advice please?

EDIT: Fri, Aug, 28, 12:05 am
[/B][/U]
dAmn now works for me, and I have no clue why. It just started working all of a sudden a few days ago. Now the problem is with whirled.
They think it may be a linux-related bug, so I'm asking their bug-hunting team for help. If or when I get an update, I'll post it here.

---

### Post by credobyte on 2009-08-24
In Terminal:
```
 
sudo apt-get install sun-java6-jre sun-java6-plugin

```

---

### Post by Xavier Aliatos on 2009-08-24
Alright, I've done so. It's installed as far as I know. The only problem is, when I use either of the sites I mentioned, nothing will load. With Whirled, it just stays blank, and with deviantart (well I don't know if its java or just the site's chat itself being a derp) it says it's unable to find a suitable java plugin.

---

### Post by kpkeerthi on 2009-08-24
Check your Java plugin by visiting [Do I have Java?]("http://www.java.com/en/download/installed.jsp?detect=jre&try=1")

---

### Post by Xavier Aliatos on 2009-08-25
Alright, it says I don't have java, even though I went through all the steps up until the end of the configuring section.
I can run most things: newgrounds, youtube, dAmn; but it still says I don't have java?
Is this an issue?

Also, Whirled still refuses to even load the actual flash movie that is the virtual world. Kind of a problem as well...

---

### Post by Mighty_Joe on 2009-08-25
You may need to tell Ubuntu which Java version to use via update-java-alternatives: [see here]("https://help.ubuntu.com/community/Java")

---

### Post by skixx on 2009-08-25
> **credobyte said:**
> In Terminal:
```
 
sudo apt-get install sun-java6-jre sun-java6-plugin

```


This works great for me thanks

---

### Post by Manyette on 2009-08-26
I believe I have just discovered the meaning of "derp".  A couple of months ago I installed java on this machine from the command line with no problems whatsoever.  Now, after a reinstall, I cannot get it to load at all, just like the posts above. I get to the configure screen (shown) and there it hangs indefinitely  No displayed errors up to this point.  Multiple tries.  Machine has all current updates.  I have to believe something in this download is hosed (or derped).  I have also tried the add/remove programs with similar dismal results.

---

### Post by kpkeerthi on 2009-08-27
> **Manyette said:**
> I get to the configure screen (shown) and there it hangs indefinitely  No displayed errors up to this point.  Multiple tries.  Machine has all current updates.  I have to believe something in this download is hosed (or derped).  I have also tried the add/remove programs with similar dismal results.
Accept the license by selecting the <OK> button (use tab key and press <enter>)

---

### Post by Manyette on 2009-08-27
If it wasn't obvious from my comments, the button was inactive, and pressing it did nothing.  It was hung at that point, and the <OK> did nothing at all.  Although the system monitor said there was a process still running, there was NO processor activity for half an hour on the last try.

---

### Post by kpkeerthi on 2009-08-28
I guess the button enables when you are at the bottom of the page. But I'm not sure.

---

### Post by Xavier Aliatos on 2009-08-28
> **Mighty_Joe said:**
> You may need to tell Ubuntu which Java version to use via update-java-alternatives: [see here]("https://help.ubuntu.com/community/Java")
Thanks for the help, I'll make sure to keep that handy tip in mind... But I said for it to use it already... I think the issue is in firefox. I check the plugins (about : plugins without the spaces), and it says I'm using sun java version 6 update 14.
How do I set it?
(Also, I think I screwed up big time... Java's site told me to do sum shiz as root, and I think I made it impossible for me to use the jre1.6.0_15 folder as I'm only the administrator........)

---

### Post by Xavier Aliatos on 2009-08-28
Woah... wtf...?
I just checked java's page, to check whether or not I have the reccomended java update:
It says I have update 14. It reccomends I download update 14.
I think my brain just stopped trying to figure out just who it is that's failing here...

---

### Post by P4man on 2009-08-28
try this. Go to system > preferences > Sun Java control center

On the first tab, temporary internet files, go settings, and delete them.
On the second tab, verify for both user and system you have an entry for 1.6 and its enabled.
On the third tab look at the certificates. For "user" there might be a trusted certificate for webex. Id say delete it (it will ask you again). Also check for system, if you select "signer CA" there should be a whole bunch of certificates. keep them!

Then try again..

---


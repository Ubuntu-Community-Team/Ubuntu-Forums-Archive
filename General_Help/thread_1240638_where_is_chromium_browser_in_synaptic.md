---
title: "where is chromium browser in synaptic"
date: 2009-08-14
forum: General Help
---

### Post by bu2971x on 2009-08-14
I cant find it in the repos...

---

### Post by ad_267 on 2009-08-14
You have to add the Chromium PPA (Personal package archive).

The PPA is here: [https://launchpad.net/~chromium-daily/+archive/ppa](https://launchpad.net/~chromium-daily/+archive/ppa)

There are instructions on that page under "read about installing"

---

### Post by bu2971x on 2009-08-14
I did all that before.....have all the stuff    how to get the actual browser????????????

---

### Post by aysiu on 2009-08-14
> **bu2971x said:**
> I did all that before.....have all the stuff    how to get the actual browser????????????
Follow these directions:
[How to Install Chromium Daily Builds in Ubuntu](http://www.psychocats.net/ubuntucat/chromium/)

---

### Post by bu2971x on 2009-08-14
did all that   went ok    still no chromium in synaptic    those directions are Bogus.............

---

### Post by aysiu on 2009-08-14
> **bu2971x said:**
> did all that   went ok    still no chromium in synaptic    those directions are Bogus.............
Those directions aren't bogus. I wrote them myself and took all the screenshots.

Believe me. I'm no GIMP or Photoshop wizard. I can't just make that stuff up.

You pasted in the repositories. Did you click Reload?

Can you paste these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal) and then paste the output back here? ```
cat /etc/apt/sources.list
sudo apt-get update
apt-cache search chromium
```

---

### Post by fragos on 2009-08-15
I took a different approach. First install ubuntu-tweak. Run it and select Applications-> 3rd party. In that list you'll find the repo for the Chromium browser. To check it you need to unlock with your user password. The next time you run ubuntu-tweak, Applications-> Add/Remove will offer the Chromium browser. Chromium is updated daily and will now be available with the Update Manager.

---

### Post by fooman on 2009-08-15
> **bu2971x said:**
> did all that   went ok    still no chromium in synaptic    those directions are Bogus.............

if you added the repos like in the guide...then it should be in synaptic.

btw...its chromium-*browser* that you should search for in synaptic....*chromium* is a space shooting game.  although searching for chromium should produce both the game and the browser in the results.

try it from command line...open a terminal and type or copy/paste the following:

```
sudo apt-get update && sudo apt-get install chromium-browser
```if you get any errors...post them back here.

hope that helps.

---

### Post by gradinaruvasile on 2009-08-15
Or just download the latest build from their buildbot...
Launch the script i attached... It will install the latest buildbot version for u.

---

### Post by martini1179 on 2009-08-18
To tell you the truth, I'm having the same problem. I'm still a Linux/Ubuntu noob, but I know how to get things from a ppa, and I've been able to get all of my ppa's up and running, EXCEPT Chromium.  

This issue could be the result of something happening withing the last few weeks. I had Chromium from the Chromium daily ppa running perfectly on my Wubi install, but two weeks later I wipe that drive and install Ubuntu proper and Chromium doesn't show up in synaptic. 

The OP should try running

```
sudo apt-get install chromium-browser
```

even though it doesn't show up in synaptic. If I remember that's what I did and it worked. No telling whether or not this bug will prevent chromium-browser from showing up in the update manager :(

---

### Post by aysiu on 2009-08-18
The only thing I can think of is perhaps you're using the Quick Search field in Synaptic instead of clicking the Search button.

Sometimes it takes a while for new things to show up in the Quick Search field.

---

### Post by martini1179 on 2009-08-18
> **aysiu said:**
> The only thing I can think of is perhaps you're using the Quick Search field in Synaptic instead of clicking the Search button.

Sometimes it takes a while for new things to show up in the Quick Search field.

Exactly right. I was using the quick search field -- which hadn't failed me for the last 4 months -- and it wasn't showing up. Using the search button (or control-F), picked it up. 

Thanks for solving that minor mystery. I think the OP's complaint will be addressed as well.

---

### Post by petjakob on 2009-10-22
that command worked for me after doing everything and still no option in synaptic. WOOT!

---


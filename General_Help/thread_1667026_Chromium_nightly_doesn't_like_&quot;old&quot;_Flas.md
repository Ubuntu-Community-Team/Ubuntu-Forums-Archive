---
title: "Chromium nightly doesn't like &quot;old&quot; Flash"
date: 2011-01-14
forum: General Help
---

### Post by olwe on 2011-01-14
I've got Chromium set up for nightly build updating on my 10.04 and I do run Update Manager daily. Lately, I get the message "The Flash plug-in was blocked because it is out of date." It gives me the option to "Run this time" or "Update plug-in." Is this a Chromium nightly build "to be expected" problem, or should I truly try to update Flash? If it's Flash that needs updating, what should I add to my Software Sources to get this newer Flash that I'm not getting normally?

---

### Post by pietro_spina on 2011-01-14
Do you remember how you previously installed flash? I did a manual installation of 64 bit 10.0flash so I suspect I need to load up the new version. But first we should look into what is current in the repos. I'll be back in a bit...

This link will tell you what you have...
[http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/)

---

### Post by olwe on 2011-01-14
Yeah, I got the repo lines from some "Post 10.04 Install" site and just plugged them in (Software Sources/Other Software etc.). I do wish there was only one "The Official Post-Install," or, even better, no need for post-install weirdness....

---

### Post by olwe on 2011-01-14
Yeah, I got the repo line(s) from a "Post-Install" site.

---

### Post by olwe on 2011-01-14
Yeah, I got the repo line(s) from a "Post-Install" site.

---

### Post by olwe on 2011-01-14
Yeah, I got the repo line(s) from a "Post-Install" site.

---

### Post by pietro_spina on 2011-01-14
Well, this is the thread I used before to install 64 bit flash and it seems to be up to date.
[http://ubuntuforums.org/showthread.php?t=1358591](http://ubuntuforums.org/showthread.php?t=1358591)

If you don't need/want 64 bit you can just use the standard Ubuntu repos.

I also came across this PPA that says it has the current 64 bit previews... If PPA's are your cup of tea.
[https://launchpad.net/~sevenmachines/+archive/flash/+packages](https://launchpad.net/~sevenmachines/+archive/flash/+packages)

I'll report back if success or failure.
-p

---

### Post by pietro_spina on 2011-01-14
[http://ubuntuforums.org/showthread.php?t=1358591](http://ubuntuforums.org/showthread.php?t=1358591)
I used the script from the above thread.

I am now running 10,3,169,29 per
[http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/)

No warnings from chromium... and I tested flash on a couple of sites including watching PART of a Taylor Swift video... and my computer did not blow up. uses about a third of my processor when windowed and 50% when full screen. 

If it matters....
AMD Phenom II X3 2.6GHz 
GeForce 9500 GT

---


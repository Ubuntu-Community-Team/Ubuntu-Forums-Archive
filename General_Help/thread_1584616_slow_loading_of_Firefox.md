---
title: "slow loading of Firefox ???"
date: 2010-09-29
forum: General Help
---

### Post by wpshooter on 2010-09-29
Why is it that the latest versions of Firefox being utilized with Ubuntu/Jaunty are so slow in completing the loading process ?

Thanks.

---

### Post by jtweaker on 2010-09-29
do you have plugins and other extension in your firefox? these things can really slow down firefox and if you're using the latest release, chances are there are still compatibility issues that needs to be addressed by the plugin and extension developers.

---

### Post by lovinglinux on 2010-09-29
Firefox startup is not slow. If you start a clean FF user profile you will see that it is almost instant. The problem should be on your user profile. 

If you have many extensions, then most likely they will slow down your Firefox startup. All enabled extensions needs to be loaded into memory before Firefox start. Extensions can include functions that are triggered when the browser loads them and these functions prevent Firefox from completely loading until they are finished.

For instance, my Firefox takes 700 milliseconds to fully load with a clean profile and 6403 with my user profile, which has about 60 extensions installed and more than 2000 bookmarks.

Unoptimized databases can also slow down Firefox startup. For example, if you start Firefox with the bookmarks sidebar open, then startup time could be reduced if your places.sqlite database is not optimized. Always avoid starting Firefox with the sidebar open and optimize your databases frequently.

See Firefox [Database Optimization](http://firefox-tutorials.blogspot.com/2010/05/database-optimization.html) tutorial and [General Troubleshooting Steps](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) tutorial.

How long does it take for your Firefox to completely load? How long does it take if you use a clean profile?

To test it,  save the following code in your home as *startup.html* :

```
<!DOCTYPE HTML>
<html>
<body>
<script>
var t = (new Date()).getTime();
dump("TIME " + t + "\n");

var url = document.location.toString();
if (url.indexOf("#") != -1) {
  var h = url.substring(url.indexOf("#")+1);
  dump("ELAPSED " + (t - parseInt(h)) + "\n");
  document.write("<span>ELAPSED " + (t - parseInt(h)) + "</span>\n");
}
dump("-----------\n");
dump("KILL\n");
window.close();
</script>
</body>
</html>
```

Close Firefox and start it from a terminal using the command below:

```
firefox file:///home/**username**/startup.html#`python -c 'import time; print int(time.time() * 1000);'`
```

If you want to test a different profile then use this:

```

firefox -no-remote -P "**profilename**" file:///home/**username**/startup.html#`python -c 'import time; print int(time.time() * 1000);'`
```

You need to change the stuff in bold accordingly.

---

### Post by ron999 on 2010-09-29
That's a good test lovinglinux.
With my own profile:-
ELAPSED 6691
With a new profile:-
ELAPSED 1899

But 6.691 seconds isn't such a big deal.
I can live with that.:)

---

### Post by lovinglinux on 2010-09-29
> **ron999 said:**
> That's a good test lovinglinux.


It is a really nice test. Source at [https://wiki.mozilla.org/Firefox/Projects/StartupPerformance/MeasuringStartup](https://wiki.mozilla.org/Firefox/Projects/StartupPerformance/MeasuringStartup)

> **ron999 said:**
> 
With my own profile:-
ELAPSED 6691
With a new profile:-
ELAPSED 1899

But 6.691 seconds isn't such a big deal.
I can live with that.:)
I agree. Six seconds isn't a big deal.

---


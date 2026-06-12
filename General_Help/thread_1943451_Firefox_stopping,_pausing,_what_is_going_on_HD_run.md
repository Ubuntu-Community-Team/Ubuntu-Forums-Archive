---
title: "Firefox stopping, pausing, what is going on? HD running 100%"
date: 2012-03-19
forum: General Help
---

### Post by fixitdude on 2012-03-19
Has anyone figured out how to fix this? I am at a loss...

Really frustrating, when I first start up Firefox it will sit OK and you can let it sit there for a while, but if you start typing in a URL then the hard drive starts running like it's sorting a database and it goes on for a full 15 to 20 seconds!

You can't type anything while that is going on, and all browser functions are not accessible, total "pause".

Once it does this then it will not do it again until the next time I start it up. What is it doing? What wonderful database of whatever is so important that it can stop the browser?

I've tried to track it down but the only thing running at the time is Firefox as far as PS or top are concerned.

Tried clearing the cache, tried the "about:config" "network.dns.disableIPv6" set to true thing, no help.

It will do this from a fresh boot with nothing else going on at all, new browser window, nothing else.

Firefox 3.6.17, only plugins are Ad Block, No Script, cookie monster.

Another thing that is annoying is when I am scrolling a web page it will pause. I don't hear the hard drive running and the CPU is OK I checked it with gkrellm at the same time.

Anyone else seen this? It didn't used to do this, seems like it started 6 months ago when I may have upgraded to the latest Firefox from the repositories.

Even right now as I type this, I will be typing and it will pause even while I am still typing and then all of a sudden there's all the stuff I just typed, total pause again.

---

### Post by HiImTye on 2012-03-19
sounds like its swapping
how much memory do you have?

---

### Post by fixitdude on 2012-03-19
> **HiImTye said:**
> sounds like its swapping
how much memory do you have?I wish it was that easy. Just booted and nothing being used in swap, plenty of ram to use up. Gkrellm shows all that stuff.

---

### Post by lovinglinux on 2012-03-20
You need to optimize your bookmarks database.

[http://www.webgapps.org/tutorials/firefox/optimization/database-optimization](http://www.webgapps.org/tutorials/firefox/optimization/database-optimization)

I would also suggest that you update your applications, because unless you are using Ubuntu Hardy, all supported Ubuntu versions are using Firefox 11 already.

If you upgrade Firefox, you will see a huge improvement in performance.

---

### Post by fixitdude on 2012-03-20
> **lovinglinux said:**
> You need to optimize your bookmarks database.

[http://www.webgapps.org/tutorials/firefox/optimization/database-optimization](http://www.webgapps.org/tutorials/firefox/optimization/database-optimization)

I would also suggest that you update your applications, because unless you are using Ubuntu Hardy, all supported Ubuntu versions are using Firefox 11 already.

If you upgrade Firefox, you will see a huge improvement in performance.WOW! That looks like it did it! How did you know that?

I thought it was some sort of database thing going on but just couldn't track it down.

Why don't they do that every 30th time you start Firefox or something?

Or even better, if it takes more than 5 seconds to do that database thing it's doing, then spend the time cleaning it up instead. It would only need to run the HD once and a while then. What were those guys thinking?

For anyone wanting to do this manually, there are two files in my .mozilla directory that were huge, just put in your specific info for your machine, and the "default" folder is probably what you are using. Hit the "tab" key in a terminal to see what choices you have. Start in your "HOME" directory for your user.

```
sqlite3 .mozilla/firefox/[random characters].default/places.sqlite "vacuum"
sqlite3 .mozilla/firefox/[random characters].default/urlclassifier3.sqlite "vacuum"
```

The "[random characters]" are there to make that folder unique, so you have to change that to whatever yours is of course.

Try ls .mozilla/firefox/
and ls -al .mozilla/firefox/[random characters].default/

To find what you need and see what files are the largest.

You should make copies of those files first, just in case.

THANKS!

Oh and if you don't have sqlite3 installed...

```
sudo apt-get install sqlite3
```

---

### Post by lovinglinux on 2012-03-22
> **fixitdude said:**
> WOW! That looks like it did it! How did you know that?

I work with Firefox databases a lot. ;-)

Sometimes they drive me crazy, but I can't live without them. :-)

---

### Post by fixitdude on 2012-03-27
One thing it is still doing, but not as bad as it was is pausing for no reason.

Nothing else running, one page loaded, as an example, youtube "browse" page, which has no active videos on it.

I want to scroll down the page so I grab the slider and start moving it down and all of a sudden it stops, count one two three and release it again.

Problem is that my mouse and hand have kept going and so now it jumps way down. Just annoying.

Does this on news sites and a lot of other places.

Memory use is low and it does take some CPU to scroll, but I have two CPUs. It does seem like it's taking more CPU to scroll on firefox lately, maybe it's all this CSS stuff getting too over bloated, no one put any limitations on how much crap you can put in a CSS file.

Any ideas on that one?

---


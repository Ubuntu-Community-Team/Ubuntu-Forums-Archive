---
title: "Cant close firefox"
date: 2010-04-06
forum: General Help
---

### Post by keithg67 on 2010-04-06
From time to time firefox will not close unless I use control Q does anyone know why this is? It does not happen all the time only on occasion.

Ubuntu 9.10

---

### Post by Naitsirhc Hsem on 2010-04-06
I would recommend using chrome, firefox is to bulky for my tastes

---

### Post by -humanaut- on 2010-04-06
Give Swiftfox a try it's build against the most recent firefox code and optimized per architecture. Huge improvement over firefox less buggy and its waaaayy faster.

---

### Post by keithg67 on 2010-04-06
I am kinda partial to firefox due to some of the add ons I use but ill have to check out swiftfox and see if the add ons work they should. I do like google chrome alot but I just wish there was a way to get my add ons working for it.

Btw I am just coming back to linux and I have to say wow the improvment over just a year ago is great. a year ago I was fighting trying to get everything to work together and now I only had one issue after install getting all my programs to work I am very impressed.

---

### Post by philinux on 2010-04-06
> **keithg67 said:**
> I am kinda partial to firefox due to some of the add ons I use but ill have to check out swiftfox and see if the add ons work they should. I do like google chrome alot but I just wish there was a way to get my add ons working for it.

Btw I am just coming back to linux and I have to say wow the improvment over just a year ago is great. a year ago I was fighting trying to get everything to work together and now I only had one issue after install getting all my programs to work I am very impressed.

It could be one of your addons. Try disabling one by one to find the culprit. Or use safe mode to be sure it is an addon.

```
firefox -safe-mode
```

---

### Post by audiomick on 2010-04-06
From what I have read, most strange behaviour in Firefox seems to be somehow Flash related, but this is an impression, not grounded knowledge.

If you want to stick to firefox ( I am perfectly happy with it myself ) you might want to look at this thread
[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by -humanaut- on 2010-04-06
SwiftFox is Firefox all your plugins etc... Would work fine with it.

---

### Post by nischalinn on 2010-04-06
I do have the same problem. My firefox also freezes occasionally. I recommend you to use _**google-chrome **_and add **extensions.** Chrome has lots of extensions which are more richer than the ff.

---

### Post by lovinglinux on 2010-04-06
> **-humanaut- said:**
> Give Swiftfox a try it's build against the most recent firefox code and optimized per architecture. Huge improvement over firefox less buggy and its waaaayy faster.

There is also Swiftweasel, which is open source, although not updated as frequently as Swiftfox.

> **keithg67 said:**
> I am kinda partial to firefox due to some of the add ons I use but ill have to check out swiftfox and see if the add ons work they should. I do like google chrome alot but I just wish there was a way to get my add ons working for it.

Btw I am just coming back to linux and I have to say wow the improvment over just a year ago is great. a year ago I was fighting trying to get everything to work together and now I only had one issue after install getting all my programs to work I am very impressed.

Swiftfox and Swiftweasel use the same source code as Firefox, just compiled with different optimizations by different people. They have a different name because Mozilla doesn't allow them to use the Firefox brand, but they are the same thing. So all extensions and plugins will work. They will use the same user profile as Firefox or clone them to a new location.

BTW, the difference in performance is considerable, specially for single core processors.

> **philinux said:**
> It could be one of your addons. Try disabling one by one to find the culprit. Or use safe mode to be sure it is an addon.

```
firefox -safe-mode
```

Indeed that's probably the case. 

> **nischalinn said:**
> I do have the same problem. My firefox also freezes occasionally. I recommend you to use _**google-chrome **_and add **extensions.** Chrome has lots of extensions which are more richer than the ff.

Seriously? Chrome has a lot less features than Firefox and the extension repository cannot be compared to Firefox in any way. Even popular extensions that have been ported from Firefox to Chrome doesn't have all the features offered by the Firefox version. Chrome doesn't even work on KDE 64bit on several users machines. I don't want to start a browse war here, so let's get back on topic, which is solving the problem with Firefox. 

See the [COLOR="Sienna"]**Troubleshooting**[/COLOR] section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by orkyahaalhai on 2010-04-06
USe Seamonkey instead , it a whole package and the mother of firefox,.
Seamonkey suite has not only explorer but many other things like mail , rss ,etc. and the explorer part hen was taken out and redrawn and launched as a seperate entity came to be knpown as firefox!!!

go to mozilla site , see it ur self,and seamonkey is superb on flash , integrated flash support , or else u can use chrome

---

### Post by -humanaut- on 2010-04-06
I was just checking the builds of swiftweasel last night It sounds like that project might be dieing or dead. It's last build was 3.0RC1 But! The Swiftfox was updated to 3.6.3 last night.

---

### Post by muteXe on 2010-04-06
The chap wants to get his firefox fixed, not get a new browser. So many irrelevant posts...

---

### Post by whiskeylover on 2010-04-06
> **keithg67 said:**
> From time to time firefox will not close unless I use control Q does anyone know why this is? It does not happen all the time only on occasion.

Ubuntu 9.10


Is your browsing history really really long? Sometimes Firefox takes forever to quit because of that. Try going to History/Show All History, and clear all under the History node. See if that helps.

---

### Post by philinux on 2010-04-06
Please keep on topic guys. He wants firefox fixed not another browser recommendation.

---

### Post by lovinglinux on 2010-04-06
> **whiskeylover said:**
> Is your browsing history really really long? Sometimes Firefox takes forever to quit because of that. Try going to History/Show All History, and clear all under the History node. See if that helps.

You can [optimize the database](http://lovinglinux.megabyet.net/?page_id=220#Database--Optimization-1) to solve such issues with bookmarks and history.

BTW, Firefox takes longer to open and close usually because of extensions that perform functions onload/unload. If those functions include database writing, then the problem can be a combination of both problems. Optimizing the databases and disabling all extensions should fix the problem. Then you can test which extension is causing the problem.

---

### Post by keithg67 on 2010-04-07
Man lots of responces with good info Ill take a look tonight at the other browsers I have used all of them before except swiftfox.

With the history and extensions as well as plug ins I will test those tonight to see if any of those may be causing the issue. shouldnt take to long as I only have two add ons right now. Ill post with the results and let yall know what solved the issue.

Thanks for all the great info everyone!!!!

---


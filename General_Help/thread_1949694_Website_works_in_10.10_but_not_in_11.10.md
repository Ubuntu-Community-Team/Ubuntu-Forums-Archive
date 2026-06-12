---
title: "Website works in 10.10 but not in 11.10"
date: 2012-03-30
forum: General Help
---

### Post by gtdcubo on 2012-03-30
This is a webpage that I use a lot
[https://juegos.loteriasyapuestas.es/CF/games/LAQU/play.do?locale=en](https://juegos.loteriasyapuestas.es/CF/games/LAQU/play.do?locale=en)

When I navigate to this site using Ubuntu 10.10 on my desktop computer, the page displays properly. That is to say, in the middle of the screen there is a red framed graphical grid that can accept data input. 

When I navigate to the same site using my laptop with Ubuntu 11.10 the space that should be filled with the red framed grid shows solid black for 0.1 seconds and then disappears, with no error message or any sign that there is anything missing from the site.

I do not know the same for this grid object. I am tempted to call it a pop up but it I am not sure that this is correct. I have never heard a description for this type of object that we see every day when navigating. This is why I have put the link so that you can see it yourself.

It *had* been working correctly in 11.10 until about a month ago. I have uninstalled any application that had been installed since that date, but not the files that have been installed by the software centre that form updates to already installed products. I have reinstalled the Adobe Flash player and disabled the Firefox adblocker, but neither of these actions have resolved the issue.

This occurs both in Firefox and Chrome which is surprising because I would have expected the problem to be localised to one browser or the other. It must be something that both browsers share, but I have not been able to deduce more than that. 

This issue is a show stopper for further upgrades of Ubuntu. Not only is 11.10 awful to use with all the usual things hidden away in the wrong place, but now it stops me using my favourite Spanish national lottery site. I will stick to 10.10 for good if this problem persists.

Waat I am looking for in this post is some idea of where I might start to look for a solution to this problem. 

Thanks for your attention

---

### Post by lovinglinux on 2012-03-31
It is probably a Flash problem.

I have tested with Ubuntu 12.04 Beta 2 64bit, which is what I am using now. It worked with Firefox, Opera and Chrome. I will test on 11.10 as soon as I finish installing it on a VM.

Meanwhile, try [Flash-Aid](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

---

### Post by gtdcubo on 2012-03-31
Hello, thanks for your prompt reply. I have tried flash aid but that has not solved the problem. Incidently, the link of the problematic page that I put up is now time expired, and the following week's link has not been activated yet. I will post it when it becomes available.

---

### Post by gtdcubo on 2012-03-31
This has been solved by removing Gnash SWF viewer. This was recommended in this discussion in a discussion on the page of Adobe Flash player that you reach by clicking the "More Info" button from the Ubuntu Software centre entry for the flash player. This unfortunately doesn't show a web address so I can't post it.

In short, caused by compatibility between Flash and Gnash

1. Uninstall Gnash SWF viewer and Adobe flash player
2. Reboot the computer
3 Reinstall Flash player
4. Now the problem has gone

---


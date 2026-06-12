---
title: "Automatic Updates (Not JUST Security Updates)?"
date: 2011-03-25
forum: General Help
---

### Post by steevven1 on 2011-03-25
So, it is my understanding that Ubuntu's automatic updates do not install ANY updates that are not "important security updates." For example, it did not upgrade me to Firefox 4 automatically; I had to do it myself (Don't all new browser versions usually contain new security features/patches? Oh well...That is a separate question entirely).

ANYWAY, is there some way to get the latest stable versions of all of my open-source software automatically (or at least all at once, on command), instead of just security updates? It seems silly to have to install new versions for every program manually.

Also, related/side question: Now that I have installed Firefox 4 myself (via apt-get by adding the mozilla-stable PPA), will I stop getting security updates for Firefox through the standard Ubuntu update manager?

Actually, a really thorough explanation of the whole automatic update system (or a link to one) would be great too.

Thanks so much in advance. I know I asked a lot.

---

### Post by idoitprone on 2011-03-25
For most distros, what you see is what you get. Ubuntu do not upgrade you to the latest and greatest version of any application. They tend to stick with whatever you have right now. So if you start with firefox 3.6, you will end up with firefox 3.6, even if firefox 4.0 is declared stable and ready to use.  ex. That is why the kernel number is practically same the but are backported from more recent kernels.

Bottom line, if you want cutting edge, install them yourself. Ubuntu do not want to risk any stability  or compatibility problems

You will not stop getting patch though ppa, unless the team that manages it decide to stop themselves

When you refresh the update manager, it talks to the server to refresh your package list and your update manger computes the packages that need to update
Look at launchpad for the teams that manages packages. Remember this is a open source project so it involves alot of people
[http://www.youtube.com/watch?v=4XpnKHJAok8](http://www.youtube.com/watch?v=4XpnKHJAok8) Very interesting, linus on git and software management

---

### Post by Frogs Hair on 2011-03-25
Open the update manager and use the settings tab and you will find software sources . Use the updates tab to find a list of the type of updates available . From there you can set how often you would like install updates . The link maybe helpful. [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

---


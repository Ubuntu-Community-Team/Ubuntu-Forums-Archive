---
title: "Anyone use Pandora w/ Adobe Air?  I have a couple problems..."
date: 2009-10-10
forum: General Help
---

### Post by djm227 on 2009-10-10
I've only had linux for a few days, so bear with me.....

I love pandora, and love the fact that I can get it on my Ubuntu desktop with Adobe Air.  There is one minor annoyances that it gives me however, and was wondering if there is a way around it.

The app runs fine in air...but every time I click play/pause/thumbs up/thumbs down/next song...and pretty much all controls within the app, it performs the function but it also opens up a browser window which takes me to the web based pandora, which I have to close out of.  I know it isn't that big of a deal, but it kind of defeats the purpose of using a desktop app if the browser is opening all the time anyways.

 If there was a way to block air from opening pop ups or something it would be 10x better.


Thanks for the help!

---

### Post by djm227 on 2009-10-13
maybe it was a stupid question....but nobody?

These popups are starting to get really annoying, I wish there was a way to block air from being able to do that.

Any help would be a appreciated.

---

### Post by looter211 on 2009-10-14
Saw your post a day ago and I have been having the same problem and searching for an answer as well.  I'm guessing that the "real" reason is that Pandora is trying to get rid of the old Air app and push their new desktop app, which is only available if you upgrade your Pandora Account.  

This is the only link I found useful pertaining to our problem.

[http://getsatisfaction.com/pandora/topics/why_does_a_new_browser_open_when_i_click_a_button_on_desktop_pandora]("http://getsatisfaction.com/pandora/topics/why_does_a_new_browser_open_when_i_click_a_button_on_desktop_pandora")

---

### Post by djm227 on 2009-10-14
> **looter211 said:**
> Saw your post a day ago and I have been having the same problem and searching for an answer as well.  I'm guessing that the "real" reason is that Pandora is trying to get rid of the old Air app and push their new desktop app, which is only available if you upgrade your Pandora Account.  

This is the only link I found useful pertaining to our problem.

[http://getsatisfaction.com/pandora/topics/why_does_a_new_browser_open_when_i_click_a_button_on_desktop_pandora](http://getsatisfaction.com/pandora/topics/why_does_a_new_browser_open_when_i_click_a_button_on_desktop_pandora)


Wow I can't believe that is actually their excuse.  If they broke it, they should fix it....not force people to buy a new one or deal with the pop-ups.

Is the new app compatible with linux?  I thought I heard that it was'nt.

---

### Post by djm227 on 2009-10-14
I just found a good alternative.  Screenlets has an add on for it, pretty much the same thing except no pop-ups....but to my knowledge you can't minimize it.

Still looking for a way to get the Pandora paid app on Linux, if anybody knows please post it.

---

### Post by Benjimusprime on 2009-12-06
hey, I am experienceing same probs, found that the browser does not pop up when you use the rclick interface from the mmenu tool bar.  less functionality though...
Also, I get a certificate warning everytime I start it and I have to enable "This Session" to move forward...

any thoughts?

---

### Post by greg963 on 2009-12-15
You can use prism to launch pandora
```

sudo apt-get install prism

```

Then launch prism and follow the instructions to create a desktop shortcut.

The result is not very different than opening pandora in Adobe Air

---

### Post by yblumberg on 2009-12-21
I figured out how to make it work, at least on a mac. If you go to Show Package Contents (by right clicking the application) then Contents>Resources>javascript>main.js and change loader.navigateInSystemBrowser = true; to loader.navigateInSystemBrowser = false;

If you can get to main.js on ubuntu I expect it will work the same.

Open (or reopen) Pandora and try clicking play or next or something. It should work without opening any windows in your default browser. Of note, this will prevent opening ANY external pages. I found that clicking "Your Profile Page" loads the popup blocker warning and prevents the keyboard controls from working until I relaunch the application. I plan to try to find a better workaround if I can, but in the meantime I like this fix. 

For those who are wondering, the reason I prefer the Air app to those created with Prism or Fluid because, among other really tiny things, it has controls I can access in the dock with a right click.

---

### Post by looter211 on 2010-03-10
> I figured out how to make it work, at least on a mac. If you go to Show Package Contents (by right clicking the application) then Contents>Resources>javascript>main.js and change loader.navigateInSystemBrowser = true; to loader.navigateInSystemBrowser = false;

If you can get to main.js on ubuntu I expect it will work the same.

Open (or reopen) Pandora and try clicking play or next or something. It should work without opening any windows in your default browser. Of note, this will prevent opening ANY external pages. I found that clicking "Your Profile Page" loads the popup blocker warning and prevents the keyboard controls from working until I relaunch the application. I plan to try to find a better workaround if I can, but in the meantime I like this fix.

For those who are wondering, the reason I prefer the Air app to those created with Prism or Fluid because, among other really tiny things, it has controls I can access in the dock with a right click

Great find man!  I am still struggling to find a way to listen to Pandora on my desktop without having to upgrade to Pandora One.  After reading your post and doing a little searching this is where the java file is located for Ubuntu users

```
/opt/Pandora/share/javascript

```

the file main.js is in there and all you need to do is edit it.  I'm not too familiar with Java but maybe I can look into further revamping the code where Pandora dropped the ball.  Either way this works for me for now.  thanks again hope this helps someone.

---

### Post by Keith1212 on 2010-03-11
> **yblumberg said:**
> I figured out how to make it work, at least on a mac. If you go to Show Package Contents (by right clicking the application) then Contents>Resources>javascript>main.js and change loader.navigateInSystemBrowser = true; to loader.navigateInSystemBrowser = false;

If you can get to main.js on ubuntu I expect it will work the same.

Open (or reopen) Pandora and try clicking play or next or something. It should work without opening any windows in your default browser. Of note, this will prevent opening ANY external pages. I found that clicking "Your Profile Page" loads the popup blocker warning and prevents the keyboard controls from working until I relaunch the application. I plan to try to find a better workaround if I can, but in the meantime I like this fix. 

For those who are wondering, the reason I prefer the Air app to those created with Prism or Fluid because, among other really tiny things, it has controls I can access in the dock with a right click.

> **looter211 said:**
> Great find man!  I am still struggling to find a way to listen to Pandora on my desktop without having to upgrade to Pandora One.  After reading your post and doing a little searching this is where the java file is located for Ubuntu users

```
/opt/Pandora/share/javascript

```the file main.js is in there and all you need to do is edit it.  I'm not too familiar with Java but maybe I can look into further revamping the code where Pandora dropped the ball.  Either way this works for me for now.  thanks again hope this helps someone.

thx guys worked perfect.

---

### Post by Foxcow on 2010-07-13
> **greg963 said:**
> You can use prism to launch pandora
```

sudo apt-get install prism

```

Then launch prism and follow the instructions to create a desktop shortcut.

The result is not very different than opening pandora in Adobe Air




Is there anything else aside from Prism I need to get this to work?  I installed it and followed the instructions but it immediately crashes.

---


---
title: "NBC Videos won't play"
date: 2010-04-13
forum: General Help
---

### Post by blur xc on 2010-04-13
Is there a known issue with NBC videos and Linux?  My wife says she used to be able to see them, but now they just load forever (stupid peacock) and never plays.

Thanks,
BM

---

### Post by wojox on 2010-04-13
Do you have moonlight installed?

---

### Post by blur xc on 2010-04-13
> **wojox said:**
> Do you have moonlight installed?

Can't say...  I'll check when I get home.

BM

---

### Post by blur xc on 2010-04-13
Ok- installed moonlight but still no dice.  Now I get this message:

```
Sorry but we do not support that browser, please use one of these

= = = = = = = = = = = = = = = = = = = =

Windows
Internet Explorer 7
Internet Explorer 6
Firefox 3
Firefox 2
Chrome

Mac
Firefox 3
Firefox 2
Safari
Chrome
Camino

= = = = = = = = = = = = = = = = = = = =
```

I'm using namoroka- don't know why that would be a problem.

BM

---

### Post by WinterRain on 2010-04-13
It says windows and mac are supported, not linux.

---

### Post by JoelOl75 on 2010-04-14
There is a way to FAKE out the browser information sent to the NBC website with a setting in the about:config section of firefox but I am at work and can't recall exactly how to do it at this time...  Hopefully someone else can chime in but it can be done!

---

### Post by wojox on 2010-04-14
> **blur xc said:**
> 

I'm using namoroka- don't know why that would be a problem.

BM


Don't know. It's not working here either. I could watch the Olympics fine. Never tried their shows. User Agent Add-on for Firefox don't help either.

---

### Post by sdowney717 on 2010-04-14
Microsoft and NBC are tied together MSNBC. If you do a google search and put in those terms you see a lot of interaction, perhaps a collusion exists to keep linux as an unsupported outsider.

I did see that ABC works in ubuntu
[http://abc.go.com/watch/lost/93372/258167/everybody-loves-hugo](http://abc.go.com/watch/lost/93372/258167/everybody-loves-hugo)

---

### Post by blur xc on 2010-04-14
> **WinterRain said:**
> It says windows and mac are supported, not linux.

Missed that...

Jeez...  so stupid.  Why does the OS have anything to do with a website playing or not?  It's not like they need you to dl and run a .exe or anything.  I could understand why they'd support some browsers, but a browser is a browser and shouldn't matter what operating system it is running on...

Jerks.

Thanks for the help...
BM

---

### Post by opensource-for-all on 2010-04-16
you can watch most of the shows on NBC.com on Hulu.com :)

---

### Post by BandD on 2010-04-20
I get the same "we don't support that browser" pop-up message.  

Anybody know what setting to change in about:config to trick the NBC site.  This is kind of a deal breaker for my wife.  We were able to watch these videos without problems two weeks ago (we haven't tried watching any again until tonight).

Thanks for any help!

---

### Post by BandD on 2010-04-20
Ok, so after about an hour of google searches and a bunch of trial and error I found a fix the the NBC site issue.  

* NOTE: I'm using adobe's 10.1 pre-release version of the flashplugin.  This may be required to view videos on NBC's site.  For a quick guide for firefox users see [here]("http://www.ubuntugeek.com/how-to-install-adobe-flash-player-10-1-beta-in-ubuntu.html").*

Step one: Go to tools in the firefox menu.  Click "add-ons".  In  the pop up window click "Get Add-Ons".  Search for user agent switcher and click to install.  Once installed restart firefox.

Step two: Go to [this site]("http://www1.qainsight.net:8080/content/binary/AgentStrings20070304.xml"). Copy and paste all text into a gedit text file.  Save the file with a .xml extention.  

Step three:  Open firefox again and go to Tools --> Default User Agent.  Then select  "Edit User Agents" Then click import.  Navigate to the .xml file you saved in gedit and click import.  

Step four:  Go to Tools-->Defualt User Agent.  From the menu select "MSIE (WinXP)"  Then go to the NBC site and you should be able to watch your video.  Each time you restart firefox the user agent will go back to "default" (ubunut branded).  When you want to watch a video on the NBC site you will have to change the user agent to "MSIE 7 (WinXP)" BEFORE you click on the video you want to watch.

Hope that helps.  The wife is happy now!

---

### Post by blur xc on 2010-04-20
> **BandD said:**
> Ok, so after about an hour of google searches and a bunch of trial and error I found a fix the the NBC site issue.  

Step one: Go to tools in the firefox menu.  Click "add-ons".  In  the pop up window click "Get Add-Ons".  Search for user agent switcher and click to install.  Once installed restart firefox.

Step two: Go to [this site]("http://www1.qainsight.net:8080/content/binary/AgentStrings20070304.xml"). Copy and paste all text into a gedit text file.  Save the file with a .xml extention.  

Step three:  Open firefox again and go to Tools --> Default User Agent.  Then select  "Edit User Agents" Then click import.  Navigate to the .xml file you saved in gedit and click import.  

Step four:  Go to Tools-->Defualt User Agent.  From the menu select "MSIE (WinXP)"  Then go to the NBC site and you should be able to watch your video.  Each time you restart firefox the user agent will go back to "default" (ubunut branded).  When you want to watch a video on the NBC site you will have to change the user agent to "MSIE 7 (WinXP)" BEFORE you click on the video you want to watch.

Hope that helps.  The wife is happy now!

Wow- That's awesome!  I can't wait to give that one a try...  Can you make a shortcut toolbar button to switch user agents quickly?

thanks,
BM

---

### Post by skain on 2010-04-21
Installed moonlight, and user agent switcher.

Still not working for me under Karmic.  I don't get the unsupported browser pop-up any longer, but all NBC will display is the animated peacock and the video refuses to load.

Same issue under Chrome for Linux.  :confused:

---

### Post by |{urse on 2010-04-21
Ive never been able to see the shows on nbc.com with any browser on linux (several different distros of it at that!) It's been nothing but that stupid peacock for years. There's nothing wrong with your machine (hopefully). =/ 

HULU FTW

---

### Post by |{urse on 2010-04-21
I just saw your howto up there, nice! I'll try that sometime.
:guitar:

---

### Post by fragos on 2010-04-22
NBC has coded their site to not allow Linux. That doesn't mean Linux won't work it may only show web technology ignorance on their part. I even had a Comcast support person once tell me that I had to get Windows to use the Internet. There is no end of ignorance in the strangest places. Perhaps they were stupid enough to use Active-X instead of Javascript which would limit users to Windows.

---

### Post by BandD on 2010-04-25
I also forgot that I'm running the the pre-release version of adobe's 10.1 flashplugin.  I read somewhere a while ago that it was required to make videos play on NBC's site.  There is an easy turtoial for firefox users [here]("http://www.ubuntugeek.com/how-to-install-adobe-flash-player-10-1-beta-in-ubuntu.html")

I've also amended my mini-tutorial above in inculde and blurp about installing the 10.1 pre-release.

---

### Post by blur xc on 2010-04-26
> **BandD said:**
> I also forgot that I'm running the the pre-release version of adobe's 10.1 flashplugin.  I read somewhere a while ago that it was required to make videos play on NBC's site.  There is an easy turtoial for firefox users [here]("http://www.ubuntugeek.com/how-to-install-adobe-flash-player-10-1-beta-in-ubuntu.html")

I've also amended my mini-tutorial above in inculde and blurp about installing the 10.1 pre-release.

Sweet- thanks.  I was just going to post that your instructions didn't work for me...  I'll get on that 10.1 flash plugin and try again.

Thanks,
BM

---

### Post by blur xc on 2010-04-28
Thanks BandD!  I finally got around to isntalling the 10.1 RC flash player, and along with your other tips, my wife is happily viewing office out-takes again.  This thread is marked solved!

The only one thing I'd wish for, would be a nice firefox tool button to easily toggle between user agents, so my less than tech savvy wife won't have to go into the user agent menu all the time...

BM

---

### Post by oldgeekster on 2010-05-10
> **BandD said:**
> I also forgot that I'm running the the pre-release version of adobe's 10.1 flashplugin.  I read somewhere a while ago that it was required to make videos play on NBC's site.  There is an easy turtoial for firefox users [here]("http://www.ubuntugeek.com/how-to-install-adobe-flash-player-10-1-beta-in-ubuntu.html")

I've also amended my mini-tutorial above in inculde and blurp about installing the 10.1 pre-release.Ubuntugeek's tutorial you linked to is a bit out of date, (they are up to RC4 so you have to go looking for and manually install the file), but the concept is the same - you just have to change the file name you are working with.

Just watched Betty White's SNL hosting appearance on my Lucid Lynx system. :cool:

---

### Post by Old *ix Geek on 2010-05-10
I have to jump on my soapbox...my long-standing soapbox...for a moment.

It's all well and good to trick a site into working with Linux so you can have your instant gratification, but it ACCOMPLISHES nothing.  Remember that horrific period in the web's history when many sites were "IE only"?  You know why they stopped being IE only?  Because people like me COMPLAINED. :mad:

When you visit a site that doesn't support Linux, and instead of complaining about it you trick it into seeing you as a windoze user, you're HURTING all of us Linux users.  Sites like that will continue ignoring Linux as long as they THINK no Linux users want to access it.  Speak up, folks.

---

### Post by User3k on 2010-05-10
> **sdowney717 said:**
> Microsoft and NBC are tied together MSNBC. If you do a google search and put in those terms you see a lot of interaction, perhaps a collusion exists to keep linux as an unsupported outsider.

I did see that ABC works in ubuntu
[http://abc.go.com/watch/lost/93372/258167/everybody-loves-hugo](http://abc.go.com/watch/lost/93372/258167/everybody-loves-hugo)

I don't think it is that. I watch videos online all the time at MSNBC in Linux and BSD. It is one of my mainstream media news sources so it is something I want with all my os'. NBC itself is just really messed up. Like others already said here catch what you can at Hulu and forget about NBC's website.

---

### Post by BandD on 2010-05-11
I've written to the NBC webmaster several times about how ludicrous it is that they won't allow opperating systems other than Windows and OSX.  I've done my share of complaining while still "tricking" their site into thinking I'm using an OS I'm not.  

I don't want to give the impression that I'm just rolling over for NBC.  I did what I can and I'm prefectly good with tricking them.

And you're right about the mini guide.  I i'm so used to tab auto-complete in the terminal that I forget about stuff like that.  Plus I've always been good at generalizing things...

---

### Post by BandD on 2010-05-23
This doesn't seem to be a problem any more.  Either NBC stopped doing the browser check or they now accept Firefox run from a Linux machine in addition to the MS and Mac editions...

Maybe the complaining worked!

---

### Post by cmjrff on 2010-05-24
Does anyone know where to get the flash 10.1 pre release in amd64?

---

### Post by blur xc on 2010-05-24
> **cmjrff said:**
> Does anyone know where to get the flash 10.1 pre release in amd64?

Yeah, I just upgraded to Ubuntu 10.04, 64bit over the weekend and have not yet fixed flash, and don't know if there's anything special I need to do...

BM

---


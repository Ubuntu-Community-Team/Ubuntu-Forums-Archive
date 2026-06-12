---
title: "Applets not working in Firefox 3"
date: 2010-03-02
forum: General Help
---

### Post by tylerhayes on 2010-03-02
Hello,

I am running Jaunty 9.04 with Firefox 3.0.18.

Here is the output of [FONT=Courier New]$ java -version[/FONT]:

[FONT=Courier New]java version "1.6.0_16"
Java(TM) SE Runtime Environment (build 1.6.0_16-b01)
Java HotSpot(TM) 64-Bit Server VM (build 14.2-b01, mixed mode)
[/FONT]
I have tried the solution to this thread: [http://ubuntuforums.org/showthread.php?t=840649](http://ubuntuforums.org/showthread.php?t=840649)
but to no avail.  And this thread: [http://ubuntuforums.org/showthread.php?t=1081574](http://ubuntuforums.org/showthread.php?t=1081574)
doesn't help either.

The website I am trying to view the applet on is: **[http://www.phy.ntnu.edu.tw/ntnujava/index.php?topic=120.0](http://www.phy.ntnu.edu.tw/ntnujava/index.php?topic=120.0)**.

Nothing comes up saying a missing plug-in needs to be installed, but a small, blank window appears with a title of "Java" which can't be closed and has to be killed.

Any ideas?

Thanks,
Tyler

----------------------------------------------------
*Nevermind--I'm an idiot.  It's working now.*
[I]Thanks anyway.
- Tyler[/I]

---

### Post by darolu on 2010-03-02
Did you install the sun-java6-plugin package?

I got the small blank window too, seems to be part of the applet, I'm using Google Chrome browser though, do you have the same problem with other browsers or is it firefox exclusive?

---

### Post by tylerhayes on 2010-03-03
Haven't tried on other browsers, but the blank window only shows up for that one, and if it shows up for you too, then I think all is good.  Thanks for the help, but it looks like everything is fine now.  I just assumed it wasn't working when I saw the "**[COLOR=#0000ff]If java program did not show up, please download and install latest [Java RUN TIME]("http://www.java.com/en/download/manual.jsp")[/COLOR]**[COLOR=#0000ff][COLOR=Black]" message, so I didn't bother scrolling down, when in fact the applet was there below.  I'm an idiot.  But it was the solution to thread [/COLOR][/COLOR][http://ubuntuforums.org/showthread.php?t=840649](http://ubuntuforums.org/showthread.php?t=840649) that solved it (because it really was a problem earlier).

- Tyler

---


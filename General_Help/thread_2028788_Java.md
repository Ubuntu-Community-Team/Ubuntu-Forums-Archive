---
title: "Java"
date: 2012-07-18
forum: General Help
---

### Post by oldtraveler on 2012-07-18
Re: Install Java
This is one reason I keep leaving Ubuntu and then come back later thinking that surely by now Ubuntu would have made it easy to get something as universally used as java.

Does any one have a sure fire way to get java in Ubuntu 12.04? All of the  comments in  [http://ubuntuforums.org/showthread.php?t=1215746&page=3](http://ubuntuforums.org/showthread.php?t=1215746&page=3) seem to no longer work,
Qlll has posted a link which I am in the process of trying, but have not yet had success with.
> Qlll 
  Re: Install Java
Yes. See the wiki link in my signature.

In the wiki, find the link entitled "Using webupd8.org's strikingly simple method."
__________________
Community Java Wiki | The Community ATI Driver Wiki


In the wiki, find the link entitled "Using webupd8.org's strikingly simple method."
[/quote]
__________________

---

### Post by QIII on 2012-07-18
Describe what is happening.

---

### Post by oldtraveler on 2012-07-18
I installed as per 

" OpenJDK

Installation of Java Runtime Environment

    Install the openjdk-6-jre package using any installation method.

    Install the openjdk-7-jre package using any installation method. 

Browser plugin

    Install the icedtea6-plugin package using any installation method.

    Install the icedtea-7-plugin package using any installation method. 

This plugin works with the main browsers: Firefox, Chromium, Google Chrome, and Epiphany.

(On Konqueror, go to Settings &#8594; Configure Konqueror... and from menu select Java & JavaScript, then tick Enable Java globally option.) [color=red]I didn't do this.[/color]

SDK (Software Development Kit)

    Install the openjdk-6-jdk package using any installation method.

    Install the openjdk-7-jdk package using any installation method. "


All appeared to install OK so then I went to Pogo which requires java to play and when I asked for the card game board it appeared that it was going to work, but alas at the end I go a message from Pogo that said they were unable to open the game (Hearts)


So I booted to Windows and from there had no difficulty in opening the Hearts window.

---

### Post by QIII on 2012-07-18
It is possible that your game does not recognize OpenJDK (or, more precisely, OpenJDK's IcedTea browser plugin in your case) as Java.  That happens.    Many developers do not understand that OpenJDK 7 is the open source reference implementation of Oracle Java, even though Oracle recognizes it as such and takes part in its development.

In the Oracle Java 7 section, under "Command line methods", see the link at "Using webupd8.org's strikingly simple method".

---

### Post by David Andersson on 2012-07-19
> **oldtraveler said:**
> 
All appeared to install OK so then I went to Pogo which requires java to play and when I asked for the card game board it appeared that it was going to work, but alas at the end I go a message from Pogo that said they were unable to open the game (Hearts)


When I try the "Hearts" card game it says "fbconnect libarary is missing" and then a black page. This is because I have blocked javascript from Facebook. I have seen other commercial game sites not working if advertisement is blocked (AdBlock Plus). Do you block anything?

Or, it may be that the site is programmed to hate your particular browser or operating system. Try another browser or try set a fake user agent string in your current browser. (Here's how your browser presents itself: [http://useragentstring.com/](http://useragentstring.com/), hers's how to change it in firefox: [https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher](https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher) or [http://superuser.com/questions/98798/how-do-i-change-firefoxs-user-agent-via-aboutconfig](http://superuser.com/questions/98798/how-do-i-change-firefoxs-user-agent-via-aboutconfig) )

---

### Post by QIII on 2012-07-19
Oldtraveler, it may be caused by the fact that you are not allowing scripts or are running an ad blocker as suggested above.

Javascript is not Java (Oracle or OpenJDK) however confusing that may sound.  It may be a sixth cousin twice removed, but it is not Java.

Javascript started life as Livescript and was developed by Netscape.  Javascript is (generally) contained in the web page's HTML and operates as the browser interprets it.  Blocking scripts in your browser will kill it.

I block ads and scripts.

---

### Post by oldtraveler on 2012-07-19
> **QIII said:**
> It is possible that your game does not recognize OpenJDK (or, more precisely, OpenJDK's IcedTea browser plugin in your case) as Java.  That happens.    Many developers do not understand that OpenJDK 7 is the open source reference implementation of Oracle Java, even though Oracle recognizes it as such and takes part in its development.

In the Oracle Java 7 section, under "Command line methods", see the link at "Using webupd8.org's strikingly simple method".
Installing Oracle Java 7 did the trick.  Thank you.

---


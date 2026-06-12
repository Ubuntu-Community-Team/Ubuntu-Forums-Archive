---
title: "Launcher to set Firefox to User Agent IE8"
date: 2012-03-27
forum: General Help
---

### Post by GaryMac on 2012-03-27
Setting up Ubuntu in Internet Cafe ... Ubuntu 10.04
 
No Live Messenger = Problem
 
Emesene = no webcam
 
 
So ...
 
Only (simple) option = EBuddy ... 
 
Now if I go to E Buddy using IE .. sign in .. I get the webcam "button"
 
If I use Firefox - Chrome - Opera ... I do not get the webcam button.
 
 
So .. all I want to do is create a desktop launcher ... for Live Messenger ...
Which willl open [http://www.ebuddy.com/](http://www.ebuddy.com/) in Firefox but ... in IE 8 mode
 
I tried the User Agent Switcher Add On ... but it needs to be manually set.
When it is manually set - Firefox shows the webcam button.
 
I tried one on Chrome called Ultimate User Agent Switcher .. could not get that to work.
 
I have been looking all day for a solution.
 
Is it posible to simply create a launcher to do this ??
 
Among the many Launcher attempts I tried are ..
firefox [http://www.ebuddy.com/](http://www.ebuddy.com/) --user-agent "Mozilla/4.0 (compatible; MSIE 8.0; Windows NT 6.1)"
firefox [http://www.ebuddy.com/](http://www.ebuddy.com/) --user-agent="MSIE 8"
 
 
Any suggestions appricated.

---

### Post by GaryMac on 2012-03-28
Just tried AMSN ..  which does support Video Chat .. but ONLY when BOTH parties are using AMSN.
 
As already stated this is for an Internet Cafe ..  so Live Messenger is (unfortunately) A MUST.

I have Tokbox set up already ...  which is a BIG plus in that neither party needs to sign in ..  but have experienced some problems with this where (presumably) Flash was "blocked" on the other persons setup.

So I really do need to cover all bases (or lose customers) and the E Buddy option is the only viable one I can find.

**[SIZE=3]To re-itterate ..  the quest is ..[/SIZE]**
To have Firefox launch in User Agent "Internet Explorer" mode ..  this will enable the webcam "button" once striking up a connection with a MSN contact.

I will also post this on the Mozilla Forum.

---

### Post by zombifier25 on 2012-03-28
As far as I know, Firefox does not have a command line switch for user agent.
What you can do is change the user agent **permanently** via about:config.
1. Open about:config
2. Right-click, choose "New" > "String"
3. Type "general.useragent.override" (no parentheses) into the "New String Value" dialog box that appears and press "Enter."  Type or copy and paste the desired new user agent string into the "Enter  String Value" box (in this case "Mozilla/4.0 (compatible; MSIE 8.0; Windows NT 6.1)" )
When you're done, copy that Firefox profile to all of your computers (the .mozilla folder)
EDIT: Remember to delete the old one on the computer.
Also, nice to know that Ubuntu Internet cafes exists.

---

### Post by GaryMac on 2012-03-28
Zombiefier ...

Thanks for the advice ..  I tried this in BOTH Firefox & Seamonkey ... and it did not work ...  no webcam button.

I installed Seamonkey add on Proxy Tool ..  which gives the option to change User Agent (per session) ..  and that worked.


Have posted question on Mozilla Forum ... 
[https://support.mozilla.org/en-US/questions/924083](https://support.mozilla.org/en-US/questions/924083)

---

### Post by Habitual on 2012-03-28
> **zombifier25 said:**
> As far as I know, Firefox does not have a command line switch for user agent.
What you can do is change the user agent **permanently** via about:config....

How about a different FF profile that has the tweaked user agent and run that?

```
-P <profile>       Start with <profile>
```

Just a thought...

---


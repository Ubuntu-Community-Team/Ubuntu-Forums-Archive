---
title: "java does not work on firefox"
date: 2009-09-20
forum: General Help
---

### Post by serious7 on 2009-09-20
Hi I'm trying to use a java application on firefox and it is not working. It works in windows...I dont understand why it doesn't work here. It aksed to download plugins and i clicked ok but even after it installed all the necessary plugins, it still does not work. Java is enabled in the browser. I'm using 64 bit jaunty.

---

### Post by XCan on 2009-09-20
Which plugin did you install? For compatibility, I think you should instann sun-java6-plugin.

---

### Post by The Cog on 2009-09-20
If you enter the address ```
about:plugins
``` to the firefox address bar, you will see if firefox has a java plugin and if so, which version it is. Like XCan, I recommand the Sun java plugin.

---

### Post by sunchiqua on 2009-09-20
```
sudo apt-get install sun-java6-jre sun-java6-plugin

```

Already installed ?

---

### Post by JohnE1 on 2009-09-21
I just went through this very problem, and after much research and reading, I was able to piece together my own solution, borrowing from all I had learned during my research.

I have the Sun Java components working properly. I tried the IcedTea (3rd party) Java plugin route and it partially worked, but would never load a game table in Yahoo Spades, for example, yet it could load the room, okay.

I read of known Java problems with FF 3.0.xx, NoScript, and AdBlock Plus (see the link below), but since I completely removed all Java components and did a fresh install of ONLY Sun's Java components, I am not experiencing any of those problems now.

**Bug reports on FF 3.0, NoScript, and AdBlock Plus**
**[https://bugzilla.mozilla.org/show_bug.cgi?id=409566]("https://bugzilla.mozilla.org/show_bug.cgi?id=409566")**

My personal opinion, based on my experiences, is that these problems only exist with the 3rd party IcedTea java plugin, NOT the Sun's Java components.

***TIP! Be sure to bookmark the links so you can quickly get back to them after restarting Firefox!***


Here's what I suggest you try FIRST!


1.  Enable restricted formats, so you can install the Sun Java components. Restricted formats refers to software that is not 100% open source, can even be proprietary with its own licenses, but when you need them, and can use them legitimately, why wouldn't you?

**Enable restricted formats**
**[http://answers.yahoo.com/question/index?qid=20090602031805AAwfQGG]("http://answers.yahoo.com/question/index?qid=20090602031805AAwfQGG")**


2.  Install the Sun Java components.

sudo apt-get install sun-java6-bin sun-java6-fonts sun-java6-jre sun-java6-plugin

More on this can be found at the link below.

[B][I]NOTE: I chose to also install the binaries, sun-java6-bin, which is not included in the sudo apt-get install line in the link below!!
[/I][/B]

**HOW-TO-Install-Java-Runtime-Environment-JRE-in-Ubuntu-904-Jaunty**
**[http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu-904-jaunty.html#more-1307]("http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu-904-jaunty.html#more-1307")**


3.  Test the Java installation.

a. Check the java --version command in a console, per the instructions in the above link. It should return some info if Java is installed properly.

b. In Firefox, open a new tab or window and in the address bar enter, about: plugins (remove the space after the colon, the colon 'p' was showing up as a smiley face).

Alternately, in Firefox open the Tools menu, select Add-ons, when the Add-ons window appears click on the Plugins tab and see if the Java Plugin shows up and is active (not grayed out).


4. If all checks out so far, there is a good chance your Java plugin is good to go, but if it still doesn't work, don't fret, there are additional steps to resolve the issues.

The easiest way to test the Java plugin is to try to load a game table in any Yahoo Game. For temporary testing purposes, enable Popups in Firefox Edit menu, Preferences. Disable NoScript and AdBlock Plus in Firefox Tools menu, Add-ons, then shutdown and restart Firefox.


NOW. Can you get a game room to load?!?!?!


a. If, YES!!, then try to load a game table.


i. If a game table loads, then you should be good to go!!


ii. If a game table won't load, but you can get a game room to load (that's a java applet), then the java plugin is partially working.

I'm gonna guess that the issue is most likely a conflict or configuration issue with Java.

What I did was use Synaptic Package Manager to, "Mark for Complete Removal", ALL Sun Java components, and, "Mark for Complete Removal", ALL the IcedTea and openjdk components.

Then I clicked the Apply button, and, Voila!, they're all removed in a few minutes. Now you should have NO base Java or Java plugin components installed, Your copy of Ubuntu is ready for a fresh install of Sun Java!

Per my earlier instructions, go back to Step 1. Start over and re-install and test the Sun Java components.

Good Luck!! That should get it working, finally!!!!



b. NO!!! - A Yahoo game room won't load.


i. Open a new window or tab if FF and enter, about:config.

Once the about:config window appears, enter, 'java' (without the quotes) into the Filter: text area to limit the visible settings.

[B]What is the value for, java.java_plugin_library_name ?

If it's, javaplugin_oji, edit it so it reads, libjavaplugin_oji[/B]

Close FF and restart it and test again.

Does the Java plugin show up now?


ii. If it still won't work:

What I did was use Synaptic Package Manager to, "Mark for Complete Removal", ALL Sun Java components, and, "Mark for Complete Removal", ALL the IcedTea and openjdk components.

Then I clicked the Apply button, and, Voila!, they're all removed in a few minutes. Now you should have NO base Java or Java plugin components installed, Your copy of Ubuntu is ready for a fresh install of Sun Java!

Per my earlier instructions, go back to Step 1. Start over and re-install and test the Sun Java components.

Good Luck!! That should get it working, finally!!!!

------------------


I hope this helps you and others, as it helped me.


Best regards,

JohnE1

---


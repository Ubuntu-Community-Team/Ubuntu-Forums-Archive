---
title: "firefox Java warning???"
date: 2012-04-02
forum: General Help
---

### Post by eival on 2012-04-02
i just got a popup telling me IcedTea is outdated but when i researched the reason why it appears they're refering to ORACLEs version which this isnt and its telling me to install the latest ORACLE version.

can anyone else varify if this is an error on their end thinking Icedtea is an out-of-date ORACLE plugin:confused:

---

### Post by eival on 2012-04-02
[https://bugzilla.mozilla.org/show_bug.cgi?id=739955](https://bugzilla.mozilla.org/show_bug.cgi?id=739955)

thats the bug that it refers too when it popped up in firefox

---

### Post by dbclinton on 2012-04-02
I just got the same thing. 
I'm running 10.04 LTS with the native Firefox and Icedtea. I wonder if this is connected to the update cycle...I see that this update occurred on March 29:
[INDENT]Upgraded the following packages:
ca-certificates-java (20100406ubuntu1) to 20100406ubuntu1.1[/INDENT]

And here's the error message Firefox gave me:

[INDENT]Firefox has determined that the following add-ons are known to cause stability or security problems:
icedtea NPR web browser plugin (using icedtea6 1.9.13 (6b20-1.9.13-Oubuntu1~10.04.1[/INDENT]

Anyone out there know what's going on?

---

### Post by lovinglinux on 2012-04-02
**Blocklisting Older Versions of Java**

[http://blog.mozilla.com/addons/2012/04/02/blocking-java/](http://blog.mozilla.com/addons/2012/04/02/blocking-java/)

---

### Post by lovinglinux on 2012-04-02
> **dbclinton said:**
> I just got the same thing. 
I'm running 10.04 LTS with the native Firefox and Icedtea. I wonder if this is connected to the update cycle...I see that this update occurred on March 29:
[INDENT]Upgraded the following packages:
ca-certificates-java (20100406ubuntu1) to 20100406ubuntu1.1[/INDENT]

And here's the error message Firefox gave me:

[INDENT]Firefox has determined that the following add-ons are known to cause stability or security problems:
icedtea NPR web browser plugin (using icedtea6 1.9.13 (6b20-1.9.13-Oubuntu1~10.04.1[/INDENT]

Anyone out there know what's going on?

When I visit [https://www.mozilla.org/en-US/plugincheck/](https://www.mozilla.org/en-US/plugincheck/) Firefox determines that my Icedtea is a unknown plugin, but doesn't block it. However, my version is 1.2, since I am running Precise Pangolin.

[IMG]http://i.imgur.com/GL7g7.png[/IMG]


So I presume icedtea6 1.9.13 is affected by the security issue and has been blocklisted.

Here are the current versions across Ubuntu releases:

[http://packages.ubuntu.com/search?suite=all&section=all&arch=any&searchon=names&keywords=icedtea](http://packages.ubuntu.com/search?suite=all&section=all&arch=any&searchon=names&keywords=icedtea)

---

### Post by dbclinton on 2012-04-02
Thanks. This is definitely what's happening. 
The question is whether Ubuntu will upgrade us automagically in the next few days or whether we're better off upgrading directly from Java.
Regards,
David

---

### Post by QIII on 2012-04-02
While it is to be hoped that the world will one day recognize OpenJDK and the IcedTea plugin, such is not the case -- despite the fact that OpenJDK 7 is the reference implementation of Java 7.  If you go to the Oracle/Sun site by googling "Do I have Java", you will notice that it DOES recognize OpenJDK (which it did not used to), but will probably tell you your version is out of date.  Point is that Oracle/Sun understands OpenJDK.

It is possible that even after an OpenJDK update some web content will not work with OpenJDK for no reason other than the fact that some web developers don't think OpenJDK is Java and, when they have their applets check for Java, they don't think they have found it.  Java applications installed on your machine may barf when they don't find "Java".

Things are getting much better, but it's not perfect yet.

OpenJDK and Oracle/Sun Java (JRE and the JDK) can happily coexist on a machine.  All one has to do is update their alternatives to make one active and the other not.

Unfortunately, sometimes the same is not true for the plugins.

It may be necessary for you to use the Java plugin until such a time as the rest of the world pulls its head and gets with reality.  

Until then, this may be useful:

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

Now that OpenJDK is the reference implementation, I have become ambivalent.  I almost think we should boycott anything that hasn't embraced OpenJDK.

---

### Post by dln9 on 2012-04-02
I, too, got this error message:  

"Firefox has determined that the following add-ons are known to cause stability or security problems:"  

"IcedTea NPR Web Browser Plugin (using IcedTea6 1.9.13 (6b20-1.9.130ubuntu1~10.04.1))"

"For your protection, it is highly recommended that you restart with these add-ons disabled."  

Then, there is what appears to be a hyperlink of the words, "More Information", but clicking on it appears to do nothing.  There are also two buttons:  "Restart Later", and "Restart Firefox".  Finally, there is an option checked called, "Disable".  

I am running Ubuntu Lucid 10.04, and Firefox 11.0 (Mozilla Firefox for Ubuntu Canonical - 1.0).  


I have read the previous entries in this thread.  I'm sorry - I hardly understand a quarter of what is being discussed, and more importantly, the implications of what is being discussed.  

I'm looking for help - What should I be doing?  

Should I disable the IcedTea plugin?  

If I disable the IcedTea plugin, what do I replace it with?  And, how do I do that?  And, do I then need to forever manually keep it current myself?  

Should I do anything at this point - will Ubuntu shortly update all this stuff for me?  

Thanks in advance for any help.

---

### Post by dbclinton on 2012-04-02
> I'm looking for help - What should I be doing?

Should I disable the IcedTea plugin? 

I'm not the one to tell you how and when you should replace Java - I'm still unsure myself. But I can say that disabling Icedtea seems to be a really good idea. There does seem to be a real risk to your system.

---

### Post by lovinglinux on 2012-04-03
> **dbclinton said:**
> I'm not the one to tell you how and when you should replace Java - I'm still unsure myself. But I can say that disabling Icedtea seems to be a really good idea. There does seem to be a real risk to your system.

Yes, it seems to be a really good idea. What I would do is disable it, then if you need it on a site you trust, then enable it only while navigating the trusted site. You can do that using the add-on manager. Just type ***about:addons*** in the address bar or use the Tools menu.

However, keep an eye in your updates. Since it seems to be affecting only IcedTea6 1.9.13, you should receive an update soon.

---

### Post by Primus1 on 2012-04-03
Got this warning popup on going online today:

"Firefox has determined that the following add-ons are known to cause stability or security problems:

IcedTea NPR Web Browser Plugin (using IcedTea6 1.9.13 (6b20-1.9.13-Oubuntu1~10.04.1))

For your protection, it is highly recommended that you restart with these add-ons disabled."

Then it asks me to restart Firefoxe with the plugin disabled, I have no done so yet. Does anyone know what this means please?


So the best thing to do is disable this plugin?

---

### Post by lovinglinux on 2012-04-03
> **Primus1 said:**
> Got this warning popup on going online today:

"Firefox has determined that the following add-ons are known to cause stability or security problems:

IcedTea NPR Web Browser Plugin (using IcedTea6 1.9.13 (6b20-1.9.13-Oubuntu1~10.04.1))

For your protection, it is highly recommended that you restart with these add-ons disabled."

Then it asks me to restart Firefoxe with the plugin disabled, I have no done so yet. Does anyone know what this means please?


So the best thing to do is disable this plugin?

It means you need to disable the plugin and restart Firefox.

Wait for an update to enable it again.

---

### Post by Primus1 on 2012-04-03
Thanks LL, I will do that now.

---

### Post by lovinglinux on 2012-04-04
Mozilla made a mistake with the type of blocking:

[http://blog.mozilla.com/addons/2012/04/04/update-on-java-blocklist/](http://blog.mozilla.com/addons/2012/04/04/update-on-java-blocklist/)

---

### Post by claracc on 2012-04-09
I see, six days have passed from firefox advice to disable icedtea plugin 6.1.9.13 because of security concerns.

I haven't yet received any security update for the plugin in order to fix the problem.

Do someone know if the security update is going to take long?

Meanwhile, in order to see java applets, do I install last java plugin from oracle?

It seems a war against open source software have started in two very important characteristics of web browsers:

First, to see java applets
Second, to see flash videos

---


---
title: "? Java ? problem on Ubuntu Lucid"
date: 2010-09-02
forum: General Help
---

### Post by Forgotten Path on 2010-09-02
Lately I am having an issue with a website that I have come to visit very frequently.  When I use the site to search, the links that take you to the next (or last, etc) page of the results do not work.

[http://www.geocaching.com/seek/nearest.aspx?state_id=34](http://www.geocaching.com/seek/nearest.aspx?state_id=34)

I have the same issue when using either FireFox 3.6 or Chrome 6.0.  I was wondering if anyone else would have the same issue, or would have any ideas for a fix/workaround.  My brother has confirmed that the issue does not exist running Windows Vista (either FireFox or IE - versions unknown).

This is driving me up the wall, and any help would be appreciated.

---

### Post by Forgotten Path on 2010-09-02
I've tried both Sun Java and OpenJDK, with they're respective plugins, no luck with either of them...

---

### Post by QIII on 2010-09-02
If you are talking about the "next" and "previous" links, they work for me.  So do the other links.

May I ask how you installed the plugin and which update it is?

---

### Post by Forgotten Path on 2010-09-02
Everything I have done is through Synaptic.  Right now I have the following installed:

openjdk-6-jre
openjdk-6-jre-lib
openjdk-6-jre-headless
icedtea6-plugin
icedtea-6-jre-cacao

Synaptic is showing the installed version as "6b18-1.8.1-0ubuntu1"
Thanks for the reply.

---

### Post by Forgotten Path on 2010-09-02
Lets see...

about: plugins on FireFox gives me:

```
IcedTea NPR Web Browser Plugin (using IcedTea6 1.8.1 (6b18-1.8.1-0ubuntu1))

    File: IcedTeaPlugin.so
    Version: 
    The IcedTea NPR Web Browser Plugin (using IcedTea6 1.8.1 (6b18-1.8.1-0ubuntu1)) executes Java applets.

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	IcedTea 	class,jar 	Yes
application/x-java-applet 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1.3 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.2.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.2.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.3 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.3.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.4 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.4.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.4.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.5 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.6 	IcedTea 	class,jar 	Yes
application/x-java-applet;jpi-version=1.6.0_18 	IcedTea 	class,jar 	Yes
application/x-java-bean 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1.3 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.2.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.2.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.3 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.3.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.4 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.4.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.4.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.5 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.6 	IcedTea 	class,jar 	Yes
application/x-java-bean;jpi-version=1.6.0_18 	IcedTea 	class,jar 	Yes
```

And on Chrome, about: plugins outputs both:


```
IcedTea NPR Web Browser Plugin (using IcedTea6 1.8.1 (6b18-1.8.1-0ubuntu1))
The IcedTea NPR Web Browser Plugin (using IcedTea6 1.8.1 (6b18-1.8.1-0ubuntu1)) executes Java applets.
Name:	IcedTea NPR Web Browser Plugin (using IcedTea6 1.8.1 (6b18-1.8.1-0ubuntu1))
Description:	The IcedTea NPR Web Browser Plugin (using IcedTea6 1.8.1 (6b18-1.8.1-0ubuntu1)) executes Java applets.
Version:	
Priority:	2
Location:	/usr/lib/jvm/java-6-openjdk/jre/lib/amd64/IcedTeaPlugin.so
 	 Disable
MIME types:	
MIME type	Description	File extensions
application/x-java-vm	IcedTea	
.class	.jar
application/x-java-applet	IcedTea	
.class	.jar
application/x-java-applet;version=1.1	IcedTea	
.class	.jar
application/x-java-applet;version=1.1.1	IcedTea	
.class	.jar
application/x-java-applet;version=1.1.2	IcedTea	
.class	.jar
application/x-java-applet;version=1.1.3	IcedTea	
.class	.jar
application/x-java-applet;version=1.2	IcedTea	
.class	.jar
application/x-java-applet;version=1.2.1	IcedTea	
.class	.jar
application/x-java-applet;version=1.2.2	IcedTea	
.class	.jar
application/x-java-applet;version=1.3	IcedTea	
.class	.jar
application/x-java-applet;version=1.3.1	IcedTea	
.class	.jar
application/x-java-applet;version=1.4	IcedTea	
.class	.jar
application/x-java-applet;version=1.4.1	IcedTea	
.class	.jar
application/x-java-applet;version=1.4.2	IcedTea	
.class	.jar
application/x-java-applet;version=1.5	IcedTea	
.class	.jar
application/x-java-applet;version=1.6	IcedTea	
.class	.jar
application/x-java-applet;jpi-version=1.6.0_18	IcedTea	
.class	.jar
application/x-java-bean	IcedTea	
.class	.jar
application/x-java-bean;version=1.1	IcedTea	
.class	.jar
application/x-java-bean;version=1.1.1	IcedTea	
.class	.jar
application/x-java-bean;version=1.1.2	IcedTea	
.class	.jar
application/x-java-bean;version=1.1.3	IcedTea	
.class	.jar
application/x-java-bean;version=1.2	IcedTea	
.class	.jar
application/x-java-bean;version=1.2.1	IcedTea	
.class	.jar
application/x-java-bean;version=1.2.2	IcedTea	
.class	.jar
application/x-java-bean;version=1.3	IcedTea	
.class	.jar
application/x-java-bean;version=1.3.1	IcedTea	
.class	.jar
application/x-java-bean;version=1.4	IcedTea	
.class	.jar
application/x-java-bean;version=1.4.1	IcedTea	
.class	.jar
application/x-java-bean;version=1.4.2	IcedTea	
.class	.jar
application/x-java-bean;version=1.5	IcedTea	
.class	.jar
application/x-java-bean;version=1.6	IcedTea	
.class	.jar
application/x-java-bean;jpi-version=1.6.0_18	IcedTea	
.class	.jar
application/x-java-vm-npruntime	IcedTea	
.
```

and

```
Java(TM) Plug-in 1.6.0_20
The next generation Java plug-in for Mozilla browsers.
Name:	Java(TM) Plug-in 1.6.0_20
Description:	The next generation Java plug-in for Mozilla browsers.
Version:	
Priority:	8
Location:	/usr/lib/jvm/java-6-sun-1.6.0.20/jre/lib/amd64/libnpjp2.so
 	 Disable
MIME types:	
MIME type	Description	File extensions
application/x-java-vm	Java™ Plug-in	
.
application/x-java-applet	Java™ Plug-in Applet	
.
application/x-java-applet;version=1.1	Java™ Plug-in	
.
application/x-java-applet;version=1.1.1	Java™ Plug-in	
.
application/x-java-applet;version=1.1.2	Java™ Plug-in	
.
application/x-java-applet;version=1.1.3	Java™ Plug-in	
.
application/x-java-applet;version=1.2	Java™ Plug-in	
.
application/x-java-applet;version=1.2.1	Java™ Plug-in	
.
application/x-java-applet;version=1.2.2	Java™ Plug-in	
.
application/x-java-applet;version=1.3	Java™ Plug-in	
.
application/x-java-applet;version=1.3.1	Java™ Plug-in	
.
application/x-java-applet;version=1.4	Java™ Plug-in	
.
application/x-java-applet;version=1.4.1	Java™ Plug-in	
.
application/x-java-applet;version=1.4.2	Java™ Plug-in	
.
application/x-java-applet;version=1.5	Java™ Plug-in	
.
application/x-java-applet;version=1.6	Java™ Plug-in	
.
application/x-java-applet;jpi-version=1.6.0_20	Java™ Plug-in	
.
application/x-java-bean	Java™ Plug-in JavaBeans	
.
application/x-java-bean;version=1.1	Java™ Plug-in	
.
application/x-java-bean;version=1.1.1	Java™ Plug-in	
.
application/x-java-bean;version=1.1.2	Java™ Plug-in	
.
application/x-java-bean;version=1.1.3	Java™ Plug-in	
.
application/x-java-bean;version=1.2	Java™ Plug-in	
.
application/x-java-bean;version=1.2.1	Java™ Plug-in	
.
application/x-java-bean;version=1.2.2	Java™ Plug-in	
.
application/x-java-bean;version=1.3	Java™ Plug-in	
.
application/x-java-bean;version=1.3.1	Java™ Plug-in	
.
application/x-java-bean;version=1.4	Java™ Plug-in	
.
application/x-java-bean;version=1.4.1	Java™ Plug-in	
.
application/x-java-bean;version=1.4.2	Java™ Plug-in	
.
application/x-java-bean;version=1.5	Java™ Plug-in	
.
application/x-java-bean;version=1.6	Java™ Plug-in	
.
application/x-java-bean;jpi-version=1.6.0_20	Java™ Plug-in	
.
application/x-java-vm-npruntime	Java™ Plug-in	
.
```

Not sure why Chrome has both plugins.  I'll try disabling one of them and see if I can get things working in Chrome, at least.

---

### Post by QIII on 2010-09-02
The entire world is not ready for OpenJDK and IcedTea.  It is entirely possible that your website is one of those.  It may simply not recognize that you have the Java plugin.

Having both IcedTea and the Java plugin is likely to cause problems.

I would uninstall IcedTea and OpenJDK, then install the Java plugin from Synaptic.  Unfortunately, the version in the repos is Update 20, and Update 21 is the most recent version.

If you want the most recent, you can follow the instructions here, but be very careful.  I suggest C&P making corrections to version update as necessary.

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

If that doesn't work out, the removal instructions are quite easy.

If neither Java installation words, uninstall sun-java6 and reinstall OpenJDK and IcedTea and try again.

---

### Post by Forgotten Path on 2010-09-02
Okay, the repository version is Update 20, so I'm going to try doing the manual installation of Update 21 tomorrow.  I'll let you know how it goes as soon as I get it done.  Thanks for all the help.

---

### Post by lykeion on 2010-09-03
The next/prev links are JavaScript. It's got nothing to do with Java plugin or JRE whatsoever.
[U]
[Java is not JavaScript]("http://www.dannyg.com/ref/javavsjavascript.html")[/U]

The reason why the links don't work in your browser is probably due to:
* You have disabled JavaScript in your browser
and/or:
* You are using some script-blocking browser plugin (like NoScript)

In Firefox you can check for JavaScript errors using Tools > Error Console > Errors tab

---

### Post by QIII on 2010-09-03
yeah.

I hadn't even considered that it might be JavaScript actually embedded in the HTML.

I will grin sheepishly now.

---

### Post by Forgotten Path on 2010-09-03
And I jumped into it in a hurry and didn't step back and think about the difference between Java and Javascript.  Theres more than one sheepish grin floating around.

FireFox and Chrome both have Javascript enabled, and I have no script blocking add-ons enabled in either browser.  The Error console in 'Fox gives me this:

```
Error: __doPostBack is not defined
Source File: javascript:__doPostBack('ctl00$ContentBody$pgrTop$lbGoToPage_2','')
Line: 1
```

when I try to open the second page of the search results.  Is there anything I can do about this?  Why would the Javascript work under Windows but not Ubuntu?  It also works fine on my Android phone...

EDIT:  Would it possibly have anything to do with an incorrect user-agent or the fact I am connected via a localhost proxy to my cell phone to receive internet?  All http requests are sent to port 8080 on my computer, forwarded to my Android phone, and then a Android app called Proxoid forwards the requests to the carriers 3G network.  In the process the phones user-agent is replaced with a "dummy" so I don't get mobile versions of web pages on my computer.  I really have no idea if this would make a difference, and I don't feel like it would, but I just wanted to put it out there...

---

### Post by Forgotten Path on 2010-09-03
Well, I just left some feedback with Groundspeak (the owners of the website).  I'm not sure if it will do any good since the problem seems limited to my machine, since QIII has no problem using the links.  I've noticed now that I get the exact same error in other parts of the site, while preforming different actions.  What is going on!??  :confused:

---

### Post by lykeion on 2010-09-04
> **Forgotten Path said:**
> The Error console in 'Fox gives me this:

```
Error: __doPostBack is not defined
Source File: javascript:__doPostBack('ctl00$ContentBody$pgrTop$lbGoToPage_2','')
Line: 1
```

when I try to open the second page of the search results.
When I check the html of the page, there's a Javascript function called *__doPostBack*, but your error seems to indicate that you miss that part. 
This is the function that handles the next/prev links.

I'd first try to clear the cache and try to load the page again:
Firefox > Tools > Clear Recent History...

If that doesn't work I'd check the html source to see if the Javascript function is there or not:
Load the page in Firefox > View > Page Source
I have the function on line 38

> **Forgotten Path said:**
> Would it possibly have anything to do with an incorrect user-agent or the fact I am connected via a localhost proxy to my cell phone to receive internet?  All http requests are sent to port 8080 on my computer, forwarded to my Android phone, and then a Android app called Proxoid forwards the requests to the carriers 3G network.  In the process the phones user-agent is replaced with a "dummy" so I don't get mobile versions of web pages on my computer.  I really have no idea if this would make a difference, and I don't feel like it would, but I just wanted to put it out there...
Neither user-agent nor proxy should be the culprit in this case. But someone else might know more about this than I do.

---

### Post by Forgotten Path on 2010-09-04
Okay, currently I am on the internet using a wifi connection at a local Atlanta Bread Co.  I'm having absolutely no problem at all using the links...

Line 38:

```
function __doPostBack(eventTarget, eventArgument) {
    if (!theForm.onsubmit || (theForm.onsubmit() != false)) {
        theForm.__EVENTTARGET.value = eventTarget;
        theForm.__EVENTARGUMENT.value = eventArgument;
        theForm.submit();
```

When I connect using my phone, the page source actually changes.  The function above at line 38 is gone, along with a large chunk of code just below it...

:confused:

---

### Post by scouser73 on 2010-09-04
> **QIII said:**
> If you are talking about the "next" and "previous" links, they work for me.  So do the other links.

May I ask how you installed the plugin and which update it is?

+1, the Next & Previous links also work well for me.

---

### Post by Forgotten Path on 2010-09-04
GOT IT!!

It was the user agent, apparently.  When Proxoid forwards requests to the 3G network, you have three choices as what to do with your user agent:  "Don't change", "Replace with dummy", and "Remove".  I changed the setting here to "Remove".  I previously had it set to "Replace with dummy".  I think its because geocaching.com doesn't recognize the user agent so they disable certain features on the site.  I tried this because of this line:

```
<!--[if lte IE 6]>
                    <div class="WarningMessage PhaseOut">
                        <p>Groundspeak is phasing out support for older browsers. Visit the <a href="http://support.groundspeak.com/index.php?pg=kb.page&id=215" title="View browser support information">Knowledge Books</a> for more information.</p>
                    </div>
                <![endif]-->

```

in the page source.  I'll post again if for some reason this stops working.

Thank you everyone for all your help.  I would have never noticed that line if lykeion hadn't asked me to check the page source. :D

---


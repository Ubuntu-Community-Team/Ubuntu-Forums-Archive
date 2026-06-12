---
title: "Firefox plugins don't work very well"
date: 2011-05-12
forum: General Help
---

### Post by gigaSproule on 2011-05-12
For some reason, none of the plugins for Firefox seem to work at all well, but they work fine in Chromium. The plugins in question, or at least the ones that I have found so far, are Flash and Java. I thought that Chromium and Firefox used the same plugins?

Is this a common problem, or have I just messed up both of my computers?

---

### Post by lithopsian on 2011-05-12
Chromium?  Or Google Chrome?  Not quite the same thing.  Google Chrome uses its own Flash plugin, so not the same as Firefox.

They should both be using the same Java plugin.

I don't have issues with either but I don't use a massive amount of Java or Flash.  What errors are you getting?  Which version of Firefox?  Can you post your about:plugins from both browers?

---

### Post by gigaSproule on 2011-05-12
Chromium, not Google Chrome. Try and keep my machines as Google free as possible.

Just on you tube, Chromium is a lot smoother on my netbook, not noticeable on my desktop, but that's probably to do with resources. However, it's still smoothed depending on the browser on my netbook.

I was trying Minecraft classic as my house mate is loving the full game and I just wanted to try it out. In Firefox, it downloads the files it needs, then just goes black, where as Chromium downloads the files needed and then loads up the game.

Just looked at the about:plugins page and there are 2 java applet plugins in Chromium...

Firefox:
Shockwave Flash

    File: libflashplayer.so
    Version: 
    Shockwave Flash 10.2 r159

IcedTea-Web Plugin (using IcedTea-Web 1.1pre (1.1~20110420-0ubuntu1))

    File: IcedTeaPlugin.so
    Version: 
    The IcedTea-Web Plugin executes Java applets.

Chromium:
Flash - Version: 10.2.159
Shockwave Flash 10.2 r159

Java - Version: 1.6.0.24
The next generation Java plug-in for Mozilla browsers.

IcedTea-Web Plugin (using IcedTea-Web 1.1pre (1.1~20110420-0ubuntu1))
The IcedTea-Web Plugin executes Java applets.

---

### Post by lovinglinux on 2011-05-12
Get [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/161939/") and run it. It will detect installed flash plugins, remove them and install the latest beta flash according to your system architecture and version. Additionally, it will apply some tweaks that should improve performance. If you still get that issue after running Flash-Aid, then go to the extension Help tab, click the "Generate Report" button and send me the results so I can analyze your situation.

---

### Post by gigaSproule on 2011-05-13
It's not improved anything for Flash. Hope it can prove something...

---

### Post by lovinglinux on 2011-05-13
> **gigaSproule said:**
> It's not improved anything for Flash. Hope it can prove something...

There is nothing wrong with your flash installation. You could try to use the Chrome plugin in Firefox. You can do that via Flash-Aid. Launch it, select the "Expert Mode" at the bottom, then open the "Installation Options" tab and change the version to "Google, from Chrome". Then execute the script. The extension will remove the current flash installation and copy the plugin from Chrome.

Could you please be more specific about what exactly doesn't work? Does it happen in all pages with flash or just particular ones?

---

### Post by gigaSproule on 2011-05-13
There isn't an option for Google. There Adobe Beta, Adobe Stable, Gnash and custom URL.

The problem is not so much of it doesn't work, just that it's really really slow. I wouldn't have a problem with it if it wasn't for Chromium working fine.

The thing that is not working is the Java plugin for Firefox, but is again working for Chromium.

---

### Post by lovinglinux on 2011-05-13
> **gigaSproule said:**
> There isn't an option for Google. There Adobe Beta, Adobe Stable, Gnash and custom URL.

The problem is not so much of it doesn't work, just that it's really really slow. I wouldn't have a problem with it if it wasn't for Chromium working fine.

The thing that is not working is the Java plugin for Firefox, but is again working for Chromium.

The option is not available because you are using Chromium and not Chrome, which means is not a Flash problem, because Chromium uses the same plugin as Firefox.

Could you please provide a link to a page that work slow on Firefox?

Also try to create a new Firefox profile. You can do that with the profile manager. Close Fireox and run the following from a termninal:

```
firefox -P
```

---

### Post by gigaSproule on 2011-05-13
It seems to happen with any site that has a flash video. Here is an example of one.

[http://www.penguspy.com/amnesia-the-dark-descent/](http://www.penguspy.com/amnesia-the-dark-descent/)

I will try creating a new profile now.

EDIT: It's not really done much to improve anything. I just tried Chromium again and although not perfect, probably because my netbook isn't plugged in, I still get about twice as many FPS as in Firefox.

---

### Post by lovinglinux on 2011-05-13
> **gigaSproule said:**
> It seems to happen with any site that has a flash video. Here is an example of one.

[http://www.penguspy.com/amnesia-the-dark-descent/](http://www.penguspy.com/amnesia-the-dark-descent/)

I will try creating a new profile now.

That particular video uses 80% of my Core2 Duo, either using Firefox or Chrome. When opening the video on YouTube, which is smaller, it uses 50%. Normally an YouTube video only uses 35% of my CPU.

---

### Post by gigaSproule on 2011-05-13
It seems to run just as well on you tube in Firefox and Chromium. Maybe it's just Firefox showing how it still lacks behind Chromium even with Firefox 4.

Do you know why there are 2 Java plugins for Chromium, but only the one for Firefox?

---

### Post by lovinglinux on 2011-05-13
> **gigaSproule said:**
> Do you know why there are 2 Java plugins for Chromium, but only the one for Firefox?

Nope.

---

### Post by gigaSproule on 2011-05-14
Ok, thanks for the help!

---


---
title: "Scrolling a web page with Firefox is slow except in Facebook"
date: 2010-02-27
forum: General Help
---

### Post by meamusta on 2010-02-27
Hi, there is quite a many threads about Firefox and scrolling, but they have not been helpful for me.

My Firefox is other vice pretty fast, but when I scroll up or down on almost any web page using mouse wheel or the scroll bar, page is moved step by step and screen is rendered (from bottom to up) for each step. Each page render takes about a quarter of a second, so the usability is very poor.

Scrolling down is a little bit better, but scrolling up, it is just frustrating.

Only on Facebook pages scrolling works like it should. There is no steps or clearly visible page rendering happening all the time. (Funny because in some thread a guy was reporting that scrolling in facebook particularly was slow)

I tried Firefox 3 and 3.5, both have the same issue.

I have disabled desktop visual effects and enabled the network.dns.disableIPv6 in Firefox configuration, like suggested in [http://www.thegeekstuff.com/2009/07/ubuntu-firefox-slow-solution/](http://www.thegeekstuff.com/2009/07/ubuntu-firefox-slow-solution/)

I have modified my xorg. Currently it is like:

Section "Module"
        Load "dri"
        Load "glx"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        SubSection "Display"
                Virtual 2944 1200
        EndSubSection
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "intel"
        Option          "UseFBDev"              "true"
        Option          "AccelMethod"           "UXA"
        Option          "MigrationHeuristic"    "greedy"
EndSection


My graphics card is "Mobile 915GM/GMS/910GML Express Graphics Controller".
I tried the old version 2.4 intel drivers for my graphics card, not a slightest change in scrolling behavior.

To be honest, I don't think it is the graphics driver or card problem because with for example Konqueror browser scrolling is fast and "continuous". And some sites like Facebook can be scrolled easily. (I have not noticed any other sites, but I suppose they exist)


If someone has an idea what else I could try to improve the usability of my Firefox, please tell me.

Changing the browser would be a solution, but I would miss tools like firebug.

---

### Post by DeadSuperHero on 2010-02-27
This sounds like a really weird problem, meamusta!

I would try running firefox from the terminal twice and post the output in this thread:

-Once where you just visit facebook and scroll up and down.
-Once where you visit some other site and scroll up and down.

Some things to consider:
-Would an update help fix it?
-Would using an alternative form of Firefox (IceCat, Swiftfox, IceWeasel, BurningDog) somehow work around the scrolling problem, while at the same time enabling you to use your Firebug extension?

---

### Post by tgalati4 on 2010-02-27
There is also an error console under "tools".  Open that up and look for messages to compare between the two sites.  Also, I use adblock and noscript plug-ins.  If one site has flash ads on the side bars, that can really slow scrolling, because the flash objects get reloaded.  Ever wonder why facebook became popular over myspace?

Also, any flash on the page can't take advantage of the graphics processor.  All flash rendering is computed by the CPU.  Hence the additional slowness.

---

### Post by meamusta on 2010-02-27
> **Mr. Psychopath said:**
> I would try running firefox from the terminal twice and post the output in this thread:

-Once where you just visit facebook and scroll up and down.
-Once where you visit some other site and scroll up and down.

Some things to consider:
-Would an update help fix it?
-Would using an alternative form of Firefox (IceCat, Swiftfox, IceWeasel, BurningDog) somehow work around the scrolling problem, while at the same time enabling you to use your Firebug extension?

I can run firefox from the console, but how to get the output?

Haven't tried the alternative Firefox browsers. Maybe I'll try them. Though, I just tried Chromium and it looks pretty good browser. It also has a Firebug like tool build in.

---

### Post by meamusta on 2010-02-28
This morning my computer didn't want to start with full graphics mode, so I restored my old xorg.conf file. Now the computer starts and there is no difference in browser behavior.

Current xorg.conf:

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        SubSection "Display"
                Virtual 2944 1200
        EndSubSection
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Option          "UseFBDev"              "true"
EndSection



On facebook site that is scrolling ok, firefox error console shows a long list of css errors like "Error in parsing value for property 'filter'. Declaration dropped." and "Expeted declaration but found '*'. Skipped to next declaration." and "Unknown property 'border-radius'. Declaration dropped."

On google search result page, where scrolling is poor, the error console shows one error message "Unkown property 'zoom'. Declaration dropped."

I quess this doesn't reveal much.

---

### Post by meamusta on 2010-02-28
Ok, now the scrolling problem is solved. I removed the virtual display subsection from the xorg.conf. It was not needed anymore.

Current xorg.conf:

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "intel"
        Option          "UseFBDev"              "true"
        Option          "AccelMethod"           "UXA"
        Option          "MigrationHeuristic"    "greedy"
EndSection

---

### Post by graytron on 2010-11-07
I'm running Ubuntu 10.04 server edition on an Intel Xeon quad core + ATI Radeon HD 4670 system with Compiz 3D composition and EXA 2D acceleration enabled.

Firefox scroll bar scrolling is noticeably sluggish if there are _any_ other maximized windows on other desktops. If I unmaximize all other windows firefox scrolls like a charm.

Anyone have similar experiences?

meamusta: If you restore the "Display" SubSection, will firefox show any difference when scrolling with and without other maximized windows?

---


---
title: "Internet explorer on ubuntu 10.04"
date: 2010-06-01
forum: General Help
---

### Post by rebel01.nilesh on 2010-06-01
hi,
although of no use IE7 is default browser for some websites and hence i want to install it on my ubuntu 10.04. I tried wine and IES but a weird problem occurs. Although i have wine 1.0.x version installed it prompts that the wine version is out of date and a certain 0.9.x version is required.

Please can someone guide me through the installation process please. IE7 or even 6 would be fine.

thanx

---

### Post by magneze on 2010-06-01
I would be amazed if this worked at all tbh considering how hooked into Windows IE is.

Firefox works fine for pretty much everything these days - no-one ignores a browser with 25% share.

What sites do you have issues with?

---

### Post by dino99 on 2010-06-01
i've never found an url refusing Firefox, no need of IE :P

install the latest wine and winetricks with this ppa:

[https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

---

### Post by rebel01.nilesh on 2010-06-01
hi,

i found out a way after 2 hectic days of searching and trying.

the way is as follows:

first open winecfg through terminal and open libraries tab. the add the following overrides

  	 	 	 	 	 	  **Wine DLL Overrides**

[Software\\Wine\\DllOverrides] 1233608859
"browseui"="native, builtin"
"comctl32"="builtin"
"crypt32"="native, builtin"
"gdiplus"="native"
"hhctrl.ocx"="native, builtin"
"hlink"="native, builtin"
"iernonce"="native, builtin"
"iexplore.exe"="native, builtin"
"itircl"="native, builtin"
"itss"="native, builtin"
"jscript"="native, builtin"
"mlang"="native, builtin"
"mshtml"="native, builtin"
"msimtf"="native,builtin"
"msxml3"="native,builtin"
"riched20"="native,builtin"
"riched32"="native,builtin"
"secur32"="native, builtin"
"shdoclc"="native, builtin"
"shdocvw"="native, builtin"
"shlwapi"="native, builtin"
"url"="native, builtin"
"urlmon"="native, builtin"
"usp10"="native, builtin"
"uxtheme"="native,builtin"
"wininet"="builtin"
"wintrust"="native, builtin"


now download and install winetricks from one of the repositories. 

now download ies4linux tar file and extrect it.
run ies4linux from the extracted folder by choosing the option run in terminal.
that shuld pretty much do it. hope it works for you.


there are shortcomings though. the mouse pointer doesnt work completely and dissapears at certain parts of the pages. so there you go.

---

### Post by philinux on 2010-06-01
For the problem sites try the user agent switcher addon to test.

[https://addons.mozilla.org/en-US/firefox/addon/59/](https://addons.mozilla.org/en-US/firefox/addon/59/)

---

### Post by JustinR on 2010-06-01
Hi,

According to the Wine Database on Internet Explorer 7, if you can get it working these features do not:

**About screen. Print/Print Preview. Creating favorites. Page properties. Enable/disable addons. IE Run Once. Flash. Search box. Some misalignment of icons in buttons. Find. Asterixes in password boxes show up as empty box characters. JavaScript**

So basically your web browsing experience will not go well, especially without Java Script and Flash!

If you still want to install it, they say to use WineTricks, search for it on google and download it. It doesn't say what else you need though.

For IE6 there is better success:

These things work:
Installation via Winetricks. HTML, JavaScript, CSS as on Windows. Toolbar and menu buttons. Normal installation works if the registry key HKEY_LOCAL_MACHINE->Software->Microsoft->Internet Explorer->Version is set to a value lower than 6 (forr instance, 5.0), but the app is unusable in this condition. Flash. Mouse pointer visible and works, unlike previous Wine releases. HTTPS appears to work

What does not:
Flash renders badly (animation works, but parts are missing). Sometimes the panels for Search/Favorites/Media do not appear, nut render on second attempt. Does not install an entry in the Wine Program menu. Installation by installer EXE.

What was not tested:
Silverlight, Java, ActiveX.

-

So Internet Explorer 6 seems like a better choice but both seem like bad browsing experiences.

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=25](http://appdb.winehq.org/objectManager.php?sClass=application&iId=25)

---

### Post by dnguyen1963 on 2010-06-01
> **dino99 said:**
> i've never found an url refusing Firefox, no need of IE :P

install the latest wine and winetricks with this ppa:

[https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

I have come across a few websites that require IE only...mostly, educational or library websites.

---

### Post by kaldor on 2010-06-01
> **philinux said:**
> For the problem sites try the user agent switcher addon to test.

[https://addons.mozilla.org/en-US/firefox/addon/59/](https://addons.mozilla.org/en-US/firefox/addon/59/)

In the very rare cases I had an issue, this always did the trick. I greatly recommend it.

---

### Post by irv on 2010-06-15
I have been fooling around with "PlayOnLinux" which is for games, but I installed IE7 and I got it to work except for logging on to Netflix. Here is a screen shot of what error I get when I try. Like I said it does work for browsing the Internet.
[ATTACH]160557[/ATTACH]

---

### Post by rggavubt on 2010-07-19
> **irv said:**
> I have been fooling around with "PlayOnLinux" which is for games, but I installed IE7 and I got it to work except for logging on to Netflix. Here is a screen shot of what error I get when I try. Like I said it does work for browsing the Internet.
[ATTACH]160557[/ATTACH]

I just installed IE7 on 10.04 using instructions on this website using PlayOnLinux also :

[http://weblog.scanyours.com/2010/05/30/howto-run-internet-explorer-7-within-ubuntu-10-04-lucid-lynx/]("http://weblog.scanyours.com/2010/05/30/howto-run-internet-explorer-7-within-ubuntu-10-04-lucid-lynx/")

IE7 works but not very good.  I can't get to the Netflix login screen.  I get "cant download %ws"

---

### Post by tekkidd on 2010-07-19
The easiest way to install IE7 into linux is to install Play On Linux ([http://www.playonlinux.com/en/](http://www.playonlinux.com/en/)). After you install the package you can go in and install IE7, but dont expect it to run well. I suggest though you first try to go to the site with Firefox and if it requires a plugin, install the plugin in wine alongside firefox in wine (Firefox has a Platinum rating from WineHQ)

---

### Post by xtheunknown0 on 2010-09-08
> **rebel01.nilesh said:**
> <snip>
the way is as follows:

first open winecfg through terminal and open libraries tab. the add the following overrides

  	 	 	 	 	 	  **Wine DLL Overrides**

[Software\\Wine\\DllOverrides] 1233608859

What do I do with this line? I added all the stuff below.

> **rebel01.nilesh said:**
> 
<snip>

now download and install winetricks from one of the repositories. 

now download ies4linux tar file and extrect it.
run ies4linux from the extracted folder by choosing the option run in terminal.
<snip>


I've followed pretty much all of the above instructions but I get [https://sites.google.com/site/xtheunknown0/linux-1](https://sites.google.com/site/xtheunknown0/linux-1)

What do I do next to get an IE working?

TIA,
xtheunknown0

---

### Post by wombatvvv on 2010-09-08
The only possible reason anyone should want to install IE7 is if they are a web developer and they need it for testing.

Firefox is miles better than IE7, and any website that doesn't support Firefox is not worth you visiting. Most modern websites do the opposite: work well in Firefox but have little bugs in IE7 and below.

As a web developer I can tell you as a fact that IE7 is a pile of crap. Chrome, Firefox and Opera are all miles ahead. IE8 is okay, but not as good as those others.

---

### Post by dirghrabadia on 2010-09-08
>  What do I do next to get an IE working? Make sure you have Wine installed already. If not, 

 ```

 sudo apt-get install wine
 
``` Then, carry out the following:
```

wget http://www.kegel.com/wine/winetricks

sh winetricks ie6


```

To run IE:
```
 wine iexplore 
```
IE7 didn't work out well for me. Hence ie6. But yeah, like others suggested, use IE only if its absolutely required and if the user agent switcher doesn't work for the site.

---

### Post by xtheunknown0 on 2010-09-08
> **dirghrabadia said:**
> <snip>
Then, carry out the following:
```

wget http://www.kegel.com/wine/winetricks

sh winetricks ie6


```

To run IE:
```
 wine iexplore 
```


Thanks! This worked :)
> **dirghrabadia said:**
> 
IE7 didn't work out well for me.

IE7 didn't work at all (for me).

---

### Post by borgulas on 2010-09-09
I'd also like IE6, 7 and 8 to work for web developing. Is there maybe an alternative way for testing? 

For example I use [https://browserlab.adobe.com/](https://browserlab.adobe.com/) now, which is also pretty neat. But it can 't be used for offline/local testing.

---

### Post by jetole on 2010-11-03
> **dino99 said:**
> i've never found an url refusing Firefox, no need of IE :P
> **wombatvvv said:**
> Firefox is miles better than IE7, and any website that doesn't support Firefox is not worth you visiting.

While I would agree with you 99% of the time and 99% of the time you are right, I have to disagree with you here. I'm a network admin and one of the sections of the company I work for uses Cisco Linksys SRW224G4 managed switches [http://www.cisco.com/en/US/products/ps9986/index.html](http://www.cisco.com/en/US/products/ps9986/index.html).

I must have access to these switches and unfortunately they have, by far, the most poor firmware I have ever witnessed. Among their flaws, they offer SSH access but the RSA modulus they use is literally smaller then the specifications for the allowed modulus access for SSH protocol IIRC. This means any recent openssh client will refuse to connect to it. They offer far less configuration options via SSH then they do in the web GUI. The web GUI is clunky at best. It is organized poorly, it's an administrators nightmare all around.

On top of everything else (and I am probably forgetting a ton here), the web based GUI will only work with IE. As far as I can tell this is not a design decision because it has nothing to do with the user agent presented. It will only work with IE because the page content is literally broken in all other browsers. You get hover overs that you can't click on. The main page content doesn't load. It's a mess. On top of that, if you read the source, you see very bad programming practice all over (for example a relative, parent directory URL in a href / <a href="../../page.html">).

Anyways... I can go on forever itemizing the flaws in this switch but my point was and is, I must have access to these switches at work and regardless of what browser I try and what user agent strings I set, this is a scenario where we have a page that requires IE and I must access it whether I want to or not.

"no need of IE" and "any website that doesn't support Firefox is not worth you visiting" does not apply to all situations unfortunately so please try and keep an open mind guys.

In the meantime, until the switches either get replaced or I find a way to install IE on Linux without needing a full VM, I guess I will keep using RDP / rdesktop to a windows machine to configure these switches.

---

### Post by wruslan on 2010-11-11
Try this URL:

[http://ubuntuforums.org/showthread.php?p=10101375#post10101375](http://ubuntuforums.org/showthread.php?p=10101375#post10101375)

It should help.

---

### Post by unix1980 on 2010-11-15
Agree with jetole.  I need access to a banking site where links are not clickable. User agent switching doesn't help.  I use IE on a virtualbox machine to work around this problem.

---

### Post by painteddeer on 2011-02-12
Not true that Firefox will get you everywhere... here's an example and as much as I would like to not have a windows computer I have to keep one because of this.

Thank you for your interest in the MLS System

The MLS System was specifically designed for Internet Explorer versions 6.0 or greater. Your browser version is not supported. To download the latest version of Internet Explorer, visit the Internet Explorer Downloads Web site.

Once Internet Explorer is installed, you can go to the MLS System site by typing [http://mibor.mlxtempo.com](http://mibor.mlxtempo.com) into the address bar.

The MLS System is the premiere web application that helps Realtors get the most out of their business.

© 2011 MarketLinx, Inc. All rights reserved.

---

### Post by cascade9 on 2011-02-13
@ painteddeer- have you tried a user agent switcher firefox add-on?

---

### Post by TWGTech on 2011-06-02
I know this is an old thread, but I agree that sometimes, sites are built only for IE. That includes many internal business sites, but also the IMM for IBM Blades works much better in IE than FF (can't even attach local drives in *nix), and ADP specifically requires IE - "This site requires Microsoft Internet Explorer Version 6.0 or higher.". Tell these companies to rebuild their products because everything runs better in FF, and see what you get =;.

I have also found printing FF to PDF to be pretty cumbersome (doesn't like to do frames (sometimes I can select it and other times not), and fonts are fuzzy), but I only do it a few times a month, so haven't really dug into it, but have tried some print to pdf products with not much better success.

I run Ubu, and have to keep a Win box available for just such items. Would be great to have a slick integration of IE for *nix. Better yet...MS needs to realize that there is a population that wants/needs to use its products and port to *nix.

Gotta get over the wars and realize that some of us need to use everything available, not just sit in one camp and bemoan the others. So...I'm off to give IE in wine a shot and see what happens. Thanks to all who offered suggestions to get this working. Hope to have some success.

---


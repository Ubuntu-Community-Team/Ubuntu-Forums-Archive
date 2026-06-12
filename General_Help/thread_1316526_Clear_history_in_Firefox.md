---
title: "Clear history in Firefox"
date: 2009-11-06
forum: General Help
---

### Post by Jaraxle on 2009-11-06
This is something that's been annoying me for quite awhile. Firefox seems to remember certain sites that I've visted no matter what I do. I have tried Tools|Clear Private Data, and Edit|Preferences|Privacy|Clear Now, etc. I also have it set to always clear my private data when I exit Firefox.

No matter what I do, I cannot get rid of these sites. Someone mentioned manually deleting the history.dat file from the command line. Is this file stored under .mozilla/firefox/ in my users directory? If so, I cannot find it. I've tried other locations, such as /etc/firefox-3.0 but cannot find history.dat

Could someone help me? Again, I have tried clearing the cache - have even manually deleted everything from the cache - but that didn't solve the problem. I think it has something to do with history, but needs to be removed manually. Clearing it from the browser doesn't work.

---

### Post by DapperMe17 on 2009-11-06
Hi,

I know this isn't an answer to your question, but

I suggest that you consider using the "distrust" extension. It runs everything in RAM, rather than writing to disk. 

It's a great extension for privacy.:popcorn:

---

### Post by tuwe on 2009-11-06
Flash stores cookies on your computer, too. You might want to look into your ~/.macromedia folder. 
Or use the better privacy addon, which allows you to remove these flash cookies.

[https://addons.mozilla.org/en-US/firefox/addon/6623](https://addons.mozilla.org/en-US/firefox/addon/6623)

---

### Post by muhannadfa on 2009-11-06
> **Jaraxle said:**
> This is something that's been annoying me for quite awhile. Firefox seems to remember certain sites that I've visted no matter what I do. I have tried Tools|Clear Private Data, and Edit|Preferences|Privacy|Clear Now, etc. I also have it set to always clear my private data when I exit Firefox.

No matter what I do, I cannot get rid of these sites. Someone mentioned manually deleting the history.dat file from the command line. Is this file stored under .mozilla/firefox/ in my users directory? If so, I cannot find it. I've tried other locations, such as /etc/firefox-3.0 but cannot find history.dat

Could someone help me? Again, I have tried clearing the cache - have even manually deleted everything from the cache - but that didn't solve the problem. I think it has something to do with history, but needs to be removed manually. Clearing it from the browser doesn't work.

u know what, u're a beta tester man, don't bother it 
about this, ubuntu support team will say, well it is newly released and every new thing has buggs
u know what ubuntu > every release of yours is buggy and ur buggs r majors 
Nvidia problems
Ati problems
Intel performance regression problems
audio problems
cannot connect internet
cannot delete beowser hx and private data > what secure system

every release same issues like the before and even worst >>> what r u coding or solving newly >> nothing

Close ur doors, & when u;re ready comeback

---

### Post by wilee-nilee on 2009-11-06
> **tuwe said:**
> Flash stores cookies on your computer, too. You might want to look into your ~/.macromedia folder. 
Or use the better privacy addon, which allows you to remove these flash cookies.

[https://addons.mozilla.org/en-US/firefox/addon/6623](https://addons.mozilla.org/en-US/firefox/addon/6623)

I like this one thanks. Distrust wont run in shiretoko.

---

### Post by tuwe on 2009-11-06
> **muhannadfa said:**
> u know what, u're a beta tester man, don't bother it 
about this, ubuntu support team will say, well it is newly released and every new thing has buggs
u know what ubuntu > every release of yours is buggy and ur buggs r majors 
Nvidia problems
Ati problems
Intel performance regression problems
audio problems
cannot connect internet
cannot delete beowser hx and private data > what secure system

every release same issues like the before and even worst >>> what r u coding or solving newly >> nothing

Close ur doors, & when u;re ready comeback

Dude, seriously. 
On my Macbook Pro i have Karmic running since alpha and decided to upgrade my PC at work when RC came out because everything runs so flawlessly. I haven't experienced one single problem ever. So stop spreading FUD.

---

### Post by muhannadfa on 2009-11-06
> **tuwe said:**
> Dude, seriously. 
On my Macbook Pro i have Karmic running since alpha and decided to upgrade my PC at work when RC came out because everything runs so flawlessly. I haven't experienced one single problem ever. So stop spreading FUD.

shame on u >>> it's sticky on support forums
so don't bother urself cause u're being untruthful,
zip it

---

### Post by peakshysteria on 2009-11-06
> **Jaraxle said:**
> This is something that's been annoying me for quite awhile. Firefox seems to remember certain sites that I've visted no matter what I do. I have tried Tools|Clear Private Data, and Edit|Preferences|Privacy|Clear Now, etc. I also have it set to always clear my private data when I exit Firefox.

No matter what I do, I cannot get rid of these sites. Someone mentioned manually deleting the history.dat file from the command line. Is this file stored under .mozilla/firefox/ in my users directory? If so, I cannot find it. I've tried other locations, such as /etc/firefox-3.0 but cannot find history.dat

Could someone help me? Again, I have tried clearing the cache - have even manually deleted everything from the cache - but that didn't solve the problem. I think it has something to do with history, but needs to be removed manually. Clearing it from the browser doesn't work.

I guess you might want to remove the so called Awesomebar? Google gives you lots of hits. But here the most common way to remove it:

Type **about:config** into the location bar and change the value **browser.urlbar.matchOnlyTyped** to true. After this, you need to restart Firefox. All this does is make it so that Firefox only searches the URLs you have typed and not the titles of pages.

Then once again type **about:config** into your address bar, hit the "okay" button when the security warning pops up, then paste **browser.urlbar.maxRichResults** in the open box, and hit the Enter key.

Double-click the result, and it'll let you change that digit. Change it to 0. Restart and thats it.

(Also remember to set remember my history for 0 Days). There should beno need for installing an addon for this.

Let's hear how it goes man :)

---

### Post by Jaraxle on 2009-11-06
peakshysteria: I followed your instructions and it worked like a charm! Thanks so much. I agree, you shouldn't need a plugin for something like this.

So what is the Awesomebar? Is that a nickname for Firefox remembering certain websites? Also, do I also need to check the box for Keep my history for at least 0 days under Preferences|Privacy? I had it unchecked (with the default value of 90 days), so I set it to 0 days and unchecked it again. I guess if it doesn't work I'll go and check it for 0 days, but I guess it should be the same.

Thanks again, I didn't think this post would start a small flame war! ;)

---

### Post by dbyjazz on 2009-11-06
this thread makes me lol

---

### Post by muhannadfa on 2009-11-06
> **Jaraxle said:**
> peakshysteria: I followed your instructions and it worked like a charm! Thanks so much. I agree, you shouldn't need a plugin for something like this.

So what is the Awesomebar? Is that a nickname for Firefox remembering certain websites? Also, do I also need to check the box for Keep my history for at least 0 days under Preferences|Privacy? I had it unchecked (with the default value of 90 days), so I set it to 0 days and unchecked it again. I guess if it doesn't work I'll go and check it for 0 days, but I guess it should be the same.

Thanks again, I didn't think this post would start a small flame war! ;)
):P great man :popcorn:

---

### Post by peakshysteria on 2009-11-06
> **Jaraxle said:**
> peakshysteria: I followed your instructions and it worked like a charm! Thanks so much. I agree, you shouldn't need a plugin for something like this.

So what is the Awesomebar? Is that a nickname for Firefox remembering certain websites? Also, do I also need to check the box for Keep my history for at least 0 days under Preferences|Privacy? I had it unchecked (with the default value of 90 days), so I set it to 0 days and unchecked it again. I guess if it doesn't work I'll go and check it for 0 days, but I guess it should be the same.

Thanks again, I didn't think this post would start a small flame war! ;)

Awesomebar; personally I hate it and have no use for it. Therefore I removed it. And so does a lot of other people. But then again there are more than a few that love it. Google it or head on over to Mozillazine and you might get the pros and cons of it. Glad to hear things are sorted in your end.

My Firefox Information

Last updated: Fri, 06 Nov 2009 21:21:36 GMT
User Agent: Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.1.5) Gecko/20091102 Firefox/3.5.5

**Extensions** (enabled: 20, disabled: 1; total: 21)
[list]
[*][Autohide](http://www.krickelkrackel.de/autohide/) 1.3.1 [disabled]
[*][Dictionary Switcher](http://en.design-noir.de/mozilla/dictionary-switcher/) 1.0 
[*][Dictionary Tooltip](http://www.dictionarytip.com) 1.5 
[*][DownloadHelper](http://www.downloadhelper.net) 4.6.4 
[*][Flashblock](http://flashblock.mozdev.org/) 1.5.11.2 
[*][Forecastfox](http://forecastfox.mozdev.org/) 0.9.10.1 
[*][Greasemonkey](http://www.greasespot.net/) 0.8.20090920.2 
[*][Highlighter](http://hashcolouredtabs.mozdev.org/highlighter/) 0.1.4 
[*][InfoLister](http://mozilla.doslash.org/infolister) 0.10.1 
[*][last.fmCode](http://mll2.free.fr/?p=42) 0.7b 
[*][Linkification](http://yellow5.us/firefox/linkification/) 1.3.6 
[*][Locationbar²](http://en.design-noir.de/mozilla/locationbar2/) 1.0.3 
[*][Nightly Tester Tools](http://www.oxymoronical.com/web/firefox/nightly) 2.0.2 
[*][Norsk Bokmål og Nynorsk ordliste]() 2.0.10.0 
[*][Personas](http://www.getpersonas.com/) 1.3.1 
[*][SmoothWheel (AMO)](http://smoothwheel.mozdev.org/) 0.44.19.20090811.3 
[*][Tab Mix Plus](http://tmp.garyr.net) 0.3.7.4pre.090516 
[*][Text Link](http://piro.sakura.ne.jp/xul/_textlink.html.en) 3.1.2009032701 
[*][Tiny Menu](http://trac.arantius.com/wiki/Extensions/TinyMenu) 2.0.1 
[*][Ubuntu Firefox Modifications]() 0.8 
[*][Update Channel Selector](http://www.oxymoronical.com/web/firefox/updatechannel) 1.5 
[/list]

**Themes** (6)
[list]
[*]Camifox [selected]
[*]Chromifox Basic 
[*]Daum Firefox&#50857; &#53580;&#47560; 
[*]Default 
[*]Dustfox 
[*]Elementary 
[/list]

**Plugins**
[list]
[*]Default Plugin
[*]Demo Print Plugin for unix/linux
[*]DivX® Web Player
[*]Java(TM) Plug-in 1.6.0_16-b01
[*]QuickTime Plug-in 7.2.0
[*]Shockwave Flash
[*]VLC Multimedia Plugin (compatible Totem 2.28.1)
[*]Windows Media Player Plug-in 10 (compatible; Totem)
[/list]

---


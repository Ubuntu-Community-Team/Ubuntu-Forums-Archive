---
title: "Firefox is eating my CPU"
date: 2010-05-11
forum: General Help
---

### Post by DeMus on 2010-05-11
Hi, I just noticed that Firefox really likes my CPU. I opened the same  page in Firefox and in Google Chrome and look at the difference in the attachment.
Mind that the 20% is not even the maximum I saw in the list. I even saw around 40% while Chrome (with the same page) although has several processes open they all stay at zero, or very close to it.
What can I do to lower the large appetite?

---

### Post by x C0MMAND0 x on 2010-05-11
My first thought and from experience is that often times Firefox is loaded with user-plugins.  If you have a lot of plugins installed, expect it to use a lot more of your CPU.  That is why Chrome often is "faster" because there are so few "plugins".  Do you have a lot of firefox plugins installed?

---

### Post by lovinglinux on 2010-05-11
> **x C0MMAND0 x said:**
> My first thought and from experience is that often times Firefox is loaded with user-plugins.  If you have a lot of plugins installed, expect it to use a lot more of your CPU.  That is why Chrome often is "faster" because there are so few "plugins".  Do you have a lot of firefox plugins installed?

What you are referring to are extensions, not plugins.

> With regard to web browsers, plug-ins differ from extensions.[1]  Plug-ins are generally external, binary components using the Netscape Plugin API (or ActiveX within Microsoft Internet Explorer) to handle new types of multimedia. Extensions, on the other hand, usually integrate with the browser's application logic or "chrome", that is, the interface of the browser itself. Since plug-ins and extensions both increase the utility of the original application, Mozilla uses the term "add-on" as an inclusive category of augmentation modules that consists of plug-ins, themes, and search engines. [http://en.wikipedia.org/wiki/Plug-in_%28computing%29](http://en.wikipedia.org/wiki/Plug-in_%28computing%29)

Although using many extensions can decrease overall browser performance, excessive CPU usage when idle is not a direct effect of the quantity of extensions installed. For instance I have right now 52 extensions installed and Firefox is only using 1% of my CPU while I type this. Nevertheless, an extension could have a bug that leads to excessive CPU usage. This could happen for example if the extension performs too many synchronous database reading/writing. I have experienced this myself with one of my extensions, that was interacting badly with a third-party extension on a very specific circumstance (closing the sidebar with the extension open, while having the third-party extension advanced settings enabled).

Anyway, to test if it is an extension issue, you should start Firefox in safe mode. See [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

Although it could be indeed an extension, most likely the problem is caused by a bad flash or javascript content on the page opened by Firefox.

Have you tested both browsers with the same page? Can you provide the link?

What version of Firefox you are using?

---

### Post by 2hot6ft2 on 2010-05-11
Firefox was bogging down on me too and firefox.bin was at the top like in your screenshot.
If I go by your signature for the system specs. then I would suggest this:

[Speed up Firefox by moving cache into RAM]("http://www.ultimateeditionoz.com/forum/viewtopic.php?f=23&t=216")

And some other things I did to speed it up
Firefox changes

1) Type “about:config” (no quotes) in the address bar in the browser.
2) Copy and paste the Preference Name into the Filter
3) For true/false entries right click and select Toggle OR double click on it.
4) For others right click and select Modify
You might have to create some of these entries by Right Click –> New –>Interger or Boolean in the lower section where the preferences are.

```
Preference Name						Type		Value

config.trim_on_minimize				New ->	boolean		true
browser.blink_allowed					""		false
browser.urlbar.doubleClickSelectsAll			""		true
network.dns.disableIPv6					""		false
browser.search.openintab				""		true
ui.submenuDelay					New ->	Integer		0
browser.sessionhistory.max_total_viewers		Integer		0 (was -1)
network.http.pipelining					boolean		true
network.http.proxy.pipelining				boolean		true
network.http.pipelining.maxrequests			Integer		some number like 10 (was 4)
nglayout.initialpaint.delay			New ->	Integer		0
content.notify.backoffcount			New ->	Integer		5
content.notify.interval				New ->	Integer		0
plugin.expose_full_path					boolean		true

```
Close and reopen firefox.

What some of them do
Reduce RAM usage to 10mb when Firefox is minimized
config.trim_on_minimize

Reduce the amount of RAM Firefox uses for it’s cache feature
browser.sessionhistory.max_total_viewers

Increase the Speed in Which Firefox loads pages
network.http.pipelining
network.http.proxy.pipelining
network.http.pipelining.maxrequests

The amount of time the browser waits before it acts on information it receives.
nglayout.initialpaint.delay
---------

If your CPU can be adjusted (scaled) not all can be.

Right click on the top panel and select Add to Panel
Select CPU Frequency Scaling Monitor
Click Add then Close
Left click on the new applet in the top panel and make sure it's not set to Powersave. Ondemand works a lot better.
You can always right click on it and select Remove from Panel if you want.
:popcorn:

---

### Post by lovinglinux on 2010-05-11
> **2hot6ft2 said:**
> Firefox was bogging down on me too and firefox.bin was at the top like in your screenshot.
If I go by your signature for the system specs. then I would suggest this:

[Speed up Firefox by moving cache into RAM]("http://www.ultimateeditionoz.com/forum/viewtopic.php?f=23&t=216")

And some other things I did to speed it up
Firefox changes

1) Type “about:config” (no quotes) in the address bar in the browser.
2) Copy and paste the Preference Name into the Filter
3) For true/false entries right click and select Toggle OR double click on it.
4) For others right click and select Modify
You might have to create some of these entries by Right Click –> New –>Interger or Boolean in the lower section where the preferences are.

```
Preference Name						Type		Value

config.trim_on_minimize				New ->	boolean		true
browser.blink_allowed					""		false
browser.urlbar.doubleClickSelectsAll			""		true
network.dns.disableIPv6					""		false
browser.search.openintab				""		true
ui.submenuDelay					New ->	Integer		0
browser.sessionhistory.max_total_viewers		Integer		0 (was -1)
network.http.pipelining					boolean		true
network.http.proxy.pipelining				boolean		true
network.http.pipelining.maxrequests			Integer		some number like 10 (was 4)
nglayout.initialpaint.delay			New ->	Integer		0
content.notify.backoffcount			New ->	Integer		5
content.notify.interval				New ->	Integer		0
plugin.expose_full_path					boolean		true

```
Close and reopen firefox.

What some of them do
Reduce RAM usage to 10mb when Firefox is minimized
config.trim_on_minimize

Reduce the amount of RAM Firefox uses for it’s cache feature
browser.sessionhistory.max_total_viewers

Increase the Speed in Which Firefox loads pages
network.http.pipelining
network.http.proxy.pipelining
network.http.pipelining.maxrequests

The amount of time the browser waits before it acts on information it receives.
nglayout.initialpaint.delay
---------

If your CPU can be adjusted (scaled) not all can be.

Right click on the top panel and select Add to Panel
Select CPU Frequency Scaling Monitor
Click Add then Close
Left click on the new applet in the top panel and make sure it's not set to Powersave. Ondemand works a lot better.
You can always right click on it and select Remove from Panel if you want.
:popcorn:

I have some comments about your suggestions. Please don't get me wrong. I'm not being pretentious and I'm not criticizing your suggestions, just trying to clarify some things.

First of all, the OP seems to have a CPU usage problem, not a memory leak problem. Your Firefox preferences tweaks suggestions are mostly related to how Firefox deals with memory and cache.

[config.trim_on_minimize](http://kb.mozillazine.org/Reducing_memory_usage_%28Firefox%29) is a Windows only preference, that does not reduce the amount of memory used, it just swaps memory from RAM to disk. Nevertheless, I have read some reports that when its swaps back to RAM, the original RAM usage is reduced, but it also cause Firefox to load slower. Anyway, it is a Windows only preference.

[browser.blink_allowed](http://kb.mozillazine.org/Browser.blink_allowed) - not relevant for this particular thread issue

[browser.urlbar.doubleClickSelectsAll](http://kb.mozillazine.org/Browser.urlbar.doubleClickSelectsAll) - not relevant for this particular thread issue and it is set as true by default

[network.dns.disableIPv6](http://kb.mozillazine.org/Network.dns.disableIPv6)	- highly recommended, but not related to CPU usage

browser.search.openintab - not relevant for this particular thread issue

ui.submenuDelay - not relevant for this particular thread issue and can be annoying when moving bookmarks

[browser.sessionhistory.max_total_viewers]("http://kb.mozillazine.org/Browser.sessionhistory.max_total_viewers") - set it to "0" prevents Firefox from storing pages in memory for the Back/Forward actions. If you really need to reduce memory usage, it would be better to limit the amount of memory used by this feature than disabling it completely, since this would force Firefox to load the page again when you use back and forward buttons.

[network.http.pipelining]("http://kb.mozillazine.org/Network.http.pipelining") - good to speed up page loading, but not related to CPU usage

[network.http.proxy.pipelining]("http://kb.mozillazine.org/Network.http.proxy.pipelining")  - good to speed up page loading (proxies only), but not related to CPU usage

[network.http.pipelining.maxrequests]("http://kb.mozillazine.org/Network.http.pipelining.maxrequests")	  - good to speed up page loading, but not related to CPU usage and the highest value you can set is 8. So your current settings doesn't work.
[URL="http://kb.mozillazine.org/Nglayout.initialpaint.delay"]

nglayout.initialpaint.delay[/URL] - although I include this option on my tutorial, I don't use it. Setting this to "0" doesn't speed up anything, just force Firefox to display the page as soon as it starts arriving, giving the impression that it is loading faster. Anyways, not related to CPU usage

[content.notify.backoffcount]("http://kb.mozillazine.org/Content.notify.backoffcount") - doesn't work if [content.notify.ontimer]("http://kb.mozillazine.org/Content.notify.ontimer") is not set to true

[content.notify.interval]("http://kb.mozillazine.org/Content.notify.interval") - doesn't work if [content.notify.ontimer]("http://kb.mozillazine.org/Content.notify.ontimer") is not set to true. Lowering the interval will lower the perceived page loading time but increase the total loading time, especially on slower connections. Values below 100,000 have a significant impact on performance and are not recommended.

[plugin.expose_full_path]("http://kb.mozillazine.org/About:plugins") - not relevant for this particular thread issue

Bottom line, if you have memory leak issues, I would recommend tweaking only one preference, which is [browser.cache.memory.capacity](http://kb.mozillazine.org/Browser.cache.memory.capacity). Select a value according to your RAM capacity and you should be fine.

---

### Post by DeMus on 2010-05-12
Thanks guys, I will look into it. As I wrote I had opened the same page, General Help on the Ubuntu forums, in both browsers and then took the screenshot.
In both browser I use add-ons or Extensions like:

_Firefox_
Reloadevery                    
Speed-dial                     
Ubuntu Firefox Modifications   

_Chrome_
Auto-reload
Speed-dial
Tabs to front

So there are not that many although the reload one is continues (every 10 seconds) reloading the page.
But that is on both browsers.

I will see if some of the tweaks work for me. Thanks for all your answers.

---


---
title: "Firefox dead slow on UbuntuFormum but not most elsewhere"
date: 2011-07-11
forum: General Help
---

### Post by held7over on 2011-07-11
ubuntu 10.10  Firefox 3.6.18

I have been running ubuntu 10.10 since it came out and this problem just started for me in the last couple of weeks and seems to be growing worse.

Firefox was still stalled after 2 minutes of waiting to create this Post. The way I finally got here was to hit the manual refresh. Clicking on the URL Line and hitting Enter didn't help. I have noticed this happens on a few other sites, as well, but for the rest of them, Firefox seems fast.

Chromium jumps onto the UbuntuForum bang fast. 

I applied the fix I found at [www.ubuntugeek.com/how-to-fix-firefox-slow-problem-in-ubuntu-10-04lucid.html](www.ubuntugeek.com/how-to-fix-firefox-slow-problem-in-ubuntu-10-04lucid.html)   --It didn't appear to help. However just now, when I clicked the bookmark of that URL to get the URL to paste here, it loaded darn fast, whereas last time I waited 3 to 4 minutes for it.

Does anyone know what is happening and how to fix this for all sites, especially UbuntuForum?

Thanks! :D

---

### Post by An Sanct on 2011-07-11
Hm :) this might be because UbuntuForums is driven with [YUI]("http://developer.yahoo.com/yui/3/") (Yahoo User Interface) ... check out this [samples page]("http://developer.yahoo.com/yui/3/examples/") and you will see if that is the reason, if so, switch to a newer version of Firefox, since javascript performance was greatly updated.

---

### Post by conradin on 2011-07-11
[http://www.ubuntugeek.com/how-to-install-firefox-4-in-ubuntu-using-ppa.html](http://www.ubuntugeek.com/how-to-install-firefox-4-in-ubuntu-using-ppa.html)

Using firefox 4?
When Firefox goes buggy, I keep Epiphany around.

---

### Post by DawieS on 2011-07-11
I also block *yui.yahooapis.com* with Adblock-Plus while browsing the forum. This speeds up the browsing considerably.

The block has to be disabled before posting on the forum, and re-enabled afterwards.
(2 extra mouse-clicks) :grin:

---

### Post by An Sanct on 2011-07-12
DawieS: Wow, interesting! ... Why would one block YUI? (I am really interested, read on!)

AFAIK... all the google API, yahoo API and other "common" resources are reused after once loaded, blocking them would be ... well ... nonsense ... So, Why I want to know (!) are there any security related issues, I don't know about, concerning these repositories?????

---

### Post by DawieS on 2011-07-12
> **An Sanct said:**
> DawieS: Wow, interesting! ... Why would one block YUI? (I am really interested, read on!)

AFAIK... all the google API, yahoo API and other "common" resources are reused after once loaded, blocking them would be ... well ... nonsense ... So, Why I want to know (!) are there any security related issues, I don't know about, concerning these repositories?????
I stand corrected. The real time saver on the forums is the filter *google-analytics.com* that I keep permanently blocked.

It also depends how you manage your Firefox history settings. Mine is set to delete the cache on exit, which keeps my system clean and free from potentially unwanted scripts. If I am not going to post on the forum, keeping the filter *yui.yahooapis.com* enabled, saves me from downloading the script. Then there are also the various other websites (for example Skype) that other forum members may have embedded in their signatures, and get connected as soon as you open the page.

Sometimes some of these servers may be somewhat overloaded, and may take a long time to respond, resulting in slow browsing speeds. If these (unnecessary) connections are blocked with Adblock-Plus, the browsing speed is drastically improved.

I guess that Mozilla has some deal with Google, due to the fact that you are unable to (completely) block Google from within Firefox. For that you have to use a firewall, blocking the various Google websites (with a new one popping up every second week) on outgoing connections. In principle I don't have anything against being spied on continuously, except that I have to pay for the bandwidth used in the spying activities.

I must say that I find it somewhat embarrassing when logging into my bank account on a secure connection, and see the Google connection (that was following me around for the past hour) immediately follows suit, and swaps the current connection for a secure one. Now even if I could fully trust Google with my banking details, history has proven that there are no guarantees that Google will not be hacked again in future, and my details end up in the wrong hands.

---

### Post by lovinglinux on 2011-07-12
> **DawieS said:**
> I stand corrected. The real time saver on the forums is the filter *google-analytics.com* that I keep permanently blocked.

It also depends how you manage your Firefox history settings. Mine is set to delete the cache on exit, which keeps my system clean and free from potentially unwanted scripts. If I am not going to post on the forum, keeping the filter *yui.yahooapis.com* enabled, saves me from downloading the script. Then there are also the various other websites (for example Skype) that other forum members may have embedded in their signatures, and get connected as soon as you open the page.

Sometimes some of these servers may be somewhat overloaded, and may take a long time to respond, resulting in slow browsing speeds. If these (unnecessary) connections are blocked with Adblock-Plus, the browsing speed is drastically improved.

I guess that Mozilla has some deal with Google, due to the fact that you are unable to (completely) block Google from within Firefox. For that you have to use a firewall, blocking the various Google websites (with a new one popping up every second week) on outgoing connections. In principle I don't have anything against being spied on continuously, except that I have to pay for the bandwidth used in the spying activities.

I must say that I find it somewhat embarrassing when logging into my bank account on a secure connection, and see the Google connection (that was following me around for the past hour) immediately follows suit, and swaps the current connection for a secure one. Now even if I could fully trust Google with my banking details, history has proven that there are no guarantees that Google will not be hacked again in future, and my details end up in the wrong hands.

There are several extensions that can be used to block Google Analytics and other web sites. For instance, [Ghostery]("https://addons.mozilla.org/en-US/firefox/addon/ghostery/") and even AdBlock Plus.

---

### Post by DawieS on 2011-07-12
> **lovinglinux said:**
> There are several extensions that can be used to block Google Analytics and other web sites. For instance, [Ghostery]("https://addons.mozilla.org/en-US/firefox/addon/ghostery/") and even AdBlock Plus.
You have not read my posts carefully.#-o

I say again, I do USE Adblock-Plus, which is what I recommended to the OP to increase browsing speed. However, all these add-on blockers can only block sites nominated (or referred) on the normal browsing http: pages, and NOT sites which are hard-coded into the Browser, some of which may be modified on the about:config page.

I have once done a test and removed all references to Google in the about:config page. Firefox did NOT run.:wink:

---

### Post by lovinglinux on 2011-07-12
> **DawieS said:**
> You have not read my posts carefully.#-o

I say again, I do USE Adblock-Plus, which is what I recommended to the OP to increase browsing speed. However, all these add-on blockers can only block sites nominated (or referred) on the normal browsing http: pages, and NOT sites which are hard-coded into the Browser, some of which may be modified on the about:config page.

I have once done a test and removed all references to Google in the about:config page. Firefox did NOT run.:wink:

I know you have AdBlock Plus. I was just saying that Firefox allows to block anything you want, with the help of an extension.

What do you mean by sites hard-coded in the browser? Please give examples.

---

### Post by An Sanct on 2011-07-12
I'm listening here too ... Using FF 8.0a1 and concerned about security (no-I am not American ...) which site can you not block with adblock plus?

PS. the only F I have seen in Firefox was, that it prevented me to access my own server on port 203 (other site, other ports...) and I was like WH'U'T? FF said, It prevented me from browsing that resource, because it was a security risk ... (me, being willing to take it - any time ...

---

### Post by DawieS on 2011-07-12
> **lovinglinux said:**
> I know you have AdBlock Plus. I was just saying that Firefox allows to block anything you want, with the help of an extension.

What do you mean by sites hard-coded in the browser? Please give examples.
If you use a blank screen as your home page (about:blank), and remove all default search engines, when Firefox is started, 2 connection attempts are immediately made (before you can even start typing a letter):
- to Mozilla
- to Google
Unless blocked by a firewall, Google will stay with you where-ever you go browsing further. Mozzilla will drop off after a while.

At least, this is what is happening on my default 10.04 installation. Why don't you check it out for yourself?

---

### Post by lovinglinux on 2011-07-12
> **DawieS said:**
> If you use a blank screen as your home page (about:blank), and remove all default search engines, when Firefox is started, 2 connection attempts are immediately made (before you can even start typing a letter):
- to Mozilla
- to Google
Unless blocked by a firewall, Google will stay with you where-ever you go browsing further. Mozzilla will drop off after a while.

At least, this is what is happening on my default 10.04 installation. Why don't you check it out for yourself?

If you are using Firefox 3.6.x, then there is a feature that allows to type just a web site name in the address bar and get automatically redirected to the correct domain. If the browser cannot identify the site correctly, it queries Google. To disable that see [http://kb.mozillazine.org/Keyword.URL](http://kb.mozillazine.org/Keyword.URL). This feature has been removed in Firefox 4 or above. You can regain such functionality using the [Browse By Name]("https://addons.mozilla.org/en-US/firefox/addon/222531/") extension.

A connection is made to Google when you visit a site, with safe browsing enabled. To disable that, open the preferences, click the Security tab, untick the options "Block reported attack sites" and "Block reported web forgeries".

That is all you need to stop querying Google. There is also the search suggestions, but if you removed the Google search engine, then there is nothing to worry about it. You can disable it in Firefox preferences anyway.

The *about:startup* with Google search is a feature of Ubuntu Firefox Modifications extension (aka ubufox). That is because Canonical has a deal with Google to get money from searches. You can disable it by simply disabling the add-on in **about:addons**. Mozilla has also a deal with Google, so when you disable ubufox, the startup page is replaced by the one from Firefox. Anyway, I don't think any of those startup pages connect to Google unless you use the search tool there.

Firefox also has a geolocation feature, that uses Google. However, that is only activated if you allow a site that request your location information. See [http://www.mozilla.com/en-US/firefox/geolocation/](http://www.mozilla.com/en-US/firefox/geolocation/)

---

### Post by DawieS on 2011-07-12
> **lovinglinux said:**
> If you are using Firefox 3.6.x, then there is a feature that allows to type just a web site name in the address bar and get automatically redirected to the correct domain. If the browser cannot identify the site correctly, it queries Google. To disable that see [http://kb.mozillazine.org/Keyword.URL](http://kb.mozillazine.org/Keyword.URL). This feature has been removed in Firefox 4 or above. You can regain such functionality using the [Browse By Name]("https://addons.mozilla.org/en-US/firefox/addon/222531/") extension.

A connection is made to Google when you visit a site, with safe browsing enabled. To disable that, open the preferences, click the Security tab, untick the options "Block reported attack sites" and "Block reported web forgeries".

That is all you need to stop querying Google. There is also the search suggestions, but if you removed the Google search engine, then there is nothing to worry about it. You can disable it in Firefox preferences anyway.

The *about:startup* with Google search is a feature of Ubuntu Firefox Modifications extension (aka ubufox). That is because Canonical has a deal with Google to get money from searches. You can disable it by simply disabling the add-on in **about:addons**. Mozilla has also a deal with Google, so when you disable ubufox, the startup page is replaced by the one from Firefox. Anyway, I don't think any of those startup pages connect to Google unless you use the search tool there.

Firefox also has a geolocation feature, that uses Google. However, that is only activated if you allow a site that request your location information. See [http://www.mozilla.com/en-US/firefox/geolocation/](http://www.mozilla.com/en-US/firefox/geolocation/)
Thanks a lot for your comprehensive reply.:smile:

As I have said, I don't really have privacy issues when doing normal browsing. After all, none of us would get good answers when doing a search, if all of us are continuously blocking access to the search engines. They would not be able to generate any meaningful results! All things considered, it is a small price to pay for the usefulness of the total system.

It is also good to know that we have all the means available in the form of various tools, to sometimes take action to ensure that private information stays private.

---


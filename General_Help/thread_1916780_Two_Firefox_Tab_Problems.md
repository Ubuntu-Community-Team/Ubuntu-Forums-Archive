---
title: "Two Firefox Tab Problems"
date: 2012-01-28
forum: General Help
---

### Post by professorYaffle on 2012-01-28
I've recently upgraded straight from maverick to oneiric, which included the upgrade to the new sequence of firefoxes (9.0.1 at the moment). There's two problems I have with the tabs that I need some help to get to the bottom of.

Firstly: Tab Widths. I've always had browser.tabs.tabMinWidth set to 10 in about:config so that tabs will squash down to about the size of the icon before horizontal scrolling kicks in (which, along with the hashColouredTabs addon works very nicely.) That setting is now being ignored. I've tried setting it to all kinds of values, but it has no effect. Tabs are a minimum of about eight letters, an ellipsis and the icon wide.

Secondly: The new tab button has disappeared. I've read plenty about it migrating from the main toolbar into a + sign on the row of tabs. This is not the case for me. It's gone from the old place, but not appeared in the new. In the tab row I have the left scroll button, all the tabs, the right scroll button, the pull down menu button for selecting a specific tab, and the X button for closing the current tab. (That's been changed in about:config to 3.) Definitely no "+" anywhere.

I've tried disabling all my addons and switching to the default appearance, but if makes no difference to the tab behaviour.

What's really exercising me about this is that, at work I have a very similar setup. It was also recently upgraded from maverick to oneiric, also involving the same upgrade to the new firefox (also now 9.0.1). I have a similar set of plugins and addons etc. (not exactly the same) but it has a different accumulated history. It's working fine. The tabs are all squashing down to just a favicon or so wide, and the new tab button is a "+" on the right of the other tabs, just before the pulldown menu and the close tab X. I can't work out what the difference is between that and my system at home! Does anyone have any suggestions as to where to start looking?

---

### Post by wolfen69 on 2012-01-28
Try closing firefox, go into /home, and delete your .mozilla folder.

---

### Post by professorYaffle on 2012-01-30
Hi wolfen69,

Er, yeah that will work but it's not the solution I'm after. I tried it, just to make sure, by moving ~/.mozilla out of the way, but then reverted it back into place as I've got a lot of accumulated history in there that I don't want to lose - actual browsing history, remembered passwords, a hundred or so saved sessions in the session saver plugin, not to mention wanting to avoid the hassle of finding and reinstalling all thirty or so addons I've got.

I don't think I've actually lost data like that since the phoenix/firebird/firefox naming changes (and maybe not even then - kind of hard to remember that far back.)

I'm looking for some more detailed help on how to unpick what's gone wrong from my current setup. (I've never delved deeper into firefox than tweaking about:config.)

---

### Post by lovinglinux on 2012-02-01
The tab+ button is there, it is probably just hidden somewhere. Right click on the toolbar, select "Customize" to open the customization dialog. In the dialog, click "Restore Default Set". This will reset your toolbars and buttons, including the tab+ button.

---

### Post by professorYaffle on 2012-02-02
Thanks for that, lovinglinux. That did indeed bring the TAB+ button back. I'll have to reorganise my extra buttons etc. again, but that's a small price compared to losing all the history.

However, it hasn't made any difference to the minimum tab width problem, so I'm only half way there.

---

### Post by lovinglinux on 2012-02-02
> **professorYaffle said:**
> Thanks for that, lovinglinux. That did indeed bring the TAB+ button back. I'll have to reorganise my extra buttons etc. again, but that's a small price compared to losing all the history.

However, it hasn't made any difference to the minimum tab width problem, so I'm only half way there.

The browser.tabs.tabMinWidth has been deprecated.

[http://kb.mozillazine.org/Browser.tabs.tabMinWidth](http://kb.mozillazine.org/Browser.tabs.tabMinWidth)


The easier way is to use Custom Tab Width extension:

[https://addons.mozilla.org/en-US/firefox/addon/custom-tab-width/](https://addons.mozilla.org/en-US/firefox/addon/custom-tab-width/)

---

### Post by professorYaffle on 2012-02-03
> **lovinglinux said:**
> The browser.tabs.tabMinWidth has been deprecated.
[http://kb.mozillazine.org/Browser.tabs.tabMinWidth](http://kb.mozillazine.org/Browser.tabs.tabMinWidth)

The easier way is to use Custom Tab Width extension:
[https://addons.mozilla.org/en-US/firefox/addon/custom-tab-width/](https://addons.mozilla.org/en-US/firefox/addon/custom-tab-width/)
That's exactly what I needed to know. Thankyou very much for that, much appreciated.

Cheers!

---

### Post by lovinglinux on 2012-02-04
> **professorYaffle said:**
> That's exactly what I needed to know. Thankyou very much for that, much appreciated.

Cheers!

You are welcome.

---


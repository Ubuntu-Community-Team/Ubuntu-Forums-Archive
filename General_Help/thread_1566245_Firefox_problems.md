---
title: "Firefox problems"
date: 2010-09-02
forum: General Help
---

### Post by hasi-titan on 2010-09-02
Hey guys,

I have a problem with my firefox. Everytime I start it starts on the following page:                                   

chrome://ubufox/locale/ubufox.properties


and with this text: 

                                  helloMessage=Hello World! helloMessageTitle=Hello prefMessage=Int Pref Value: %d [EMAIL="extensions.ubufox@ubuntu.com.descri"]extensions.ubufox@ubuntu.com.descri[/EMAIL]ption=Ubuntu Firefox Pack. ubufox.pluginWizard.availablePluginsPage.description.label=Choose a plugin for media type app.releaseNotesURL=http://www.ubuntu.com/getubuntu/releasenotes/1004 browser.startup.homepage=about:home browser.throbber.url=file:///usr/share/ubuntu-artwork/home/index.html app.update.url.details=file:///usr/share/ubuntu-artwork/home/index.html startup.homepage_override_url=about:blank startup.homepage_welcome_url=about:blank ubufox.pluginWizard.description.notfound=No description found in plugin database. \nReport a bug to [EMAIL="ubuntu-mozillateam@lists.ubuntu.com"]ubuntu-mozillateam@lists.ubuntu.com[/EMAIL]

 I had it once before and I fixed by deleting my Firefox profile in the terminal. That was only a couple of days ago, but I actually do not wan't to loose all my bookmarks and Add-Ons again. Somebody has an idea?
I am still a noob with Ubuntu.


Thanks in advance

---

### Post by bobcollard on 2010-09-02
Under Edit>Preferences>General tab: change your Home Page to something different or find a page you want as a home page and drag the icon from the Address to the little Home Icon and answer Yes.  See attached as example.

---

### Post by hasi-titan on 2010-09-02
Mh thanks for that. Sometimes the easiest solution is the best. Can't believe that I did not thought about that. 

Thank you.

---

### Post by bobcollard on 2010-09-02
> **hasi-titan said:**
> Mh thanks for that. Sometimes the easiest solution is the best. Can't believe that I did not thought about that. 

Thank you.
You are welcome.  Please use Quick Links above and mark this [Solved] so others may benefit from your thread..

---

### Post by y2ken on 2010-11-19
I have the same problem with my Homepage, it keeps changing to the same "chrome://ubufox/locale/ubufox.properties" Homepage. The weird thing is that I'm not using Ubuntu, I'm using Firefox in Win7. [But I do have an Ubuntu Virtualbox OS installed]
I keep changing it back to my regular homepage and it keeps changing back to "chrome://ubufox/locale/ubufox.properties"
???

---

### Post by bobcollard on 2010-11-19
> **y2ken said:**
> I have the same problem with my Homepage, it keeps changing to the same "chrome://ubufox/locale/ubufox.properties" Homepage. The weird thing is that I'm not using Ubuntu, I'm using Firefox in Win7. [But I do have an Ubuntu Virtualbox OS installed]
I keep changing it back to my regular homepage and it keeps changing back to "chrome://ubufox/locale/ubufox.properties"
???
Under Edit>Preferences>General Tab revise "When Firefox Starts:" to [Show My Home Page] then type your home address into the box or on the Browser, find your home page and drag the icon in the address bar to the Home Icon and answer (Yes.)

---

### Post by DigDesignEng on 2013-03-20
I disabled "Ubuntu Firefox Modifications" and this resolved my problem. I have the add-on "New Tab URL" set so "Default URL for new tabs" is set to "Home Page". My Firefox Preferences "Home Page" setting is set to "Mozilla Firefox Start Page", but no URL is given. If I enter "www.google.com/firefox" I get what is supposed to be the Mozilla Firefox Start Page, but if I enter "about:home" in the navigation toolbar, I get a different web page. I don't think about:home is actually a web page on the internet, but a local web page that is embedded in Firefox. I also think that ubufox is somehow involved in this problem. So someone found a way to mask the problem and you mark it "Solved" when, actually something is still broken. Perhaps someone smarter than me can add more information so we all can fully understand what is going on.

Oh yeah, it's an old post. But people are still reading it. People still need answers even though the original poster has long gone. Otherwise please delete the post because it no longer applies.

---

### Post by oldos2er on 2013-03-21
[COLOR=#000000]If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.[/COLOR]

---


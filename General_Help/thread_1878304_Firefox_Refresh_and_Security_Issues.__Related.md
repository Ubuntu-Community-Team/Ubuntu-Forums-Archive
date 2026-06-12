---
title: "Firefox Refresh and Security Issues.  Related?"
date: 2011-11-09
forum: General Help
---

### Post by Randy Schilling on 2011-11-09
I'm setting up newly installed U11.10 and working under its Unity desktop.

My Firefox does not seem to refresh web pages regularly. 
I refresh manually using F5, Ctrl+R, or Ctrl+F5 (Thanks Vasa1.).
Do I need to change a setting or add a plug-in? 

Under the Edit>Preferences>Content, I'm blocking pop-up windows, 
loading images automatically, and JavaScript is enabled. 

I installed the Noscripts extension to Firefox and while it was enabled
Firefox's status bar reported "Scripts currently forbidden".
Things were happening that I did not understand 
(I couldn't open new webpage for example) so I disabled Noscripts.
Things are back to normal.

I find its not easy reading about security. I don't have the time right now to do a thorough reading of NoScripts' FAQ so could you please tell me
simply how to set it up.  Here is what I think youy might want to know.
Generally, if I go to a website, I trust it. I don't pirate anything or go to XXX sites. 

Is the Whitelist the list of trusted websites and do I have to constantly update it? 


Many thanks and regards - Randy

---

### Post by lovinglinux on 2011-11-09
You can change the cache behavior in the about:config.

See [http://kb.mozillazine.org/Browser.cache.check_doc_frequency](http://kb.mozillazine.org/Browser.cache.check_doc_frequency)

You can also use an add-on like [Better Cache](https://addons.mozilla.org/en-US/firefox/addon/6371/)

---

### Post by Randy Schilling on 2011-11-09
Thanks Lovinglinux.

The critical instruction at the website  given in your post is this:

Edit -> Preferences -> Advanced -> Cache -> Compare the page in the cache to the page on the network: 

Cache, however,  is not available under my Advanced tab.   

I installed the BetterCache and I changed the option  under
  "How often to check for a newer version of cached page" 
from Automatic to Everytime a site Opens.  I'm not sure this is what I want though.
I'm not sure I should have changed from Automatic.

I can explain the behavior I want using this website as an example.  As Firefox WAS setup, I had to do
a manual refresh (F5) to check for responses to my posts.  I would prefer if a refresh took place automatically when an individual like yourself is kind enough to respond to my post.

Another example.  I use the  website to track the Packer football games
whenever they're game is not on TV here in Arkansas.
With Firefox under Windows 7, my page was updated automatically as each play occurs.
Not so under my Firefox running here under Ubuntu.

Do you think I should have stayed with the Automatic setting to get the behavior I want?

Many thanks for taking the time - Randy

P.S.  For the first time I have an idea of what caching is about.  Thanks

---

### Post by lovinglinux on 2011-11-09
> **Randy Schilling said:**
> Thanks Lovinglinux.

The critical instruction at the website  given in your post is this:

Edit -> Preferences -> Advanced -> Cache -> Compare the page in the cache to the page on the network: 

Cache, however,  is not available under my Advanced tab.   

I installed the BetterCache and I changed the option  under
  "How often to check for a newer version of cached page" 
from Automatic to Everytime a site Opens.  I'm not sure this is what I want though.
I'm not sure I should have changed from Automatic.

I can explain the behavior I want using this website as an example.  As Firefox WAS setup, I had to do
a manual refresh (F5) to check for responses to my posts.  I would prefer if a refresh took place automatically when an individual like yourself is kind enough to respond to my post.

Another example.  I use the  website to track the Packer football games
whenever they're game is not on TV here in Arkansas.
With Firefox under Windows 7, my page was updated automatically as each play occurs.
Not so under my Firefox running here under Ubuntu.

Do you think I should have stayed with the Automatic setting to get the behavior I want?

Many thanks for taking the time - Randy

P.S.  For the first time I have an idea of what caching is about.  Thanks

You are welcome Randy.

The default behavior is Automatic. This will give a good balance. But since you are being forced to refresh to see a post on Ubuntu forums, then setting to "Everytime a site Opens" is the best workaround. However, this will result in longer page loading times and increased bandwidth consumption.

I am not sure why your Firefox is not refreshing when needed. Although changing that option in Better Cache will "solve" the problem, is not a definitive solution. You still need to find the culprit,

Check if the problem persists with a clean Firefox profile.

---

### Post by Randy Schilling on 2011-11-10
OK, I'll check into a clean profile.  Thanks - Randy

---


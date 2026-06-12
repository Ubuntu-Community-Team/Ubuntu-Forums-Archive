---
title: "firefox location bar wont take a URL - only searches"
date: 2012-05-05
forum: General Help
---

### Post by eanema on 2012-05-05
Hi All,
I have a serious problem. I just installed Ubuntu 12.04 - upgraded from 10.04. I am using Gnome 3 classic.

The problem I am experiencing is that when I type a URL into the location bar for example [www.ubuntu.com](www.ubuntu.com) firefox searches google for [www.ubuntu.com](www.ubuntu.com) instead of just loading the page. I should also note that as I navigate links the address bar still shows [www.ubuntu.com](www.ubuntu.com) and it does not change as it should. When a new tab is opened [www.ubuntu.com](www.ubuntu.com) remains in the location bar

I have tried to search for similar problems but I can't manage find the right search terms.

Any help or pointer would be greatly appreciated!

---

### Post by Musicmaker384 on 2012-05-05
I can't help you here, but you would probably have better luck getting help with this issue if you posted this in **Absolute Beginner Talk>Firefox +1 Mega Thread.**

---

### Post by eanema on 2012-05-06
I'm not sure if I was clear.

I am not a newb - I've been using Ubuntu for years now. This is a problem with firefox not responding the way it should, as opposed to me not knowing how to use it. 

When I type into the location bar i type 'www.' and firefox suggests websites such as [www.google.com](www.google.com), [www.yahoo.com](www.yahoo.com) etc but when I complete the address of the site I'm attempting to visit and press enter it returns a google search of the address! 

Any thoughts?

---

### Post by claracc on 2012-05-06
I have firefox 12.0 in ubuntu 10.04.

What do you have in firefox --> preferences -->preferences --> privacy, addresses bar ?, I have selected history and bookmarks, and firefox behaves in the proper way.

---

### Post by eanema on 2012-05-06
In firefox, I click the Edit -> preferences -> Privacy tab and my options are as follows:

Tracking: tell websites I do not want to be tracked **is** checked
History: 
firefox will: 'never remember history'
location bar: when using the location bar, suggest: 'history and bookmarks' (although I have tried nothing as well)

it might also be interesting to note that I can't go to about:config because firefox searches for 'about:config' in google

---

### Post by eanema on 2012-05-06
well I didn't figure out the problem but I did figure out the solution.

I just deleted the .mozilla folder in my home directory. Simple fix

---


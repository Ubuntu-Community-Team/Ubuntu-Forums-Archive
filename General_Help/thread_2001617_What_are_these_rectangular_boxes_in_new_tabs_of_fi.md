---
title: "What are these rectangular boxes in new tabs of firefox 13.0?"
date: 2012-06-11
forum: General Help
---

### Post by newhere_m on 2012-06-11
I am usnig 10.04 and recently upgraded to firefox 13.0. A new feature is that if I click on the green "+" sign at the right of last tab of firefox, a new tab opens which shows 3x3=9 rectangular empty boxes. I fail to understand what these are meant for. Also there are 3x3 small very small boxes at tor right corner where a message "hide the new tabs" appears on placing the mouse. If I click on it the big rectangular boxes vanish and the new Firefox page looks normal. Can anybody please explain what these big boxes are provided for in this version of the Firefox?

---

### Post by traditionalist on 2012-06-11
> **newhere_m said:**
> I am usnig 10.04 and recently upgraded to firefox 13.0. A new feature is that if I click on the green "+" sign at the right of last tab of firefox, a new tab opens which shows 3x3=9 rectangular empty boxes. I fail to understand what these are meant for. Also there are 3x3 small very small boxes at tor right corner where a message "hide the new tabs" appears on placing the mouse. If I click on it the big rectangular boxes vanish and the new Firefox page looks normal. Can anybody please explain what these big boxes are provided for in this version of the Firefox?

It's a speed dial feature. Contains the last nine websites you looked at. You can remove it by doing this;

Type **about:config** in the url-bar and press enter.  Enter **browser.newtabpage.url** in the search bar and set it to "about:blank". Source: [http://support.mozilla.org/en-US/kb/new-tab-page-show-hide-and-customize-top-sites#w_how-do-i-turn-the-new-tab-page-off](http://support.mozilla.org/en-US/kb/new-tab-page-show-hide-and-customize-top-sites#w_how-do-i-turn-the-new-tab-page-off)

---

### Post by brainwash on 2012-06-11
> **newhere_m said:**
> A new feature is that if I click on the green "+" sign at the right of last tab of firefox, a new tab opens which shows 3x3=9 rectangular empty boxes.
Did you disable the offline cache by setting the cache limit to 0 MB or did you even turn off the browsing history? Normally those boxes should display a cached preview of your visited websites.

---


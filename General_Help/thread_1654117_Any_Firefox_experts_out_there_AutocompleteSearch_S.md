---
title: "Any Firefox experts out there? Autocomplete/Search Suggestion Problems"
date: 2010-12-27
forum: General Help
---

### Post by Rubicon421 on 2010-12-27
*(If anyone is able to and knows a better section to post this in, please move it)*

Autocomplete/search suggestions are not working the Firefox search box for me. It works in the address bar but not in the search box to the right where you can choose the search engine. 

I have tried all the obvious settings and fixes and nothing works. I made sure the "show suggestions" options is checked when you right click the search box, unchecked and rechecked it, clicked the "manage search engines" link and enabled/disabled/re-enabled it in that menu and changed the same settings from the about:config page. I have also reinstalled Firefox (but did not do a full uninstall first), and tried disabling all extensions. 

I have a lot of extensions installed and passwords and settings I don't want to have to set up again so I would like to avoid uninstalling FF if possible. Can anyone think of something else to try?

---

### Post by Rubicon421 on 2011-01-04
Bump...

---

### Post by Krytarik on 2011-01-04
1.) Uninstalling/Re-installing doesn't affect the user profile at all.

2.) What search engine are you trying to get suggestions of?
[http://support.mozilla.com/en-US/kb/Search%20suggestions#w_the-selected-search-engine-may-not-offer-search-suggestions-service](http://support.mozilla.com/en-US/kb/Search%20suggestions#w_the-selected-search-engine-may-not-offer-search-suggestions-service)

---

### Post by Rubicon421 on 2011-01-04
Search suggestions don't work from any of the sites I have in the search bar. It's enabled but I don't get any suggestions from Google, Amazon, Wikipedia or anything else. 

I found a Firefox extension called FEBE that could backup and reinstall all my extensions easily but if that doesn't affect the user settings then what would I have to delete after uninstalling to make sure that the problem doesn't come back when I reinstall?

---

### Post by Krytarik on 2011-01-04
The custom extensions are stored in the user profile!

Did you really disabled all of your extensions to test it?

Try renaming the "extensions"-directory in "/home/USER_NAME/.mozilla/firefox/USER_PROFILE" to disable them altogether.

If that doesn't change it move your entire profile-dir to another location within your home-dir.

You can restore it by deleting the newly created profile-dir and just moving your own dir back.

---


---
title: "Google.co.uk in Firefox?"
date: 2009-12-14
forum: General Help
---

### Post by Colin@oxford on 2009-12-14
The search box in my Firefox uses google.com as the default search engine.  How can I change it to use google.co.uk?  My language setting is "English(UK)" and the timezone is "London/Europe"

---

### Post by Voynix on 2009-12-14
have you tried changing the config file? I am guessing here, but if you go to aboutconfig in firefox, and look for "flagfox.customlookup.url" and "keyword.URL" you are free to customise it to your liking.    v    > **Colin@oxford said:**
> The search box in my Firefox uses google.com as the default search engine.  How can I change it to use google.co.uk?  My language setting is &quot;English(UK)&quot; and the timezone is &quot;London/Europe&quot;

---

### Post by howefield on 2009-12-14
Go to [https://addons.mozilla.org/en-US/firefox/addon/3682](https://addons.mozilla.org/en-US/firefox/addon/3682) 

Install and restart Firefox.

Go to [http://www.google.co.uk](http://www.google.co.uk)

Right click in google search bar and click “Add to Search Bar”

Click the down arrow on the right of the search field icon, and select “Manage Search Engine”

The rest should be easy enough.

---

### Post by tobsco on 2010-01-07
Or you can go to 

/usr/lib/firefox-3.0.16/searchplugins

and edit the file google.xml. Simply replace every .com with a .co.uk and everything will work fine.
Don't forget that you need root privileges to edit this file so use ```
gksudo nautilus
``` to open the file.

---

### Post by Colin@oxford on 2010-01-08
Thank you.  That is what I was hoping would be available,
For the record, I found the file in

/usr/lib/firefox-addons/searchplugins/en-US

I wonder whay I have en-US, rather than en-UK, since I downloaded from a UK mirror and am set for everything UK.

---

### Post by UltraAnders on 2010-08-18
Having the same issue with my fairly recent 10.04 install. I found I have to change the plug-ins in the /en-GB sub-folder, rather than /en-US, which suggests my Firefox is setup for GB (as I believe). Annoyingly, though, changing the .com to .co.uk breaks the "suggests" functionality. Anyone know how to get that working again?

---

### Post by karaken12 on 2010-11-17
If you choose to edit the search plugin (/usr/lib/firefox-addons/searchplugins/google.xml), make sure you leave the url starting 'suggestqueries.google.com' alone.  Firefox already lets the server know what your locale is (in this case, en-GB), so you don't need to change it.  For the record, I changed two lines total -- one as an attribute in a 'Url' element (just before the 'Param's), and the other as the contents of a 'SearchForm' tag.  Just change these two, and it all works fine.

Tom

---

### Post by UltraAnders on 2010-11-18
Tom you legend. I simply changed "suggestqueries.google.co.uk" back to "suggestqueries.google.com" and suggestions are working again. :)

---

### Post by Mr Gates on 2011-07-04
very helpful post. thanks

---


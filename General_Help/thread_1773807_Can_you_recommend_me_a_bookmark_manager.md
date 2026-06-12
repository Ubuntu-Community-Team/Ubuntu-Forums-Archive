---
title: "Can you recommend me a bookmark manager?"
date: 2011-06-02
forum: General Help
---

### Post by PeterP24 on 2011-06-02
Hello,

During the past eight years I've used a number of computers with different operating systems and browsers. On each one I made a habit of using the bookmark utility of each browser and saving the bookmarks file. I never ensured the continuity of the bookmark file - with each new computer I started a new bookmark file. Even when I was reinstalling the operating system I didn't import the old bookmark file in the newly installed browser: I've always started a new bookmark file. As a result I have tens of bookmark files for Firefox (json format - some kind of xml?) and IE (html file format?) each one containing hundreds or thousands of saved links. I have also some files containing links in text format (created usually when I was using someone else computer).

I would like to be able to manage this bookmarks files by using some sort of "bookmark manager" software. The "bookmark manager" should be able to merge the bookmark files into a single collection/file. It should be able to identify and remove the duplicate entries (I have timely versions of the same bookmark file) and also it should be able to group the entries/links on categories (for example the bookmarked articles on codeproject.com should be grouped under the codeproject.com category). Not to mention that it should provide a search facility to quickly locate the interesting bookmarks.

I couldn't find such software in ubuntu software center. Do you know something that even comes close to what I need? 

Best regards,

pts

---

### Post by nitstorm on 2011-06-02
Open Firefox, *Bookmarks -> Get Bookmark Add-ons*

You should be able to find something suited to your needs there.

---

### Post by Zill on 2011-06-02
PeterP24:  How about Firefox add-on [CheckPlaces]("https://addons.mozilla.org/en-US/firefox/addon/checkplaces/")?

---

### Post by jamesisin on 2011-06-02
I use Opera.

It has bookmark synchronization built in and can be used on nearly any platform (I use it on Windows, Mac, and both Fedora and Ubuntu).

It can import nearly any sort of bookmarks file from other browsers too.

It also has sessions management (configurations of tabs and windows) which can be included in synchronizations.

---

### Post by keithpeter on 2011-06-02
> **PeterP24 said:**
> Do you know something that even comes close to what I need?

No, but here is a suggestion: view the various bookmark files in a Web browser and then save the html file from the browser. Then use gedit to copy and paste the lists to a common file. Then put the common file into a dropbox or ubuntuone folder for future reference on all platforms.

Me? I use pinboard.in

cheers

---

### Post by hwttdz on 2011-06-02
Firefox 4 has the ability to sync any or all of history, settings, forms, tabs, and bookmarks.   Works well for me.

---

### Post by PeterP24 on 2011-06-02
Thank you all for your suggestions. 

@nitstorm - I just checked and most of the addons are based on cloud storage with emphasis on synchronization of the bookmarks along multiple device. It is not quite what I wanted but I guess I can upload all the bookmark files on the cloud in order to have a single bookmark master file then retrieve it and start sorting the links in the firefox bookmark manager. 
@Zill - have you used this software? It appears to only check the validity of the bookmarks - I don't need this - I want to keep the invalid links also.
@jamesisin - I will give Opera a try. I hope that when one imports a bookmark file in Opera the old bookmarks are not overwritten - but it probably wouldn't make sense to be overwritten (but merged instead).

Edit:
@keithpeter - interesting idea - I might try it if Opera doesn't have the expected bookmark management. Got to see what to do with .json files though. 
@hwttdz - for some reason I was under the impression that when importing a new bookmark file in firefox, the old bookmark file entries are deleted. I just realized how unreasonable this thing was. I don't need sync across multiple devices (this is the meaning of sync?). I want to create a single bookmark master file containing the other ones for start so that I can organize it. Chances are that Firefox will be quite slow at managing a few thousand bookmarks. If Opera fails I would give Firefox a try.

pts

---

### Post by jamesisin on 2011-06-02
When importing all imported bookmarks get stacked into a folder (probably called something like Imported Bookmarks or some such) at the root of Opera's bookmarks.  The only potential for conflict that comes to mind is when a bookmark already exists (and it would have to be exactly the same URL).  Normally Opera won't allow you to bookmark the same URL twice.  I'm guessing that it would ignore that particular bookmark on import.

Of course synchronization acts in merging fashion.

---

### Post by jamesisin on 2011-06-02
Also I should mention that one of the sync locations for your Opera bookmarks is your MyOpera account.  So if you lose all of your Operas you can simply install Opera (anywhere) and sync again to your MyOpera account (which is how the sync is done) and you have all your bookmarks back.

---

### Post by WorMzy on 2011-06-02
Xmarks is an internet service which can sync between different PCs, and different browsers.

Firefox, Google Chrome (and Chromium), Safari and Internet Explorer are all supported. When you first set it up on a browser, you can choose to merge the browsers bookmarks with those currently on the server, which sounds like it'd be ideal for you.

---


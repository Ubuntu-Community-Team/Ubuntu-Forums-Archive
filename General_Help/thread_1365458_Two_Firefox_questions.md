---
title: "Two Firefox questions"
date: 2009-12-27
forum: General Help
---

### Post by oxf on 2009-12-27
Hi,

Two questions..
 
At some point I managed to get a website listed in the pulldown location bar by mistake and I just cant get rid of it! It has a star next to it indicating I've bookmarked it. But I searched through all my bookmarks and I cant find it anywhere. Is there a way to find where this particular website is "hiding"? if it is bookmarked it's by mistake and well hidden. I want to get rid of this.

Secondly, is there a way of storing bookmarks for privacy purposes on an external flash.?
I can see how to import or back up bookmarks but no way to access an external list. I'd prefer not to store them directly in FF.

Thanks

---

### Post by aysiu on 2009-12-27
In answer to your first question, try Shift-Delete when the address is highlighted.

---

### Post by redwoodguy on 2009-12-27
1.Top level FF Menu select [COLOR=Blue]BOOKMARKS---->ORGANIZE BOOKMARKS[/COLOR]
2. On the left hand pane of this window will be all the categories of bookmarks and you can delete which ever you don't want.
3. on the top level of this window, choose[COLOR=Blue] IMPORT AND BACKUP---->BACKUP[/COLOR]. This will allow you to backup all your bookmarks to either a text file or an HTML file at a location of your choosing.

---

### Post by Leppie on 2009-12-27
> **oxf said:**
> Secondly, is there a way of storing bookmarks for privacy purposes on an external flash.?
I can see how to import or back up bookmarks but no way to access an external list. I'd prefer not to store them directly in FF.

you could use google bookmarks, like that you can save them online (but you will need either the google toolbar or some button like "google bookmarks reloaded" and of course a google account). like this, your bookmarks are not necessarily limited to ff.

---

### Post by barnaclebill18 on 2009-12-27
In the Organize Bookmarks there is a search bar.

---

### Post by lovinglinux on 2009-12-27
1) Open the site you want to remove, then click the star icon in the address bar and then click "Remove Bookmark" from the drop-down menu.

2) Close Firefox, then go to your Firefox profile folder. It will be some folder under ~/.mozilla/firefox. Then move the file **places.sqlite** to your flash drive. Then right-click the file **places.sqlite** stored in the flash drive and select the option "Make a link". A file named "Link to places.sqlite" or something like that will be created. Move that file back to your FF profile folder and rename it to **places.sqlite**. Just make sure the flash drive is mounted whenever you start Firefox.

---


---
title: "firefox bug!"
date: 2009-07-24
forum: General Help
---

### Post by sympaval on 2009-07-24
Hi all 

I made an update yesterday including firefox, and after the the update I
restart firefox as asked. When restarted, it worked up til this this morning,
since where:
- I don't see my bookmarks, all them have desperate, 
- All the icons ("next","previous","refresh", etc...... ) are deactivated; when
a web page is opened, it's really opened but I don't see the address in the
address bar,
- I can not access to my web server locally, since I'm not connected to
internet or have activated "Travailler hors connexion" at the file menu, while
I can access to it with another browser like Konqueror.
- My browser seems still searching the web site, since the page is already 
opened.
- The addresses I access to are not kept in the address bar.
- I also noticed that I can not mark another page.
When I press Ctrl+D or go to the bookmark menu to do it, I have no answer from
the browser.

This is few details I can give to you, hopefully you could help me
troubleshooting and fix this bug on my sytem.

I didn't get to reinstall firefox cause I thought it could lead to the lost of
my pages bookmarked, which are very important for me.

Thank a lot for excusing my english language , and helping me

I'm waiting eventually for your propositions inside my mailbox.

"About my firefox: Mozilla/5.0 (X11; U; Linux i686; fr; rv:1.9.0.12)
Gecko/2009070818 Ubuntu/8.10 (intrepid) Firefox/3.0.12
Build Identifier: Mozilla/5.0 (X11; U; Linux i686; fr; rv:1.9.0.12)
Gecko/2009070818 Ubuntu/8.10 (intrepid) Firefox/3.0.12"


Best regards!

Eugene.

---

### Post by ajgreeny on 2009-07-24
Don't worry about your bookmarks.  They are stored in the hidden folder in your home called ~/.mozilla where all the profile configuration for firefox is kept, along with the 5 latest backups of the bookmarks file in ~/.mozilla/firefox/qn4bdmr0.default/bookmarkbackups as dated .json files.

Even if your profile is totally messed up which may be your situation, you can simply rename the ~/,mozilla folder as ~/.mozillabak, restart firefox, go to *Bookmarks >Organise bookmarks* and there, restore one of those backup json files.

Give it a try now, it may solve your problem.

---

### Post by lovinglinux on 2009-07-25
See **Solution** [*[COLOR="Red"]**FOT003**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT003).

---

### Post by sympaval on 2009-07-25
Hi 
Thank a lot Friends

I got to fix my problem just by deleting the places.sqlite file and restore my bookmarks as recomended.


It woks now as previous, I have the Firefox i was used to.


Thank and keep help together.

Eugene.


See you sooner .

---

### Post by lovinglinux on 2009-07-25
> **sympaval said:**
> Hi 
Thank a lot Friends

I got to fix my problem just by deleting the places.sqlite file and restore my bookmarks as recomended.


It woks now as previous, I have the Firefox i was used to.


Thank and keep help together.

Eugene.


See you sooner .

You are welcome.

---

### Post by sympaval on 2009-07-27
Hi!


Just wanna ask how to put a thread in solved status.

Cause I've solved my problem with your help, and I'm not able to notify it so that other person could see it solved and use the solution next time.


thanks again.


Eugene.

---

### Post by undeadboe on 2009-07-27
the newer versions of fire contain many bugs. my suggestion would be to downgrade until these bugs are worked out.

---

### Post by sympaval on 2009-07-28
thank my dear, but however I want to know how to mark a thread as resolved.


Thank for your collaboration.

Best regards 

Eugene.

---


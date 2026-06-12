---
title: "[SOLVED] Firefox 3.5 devastation (trash doesnt work, no history, no bookmarks)"
date: 2009-07-07
forum: General Help
---

### Post by HD Chang on 2009-07-07
Well, I did the simple task of opening Firefox 3.5 from terminal as root for some reason and it WRECKED my system.

My trash can wont open now, my browser wont save any history & I have no bookmarks and when I try to import them it does NOTHING.

Any ideas?


Tried this crap by firefox & it didnt work:
> Places database file

You can also fix this by forcing Firefox to rebuild the Places database, as follows:

   1. (Optional) Export your bookmarks to an HTML file named bookmarks.html (see Exporting bookmarks to an HTML file for detailed instructions) and place the bookmarks.html file in the Firefox profile folder. If a bookmarks.html file already exists, allow the exported file to replace it.
   2. From the menu at the top of the Firefox windowbar, select FileFirefox and then select the ExitQuit FirefoxQuit menu item.
   3. Open the Firefox profile folder and delete (or rename) the places.sqlite file and, if it exists, places.sqlite-journal.
   4. (Optional) If you want Firefox to automatically import your bookmarks from an existing bookmarks.html file in the profile folder, instead of from a JSON backup, open the bookmarkbackups folder and remove all bookmarks-(date).json files to another location.
   5. It is probably a good idea to also delete (or rename) the localstore.rdf to remove the references to the old Places file but you will need to add back any toolbar customizations. 

Firefox will create a new places.sqlite file and automatically import the most recent bookmark backup file. If no JSON backup is found, Firefox will automatically import your bookmarks from the profile folder bookmarks.html file, if it exists. 

---

### Post by aysiu on 2009-07-07
When you say you opened Firefox as root, did you, by chance, use the command *sudo firefox*?

If so, that would explain most of your problems.

Close Firefox. Close all applications. Open a [terminal](http://www.psychocats.net/ubuntu/terminal) and enter the command ```
sudo chown -R *username:username* /home/*username*
``` where *username* is your actual username.

Then, read this:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by maheshasolkar on 2009-07-07
When you opened Firefox as root, you may have caused some files in the mozilla profile folders to be owned by root, instead of you. You should be able to find that out with something like this (in the terminal):
```

  % find ~/.mozilla -user root
```

If files like *.sqlite show up, they belong to root now, so you will not be able to write to them (use bookmarks/history etc.). In that case, you might want to try something like:
```

  % find ~/.mozilla -user root | xargs sudo chown yourname:yourname
```

where 'yourname' is your username.

I've not tried any of above, so be careful.

---

### Post by HD Chang on 2009-07-07
You guys fixed it! thanks!

I thought it was a permissions deal but didn't know which files were messed up.

PS: how can i avoid that in the future?
gksudo?  No sudo at all?

I dont get it.

---

### Post by Eeqmcsq on 2009-07-07
> PS: how can i avoid that in the future?
gksudo? No sudo at all? How did you originally launch firefox as root?

I avoid launching GUI apps from the command line, except for "sudo gedit <file name>" when I need to edit a configuration file. When I'm done, I immediately exit gedit. If I open a bash shell as root, I get what I need done AS QUICKLY AS POSSIBLE and then immediately exit bash.

---

### Post by aysiu on 2009-07-07
*gksudo* should always be used with graphical applications.

**gksudo firefox**
**gksudo gedit**
**gksudo unetbootin**

*sudo* should be used with only terminal applications.

**sudo nano**
**sudo -i**
**sudo /etc/init.d/gdm restart**

---


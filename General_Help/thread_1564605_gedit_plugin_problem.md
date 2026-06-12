---
title: "gedit plugin problem"
date: 2010-08-30
forum: General Help
---

### Post by ishokenmei on 2010-08-30
Hi, everyone.  I installed the Autocomplete plugin [http://github.com/nagaozen/gedit-plugin-autocomplete/](http://github.com/nagaozen/gedit-plugin-autocomplete/) for gedit and it works great.  But when I ran it as root &quot;sudo gedit ...&quot;, Autocomplete is not on the list of plugin and the auto complete function is not working.  Is it possible to make the plugin available to all users?  Thanks in advance.

---

### Post by Vaphell on 2010-08-30
try /usr/share/gedit-2/plugins
default ones are stored there

---

### Post by ishokenmei on 2010-08-31
Thank you for your reply, Vaphell.  I copied the folder Autocomplete and the file autocomplete.gedit-plugin to /usr/share/gedit-2/plugins and restarted the machine.  But Autocomplete is still not on the list of plugins in gedit.  Any idea?

---

### Post by inameiname on 2010-08-31
So you cut and pasted all of the files that you had previously put in /.gnome2/gedit/plugins into /usr/share/gedit-2/plugins, removing the old ones, and it's still not working for you? Did you remember to enable it in root Gedit, just as you did in Gedit? Basically you have to do all that you did in the normal Gedit, add external tools and whatnot, and then enable all the plugins that you desire, in root Gedit.

Oh, and don't forget to remove the one in /.gnome2/gedit/plugins as it's not required anymore. All that is in /usr/share/gedit-2/plugins will work with both Gedit and root Gedit.

---

### Post by ishokenmei on 2010-08-31
I finally figure it out.  First I deleted the files in /.gnome2/gedit/plugins as inameiname suggested.  Then I copied the folder Autocomplete to /usr/share/gedit-2/plugins. Lastly I copied the folder Autocomplete and the file autocomplete.gedit-plugin to /usr/lib/gedit-2/plugins.  Now it works when I run it as root or other user.  Thank all for the help!

---

### Post by inameiname on 2010-08-31
Oops, my reply was supposed to be /usr/lib/gedit-2/plugins, not /usr/share.... I just copied and pasted the first dude's reply's location, thinking it was the right one. Anyway, /usr/share input of anything isn't necessary, just what you did with putting the stuff in /usr/lib/gedit-2/plugins. So for any new plugins you ever wish to add to Gedit someday, you only need to place them inside /usr/lib/gedit-2/plugins and that's all.

Regardless, good you got it figured out.

---


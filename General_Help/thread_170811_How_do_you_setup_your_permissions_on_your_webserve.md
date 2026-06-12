---
title: "How do you setup your permissions on your webserver?"
date: 2006-05-05
forum: General Help
---

### Post by rayde on 2006-05-05
I'm curious as to how others are setting up permissions in a webserver environment, as far as access to /var/www/ and other sub directories goes.  If you know of a useful guide online to this, I'd appreciate a link.

Essentially, I am looking for the best way that multiple people can go in and edit/upload web files, without coming into permission issues based on who is actually logged in at the time of an edit/upload.

Is it bad practice to keep web files 775?  in this situation, when a user uploads a file would they then always have to manually change the group assignments so other users can make changes?  that doesn't seem practical.

Is it bad practice to use a common "webuser" account of some sort that has a shared password?

thanks for the help!

---

### Post by kaptainlange on 2006-05-05
I'm not expert, but in the two years I've run a webserver I've picked up some things.

What I am doing so far is this.  I've created the group www-users.  Then added all the users who should have access to that group.  Then add the user that apache uses, www-data on my system, to that group.

To make things easier, umask is set to 002 to allow group read/write.  Just make sure the directories you want to keep private don't share group names with others.  For example, everything under userx's home directory is strictly userx:userx unless manually specified otherwise.

Next chown the data directory of your web server to 2775.  This should ensure files created under that directory retain the group of the directory.

That should take care of your individual directories.  Now, as you mentioned uploading. If you are using user directories like public_html, there is an apache module you can use that will run that apache thread as the owner of the folder.  I forget the name, so you'll have to look that one up.  So basically, you can give people private directories via the apache user directory module, that won't be group writeable.  Anything created in your /var/www directory will still be group writeable however, and if someone uploaded something there, another www-user could easily remove it.  So my advice is to give people user directories for private data, and trust those in your www-user group to not do anything stupid.

---

### Post by rayde on 2006-05-05
thanks for the info :)

---


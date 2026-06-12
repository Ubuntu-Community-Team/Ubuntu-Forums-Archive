---
title: "Ardour installation problem"
date: 2005-02-05
forum: General Help
---

### Post by bobmitch on 2005-02-05
Have downloaded Ardour and am attempting to ./configure - but get the following error:

*** The gtk-config script installed by GTK could not be found
*** If GTK was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GTK_CONFIG environment variable to the
*** full path to gtk-config.
configure: error: *** gtk-ardour requires GTK+, but it doesn't appear to be installed
configure: error: /bin/sh './configure' failed for gtk_ardour

Now, I can`t find a single gtk-config file on the disk - nor can I see any gtk+ headers or dev packages available. 

Am I missing something obvious?  (I`m a linux noob, but learning fast. :)  )

---

### Post by Ste on 2005-02-06
[QUOTE=bobmitch]Have downloaded Ardour and am attempting to ./configure - but get the following error:

*** The gtk-config script installed by GTK could not be found
*** If GTK was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GTK_CONFIG environment variable to the
*** full path to gtk-config.
configure: error: *** gtk-ardour requires GTK+, but it doesn't appear to be installed
configure: error: /bin/sh './configure' failed for gtk_ardour

Now, I can`t find a single gtk-config file on the disk - nor can I see any gtk+ headers or dev packages available. 

Am I missing something obvious?  (I`m a linux noob, but learning fast. :)  )[/QUOTE]
 Look for libgtk -dev.
I think that's what is needed, could be wrong tho.

---

### Post by bobmitch on 2005-02-06
[QUOTE=Ste]Look for libgtk -dev.
I think that's what is needed, could be wrong tho.[/QUOTE]

Twas indeed.  Got some good help on the ardour irc channel.

Now all I have to do is get Jack working with ALSA and in turn with my onboard sound, then my terratec pro audio card.

:D

---


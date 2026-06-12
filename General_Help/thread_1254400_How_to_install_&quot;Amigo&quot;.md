---
title: "How to install &quot;Amigo&quot;?"
date: 2009-08-31
forum: General Help
---

### Post by Kdar on 2009-08-31
```
amigo.db
amigo.glade
amigo.gladep
amigo.rb
constants.rb
database.sql
dictionary_window.rb
es.png
glade_window.rb
helpers.rb
history.rb
language_english.rb
language.rb
language_spanish.rb
preferences_window.rb
status_icon_menu.rb
textview_tags.rb
```

I am trying to install amigo.
[http://gnomecoder.wordpress.com/amigo/](http://gnomecoder.wordpress.com/amigo/)

But the tar file doesn't come with configure file. What can I do to install it?

---

### Post by Kdar on 2009-08-31
anyone? please.. I am kind of lost with this one.

---

### Post by Uzi304 on 2009-08-31
Not entirely sure but try this. 
```
sudo apt-get install ruby libgtk2-ruby libgconf2-ruby libglade2-ruby libsqlite3-ruby libnotify-bin
```
Those are the dependencies needed by Amigo. Then go into the Amigo directory and run
```
./amigo.rb
```

Worth a try, I think.

---

### Post by Kdar on 2009-08-31
oh so its already pre-build package. I didn't know.

But how can I add it into program directory and add link to menu?

---

### Post by Uzi304 on 2009-09-01
```
alacarte
```
With that, you'll be able to add it into the menu. I'm not sure what you mean by program directory. If you mean being able to execute the command in a terminal regardless of what directory you're in, copy or move the script to /usr/bin

---


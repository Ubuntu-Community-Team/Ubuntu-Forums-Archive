---
title: "running eclipse on ubuntu"
date: 2009-11-01
forum: General Help
---

### Post by dyyyy on 2009-11-01
hi i downloaded eclipse ganymede from the website,
the file is eclipse-jee-ganymede-SR2-linux-gtk.tar.gz
i extracted it in /opt
i followed these instructions
> [http://flurdy.com/docs/eclipse/install.html](http://flurdy.com/docs/eclipse/install.html)

Extract the eclipse download and move to opt. 
tar xzf wtp-all-in-one-sdk-1.0-linux-gtk.tar.gz
sudo mv eclipse /opt/eclipse cd /opt sudo chown -R root:root eclipse
sudo chmod -R +r eclipse
sudo chmod +x `sudo find eclipse -type d`

Then create an eclipse executable in your path 
sudo touch /usr/bin/eclipse
sudo chmod 755 /usr/bin/eclipse
sudoedit /usr/bin/eclipse 

With this contents
#!/bin/sh
#export MOZILLA_FIVE_HOME="/usr/lib/mozilla/"
export ECLIPSE_HOME="/opt/eclipse"

$ECLIPSE_HOME/eclipse $* 

Then create a gnome menu item
sudoedit /usr/share/applications/eclipse.desktop

With this contents
[Desktop Entry]
Encoding=UTF-8
Name=Eclipse
Comment=Eclipse IDE
Exec=eclipse
Icon=/opt/eclipse/icon.xpm
Terminal=false
Type=Application
Categories=GNOME;Application;Development;
StartupNotify=true 
Configure

You now have a working eclipse. But run this command first to initialise the set up. 
/opt/eclipse/eclipse -clean

Then from here on you can run from the menu item applications/programming/eclipse

but now when i run eclipse it shows me the loading image, and when eclipse finishes loading, i have a small window containing nothing with the title eclipse that i can't close. by looking in the system monitor i have 2 processes called eclipse 'sleeping'

thank you for any help (sorry for the long text :P)

---

### Post by dawnloader on 2009-11-02
It turns out to be a known problem - check this url:
[Eclipse gets past the splash screen but then an empty window appears]("http://wiki.eclipse.org/IRC_FAQ#Eclipse_gets_past_the_splash_screen_but_then_an_empty_window_appears_.2F_Eclipse_is_crashing_on_me_whenever_I_initiate_a_browser_component_such_as_hovering_over_Java_methods_for_javadoc_tooltips...")

Solution does not look quite straight forward though - main point I think is that ganymede-SR2 just does not work properly under ubuntu 9.10

---

### Post by dyyyy on 2009-11-03
thank you,
i'll check the site

---

### Post by dyyyy on 2009-11-04
it's me again :)
what's the simplest way to run eclipse on ubuntu now?
should i download an older version?
or can someone plz expalin me in a simple way a workaround for the bug :oops:

---

### Post by waxxxd on 2009-11-04
Hi dyyyy

I had the same problem some days ago. I was trying to run the incorrect architecture version of eclipse. I had downloaded 6b bit on 32 bit Karmic. Try running eclipse from terminal and it might give you better error messages.

---

### Post by dyyyy on 2009-11-04
i'm not getting any error from the terminal,
as if eclipse is already running, in fact i have a small window with the title "eclipse", but i just can't close it and it doesn't appear in my windows list (like an empty dialog box)
i checked the link that dawnloader has put, i have this error (i checked my log), but i don't have firefox installed, i use opera
should i download firefox? and what version?
thank you
(sorry for being lazy in my last posts)

---

### Post by dyyyy on 2009-11-07
any help plllllz 
i still can't launch eclipse, any advice would be really helpful
thank you

---


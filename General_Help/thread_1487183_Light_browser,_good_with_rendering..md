---
title: "Light browser, good with rendering."
date: 2010-05-18
forum: General Help
---

### Post by dragos240 on 2010-05-18
When I mean light, I mean less than 10mb or ram usage. Dillo is VERY light, it uses less than 1mb of ram, however, it's rendering capabilities are very limited. Any suggestions?

---

### Post by kerry_s on 2010-05-18
less then 10mb, there won't be nothing decent. i use chromium, on average at least 30+mb.

---

### Post by JohnnyC35 on 2010-05-18
Swiftfox is lighter than Firefox, if that helps. Tried Chrome, Dillo, and a few others but Fire/Swift-fox give me airmiles and I figure any sluggishness will be offset for that

---

### Post by chris200x9 on 2010-05-18
uzbl? never used it, just heard about it.

---

### Post by dragos240 on 2010-05-18
> **chris200x9 said:**
> uzbl? never used it, just heard about it.

I have, It's difficult to navigate with.

---

### Post by Frogs Hair on 2010-05-18
Check Source Forge , I got 202 results for web browsers.

---

### Post by Old Marcus on 2010-05-18
Or just stop obsessing over RAM usage? Unless it significantly slows down your computer, you're being a tad perfectionist and unrealistic tbh.

---

### Post by dragos240 on 2010-05-18
> **Old Marcus said:**
> Or just stop obsessing over RAM usage? Unless it significantly slows down your computer, you're being a tad perfectionist and unrealistic tbh.

I have 1gb of ram on my netbook. I run gnome. And with firefox, browsing is very laggy. It does affect my browsing significantly.

---

### Post by kerry_s on 2010-05-18
> **dragos240 said:**
> I have 1gb of ram on my netbook. I run gnome. And with firefox, browsing is very laggy. It does affect my browsing significantly.

there you go, your using gnome & firefox. try a lighter desktop/window manager on the back end & chromium-browser(it's in the repo)

i'm using an atom 230 1.6ghz 1gb ram nettop.
running openbox + xfce4-panel + xfdesktop 

i've never ever used more the 400mb yet.

---

### Post by juancarlospaco on 2010-05-18
Here:

```

#!/usr/bin/env python
import sys
import gtk
import webkit
DEFAULT_URL = 'http://www.google.com' # Change this as you Wish
class SimpleBrowser: # needs GTK, Python, Webkit-GTK
    def __init__(self):
        self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)
        self.window.set_position(gtk.WIN_POS_CENTER_ALWAYS)
        self.window.connect('delete_event', self.close_application)
        self.window.set_default_size(350, 20)
        vbox = gtk.VBox(spacing=5)
        vbox.set_border_width(5)
        self.txt_url = gtk.Entry()
        self.txt_url.connect('activate', self._txt_url_activate)
        self.scrolled_window = gtk.ScrolledWindow()
        self.webview = webkit.WebView()
        self.scrolled_window.add(self.webview)
        vbox.pack_start(self.scrolled_window, fill=True, expand=True)
        self.window.add(vbox)
    def _txt_url_activate(self, entry):
        self._load(entry.get_text())
    def _load(self, url):
        self.webview.open(url)
    def open(self, url):
        self.txt_url.set_text(url)
        self.window.set_title('%s' % url)
        self._load(url)
    def show(self):
        self.window.show_all()
    def close_application(self, widget, event, data=None):
        gtk.main_quit()
if __name__ == '__main__':
    if len(sys.argv) > 1:
        url = sys.argv[1]
    else:
        url = DEFAULT_URL
    gtk.gdk.threads_init()
    browser = SimpleBrowser()
    browser.open(url)
    browser.show()
    gtk.main()

```

This browser qualify **100/100 on Acid3 Test**, 
it uses less than 10Mb, **Use URL as PARAMETER**.
:)

---

### Post by WinterRain on 2010-05-18
> **dragos240 said:**
> I have 1gb of ram on my netbook. I run gnome. And with firefox, browsing is very laggy. It does affect my browsing significantly.

If you're not using all of your ram, then gnome+FF is not the issue. Even if you were using 700+ ram, (which I doubt) why would it slow down? It either runs good or it doesn't. The issue is elsewhere. I have seen lesser pc's that do just fine with gnome and firefox.

---

### Post by dragos240 on 2010-05-18
> **juancarlospaco said:**
> Here:

```

#!/usr/bin/env python
import sys
import gtk
import webkit
DEFAULT_URL = 'http://www.google.com' # Change this as you Wish
class SimpleBrowser: # needs GTK, Python, Webkit-GTK
    def __init__(self):
        self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)
        self.window.set_position(gtk.WIN_POS_CENTER_ALWAYS)
        self.window.connect('delete_event', self.close_application)
        self.window.set_default_size(350, 20)
        vbox = gtk.VBox(spacing=5)
        vbox.set_border_width(5)
        self.txt_url = gtk.Entry()
        self.txt_url.connect('activate', self._txt_url_activate)
        self.scrolled_window = gtk.ScrolledWindow()
        self.webview = webkit.WebView()
        self.scrolled_window.add(self.webview)
        vbox.pack_start(self.scrolled_window, fill=True, expand=True)
        self.window.add(vbox)
    def _txt_url_activate(self, entry):
        self._load(entry.get_text())
    def _load(self, url):
        self.webview.open(url)
    def open(self, url):
        self.txt_url.set_text(url)
        self.window.set_title('%s' % url)
        self._load(url)
    def show(self):
        self.window.show_all()
    def close_application(self, widget, event, data=None):
        gtk.main_quit()
if __name__ == '__main__':
    if len(sys.argv) > 1:
        url = sys.argv[1]
    else:
        url = DEFAULT_URL
    gtk.gdk.threads_init()
    browser = SimpleBrowser()
    browser.open(url)
    browser.show()
    gtk.main()

```This browser qualify **100/100 on Acid3 Test**, 
it uses less than 10Mb, **Use URL as PARAMETER**.
:)

The world's simplest web browser? Good job :).

---

### Post by juancarlospaco on 2010-05-18
> **dragos240 said:**
> The world's simplest web browser? Good job :).

It born a day wanting something Prism-like but lightweight and more customizable,
its not perfect, but works, maybe i add psyco later.

---

### Post by Shining Arcanine on 2010-05-18
> **dragos240 said:**
> I have 1gb of ram on my netbook. I run gnome. And with firefox, browsing is very laggy. It does affect my browsing significantly.

I have two suggestions. One is that you try Chromium, it should be better than Firefox on your system. The other is that you consider Gentoo Linux. Someone else recently posted at the Gentoo forums that he switched from Ubuntu Linux to Gentoo Linux and saw his memory usage drop to 70MB of RAM at boot:

[http://forums.gentoo.org/viewtopic-t-828094.html](http://forums.gentoo.org/viewtopic-t-828094.html)

He later posted in another thread that his memory usage is 200MB with his typical applications open (firefox being one of them I assume):

[http://forums.gentoo.org/viewtopic-p-6284135-highlight-.html#6284135](http://forums.gentoo.org/viewtopic-p-6284135-highlight-.html#6284135)

He said that it used to be about double of that with Ubuntu and also that his system only has 512MB of RAM, so with 1GB of RAM, you should be golden.

The main drawback to using Gentoo Linux is that installing it will take days on your netbook, because it requires that all software be compiled from source, but in my opinion it is worth it.

Anyway, you could switch to Chromium, Gentoo Linux or both. Any of those choices should help alleviate your issues, although I suspect that your lag issues are more of a result of your netbook's processor than they are of your browser's memory usage, in which case, switching to Chromium would make the biggest difference.

---

### Post by dragos240 on 2010-05-19
> **Shining Arcanine said:**
> I have two suggestions. One is that you try Chromium, it should be better than Firefox on your system. The other is that you consider Gentoo Linux. Someone else recently posted at the Gentoo forums that he switched from Ubuntu Linux to Gentoo Linux and saw his memory usage drop to 70MB of RAM at boot:

[http://forums.gentoo.org/viewtopic-t-828094.html](http://forums.gentoo.org/viewtopic-t-828094.html)

He later posted in another thread that his memory usage is 200MB with his typical applications open (firefox being one of them I assume):

[http://forums.gentoo.org/viewtopic-p-6284135-highlight-.html#6284135](http://forums.gentoo.org/viewtopic-p-6284135-highlight-.html#6284135)

He said that it used to be about double of that with Ubuntu and also that his system only has 512MB of RAM, so with 1GB of RAM, you should be golden.

The main drawback to using Gentoo Linux is that installing it will take days on your netbook, because it requires that all software be compiled from source, but in my opinion it is worth it.

Anyway, you could switch to Chromium, Gentoo Linux or both. Any of those choices should help alleviate your issues, although I suspect that your lag issues are more of a result of your netbook's processor than they are of your browser's memory usage, in which case, switching to Chromium would make the biggest difference.


Gentoo was my main distro for a while. It served me fine, but much of the time I disliked the fact that I had to compile everything, plus there were a few wine glitches.

---

### Post by szymon_g on 2010-05-19
hm... in QT 4.7 beta tar.gz package (i don't know how about stable release) you have a small, quite nice 'example' of browser. it uses only few mb's (as far i remember) or ram. its simply called 'browser', its in /demos directory.

---

### Post by philinux on 2010-05-19
Moved to general help forum.

---

### Post by warfacegod on 2010-05-19
You could try Midori for a browser.

Before you go crazy with different environments and browsers, it might be a good idea to see if you can get Firefox running smoothly first.

This is an excellent guide: [http://ubuntuforums.org/showthread.php?t=1193567]("http://ubuntuforums.org/showthread.php?t=1193567")

---

### Post by dragos240 on 2010-05-19
Midori with google:
[http://www.glowfoto.com/viewimage.php?img=19-050828L&rand=4439&t=png&m=05&y=2010&srv=img5]("http://www.glowfoto.com/viewimage.php?img=19-050828L&rand=4439&t=png&m=05&y=2010&srv=img5")

---

### Post by warfacegod on 2010-05-19
Then get rid of that goofy icon thing. it looks rather worthless to me.

---

### Post by dragos240 on 2010-05-19
> **warfacegod said:**
> Then get rid of that goofy icon thing. it looks rather worthless to me.

Goofy icon thing? Be more specific. Do you mean the large google thing in the corner of the page, that's midori, incorrectly rendering google.

---

### Post by warfacegod on 2010-05-19
You're right I just installed Midori and it did the same thing. Now to uninstall...

---

### Post by dragos240 on 2010-05-19
What webkit version is midori based on? The example browser renders google fine.

---

### Post by warfacegod on 2010-05-19
From the Midori site:

Requirements: GTK+ 2.10, ***WebkitGTK+ 1.1.1***, libXML2 libsoup 2.25.2

Optional: Unique 0.9, libidn, sqlite 3.0, docutils, libnotify

---

### Post by Serpher on 2010-05-19
1GB of RAM should be more than enough just for web browsing. Firefox has memory leak issues however so just try out Chrome, otherwise something is terribly wrong or it's the web content that's taking up your RAM. The browser isn't going to compact what's already on the website. If that's the case try using xcfe or LXDE for a desktop environment. Also actually check if it is your RAM being eaten up. As long as you don't run out of RAM, you won't loose any performance from it.

EDIT: Just checked it out myself. Chrome uses almost no RAM, it's just the content on your page probably or something else is wrong.

---

### Post by alex_anthony on 2010-05-23
epiphany? or even the webkit gtk sample browser, GtkLauncher (not sure if it is built with the ubuntu webkit package. But its definitely not in $PATH by default - normally in /usr/libexec or something)

---

### Post by inso_741 on 2010-05-23
you might wanna take a look at links2......:P

---

### Post by Marcelo Fernández on 2010-05-28
> **juancarlospaco said:**
> Here:

```

#!/usr/bin/env python
import sys
import gtk
import webkit
DEFAULT_URL = 'http://www.google.com' # Change this as you Wish
class SimpleBrowser: # needs GTK, Python, Webkit-GTK
[...]


```

This browser qualify **100/100 on Acid3 Test**, 
it uses less than 10Mb, **Use URL as PARAMETER**.
:)

Right, but in this case, less code you write doesn't mean you browse the web faster and lighter. :)

BTW, it seems you didn't credit the author of this snippet, take a look here: 

[http://blog.marcelofernandez.info/2009/11/navegador-simple-con-pywebkitgtk/](http://blog.marcelofernandez.info/2009/11/navegador-simple-con-pywebkitgtk/)

Regards :-)

---


---
title: "Vuze Crashes During Search"
date: 2011-05-31
forum: General Help
---

### Post by bjforesthowell on 2011-05-31
I'm running 64 bit Ubuntu. When I first log in and open up Vuze using the icon in my GUI it starts and runs just fine. The second I start to run a search Vuze crashes. The Icon will show up in my Unity Panel and I'm able to maximize, and minimize thanks to this thread...

[http://ubuntuforums.org/showthread.php?t=1745514](http://ubuntuforums.org/showthread.php?t=1745514)

As soon as I start the APP i get this error in the lower right hand corner...

"Vuze did not shutdown tidily"

It gives me a link to the Vuze log files, and all I get is out of it is this...

[5/31/11 8:24 PM] Log File Opened for Vuze 4.3.0.6

[20:24:53] [stderr] ERROR: Trying to attach top of widget 'SWTSkinObjectBasic {Search/main.area.searchresultstab/v=searchresults-area, container; parent=Contents.Search.9}' to non-existant widget 'main.area.maintabs'.  Attachment Parameters: main.area.maintabs,10

I'm assuming that this is from Vuze not being able to add an icon to the Unity bar.

When I try to open Vuze from the CLI this is what it pumps out.

root@Tiny-Tim:/home/bhowell# vuze
file:/usr/lib/jni/ ; file:/usr/lib/java/ ; file:/usr/share/java/Azureus2.jar ; file:/usr/share/java/log4j-1.2-1.2.15.jar ; file:/usr/share/java/commons-cli-1.2.jar ; file:/usr/lib/java/swt-gtk-3.6.2.jar ; file:/home/bhowell/
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
UIFunctions/ImageLoad took 0ms
new shell took 76ms
new shell setup took 25ms
skinlisteners init took 0ms
skin init took 75ms
MainMenu init took 75ms
createWindow init took 0ms
skin layout took 0ms
pre skin widgets init took 0ms
hooks init took 0ms
WARNING: already added UIUpdatable com.aelitis.azureus.ui.swt.views.skin.sidebar.SideBar@26d58939
skin widgets (1/2) init took 126ms
skin widgets init took 75ms
pre SWTInstance init took 0ms
Init Core Columns took 50ms
SWTInstance init took 0ms
shell.layout took 51ms
---------SHOWN AT 1306843948080;643ms
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.

** (Vuze:2897): WARNING **: Unable to create Ubuntu Menu Proxy: The connection is closed

I've read on another thread that I've posted on that it may be because of the 

(Vuze:2897): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
root@Tiny-Tim:/home/bhowell# 

I've read on another thread that I posed on that it may be because of the xlrunner_1.9.2 package for Firefox 4. I added the package with the same results.

[http://forum.vuze.com/thread.jspa?messageID=241113](http://forum.vuze.com/thread.jspa?messageID=241113)

I'm at my wit's end here. Could someone please help me see what I'm missing?

---

### Post by bjforesthowell on 2011-06-07
Not too much in the way of replies on this one, but I did manage to get an answer on the Vuze forum and it worked like a champ!

[http://forum.vuze.com/thread.jspa?messageID=241113](http://forum.vuze.com/thread.jspa?messageID=241113)

---

### Post by forumcash on 2012-02-14
I installed and removed mozilla-plugin-vlc, but it is still crashing when I try to search. If I can pass search, It crashes when I click to the download.

---

### Post by anocide on 2012-02-15
Hello,

There are a number of people with this issue in various threads - I have been tearing my hair out for a few hours now. They all mention variants of problems with:

xulrunner, swt.jar, mozilla-plugin-vlc

None of this resolved anything for me. The solution, in hindsight, for me is ridiculously simple. In Vuze goto -

tools => options => interface => display 

Check "Force Vuze to use Mozilla for browser widgets", you shouldn't need to specify a path. Restart Vuze. Problem solved - for me anyway. Lucid and Vuze 4.3.0.6 as fetched by package manager.

---

### Post by forumcash on 2012-02-16
> **anocide said:**
> Hello,

tools => options => interface => display 

Check "Force Vuze to use Mozilla for browser widgets", you shouldn't need to specify a path. Restart Vuze. Problem solved - for me anyway. Lucid and Vuze 4.3.0.6 as fetched by package manager.

you should change mod to _Advanced_.:P However, it didn't worked for me. I run 4.7.. It doesn't work too. :(:(
        Some other says Java can be problem which is updated and I am using Kubuntu.

    :confused::confused::confused: Basically, it doesn't let me to doing anything online ,search, download etc. Do you have any other idea or torrent software which should let me to search and order depend on which torrent file is faster.:confused::confused:

---


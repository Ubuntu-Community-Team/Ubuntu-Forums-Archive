---
title: "How to install Hughesnet FAP Status on Linux Ubuntu"
date: 2011-05-02
forum: General Help
---

### Post by ricaltman on 2011-05-02
I'm running Ubuntu 11.04 and have found a way to get a FAP monitor working. I had to install KDE to do it. The FAP monitor is "FAP Status" by Dustin Widmann written as a "Plasmoid," which will only run in a KDE desktop environment.

What I did:
1. Installed Ubuntu 11.04.
2. Installed "KDE-standard" from Synaptic Package Manager.
3. Installed 3 additional packages from Synaptic Package Manager.
    a. python-kde4 (4:4.6.2b-0ubuntu1.1)

    b. python-kde4-dev (4:4.6.2b-0ubuntu1.1)

    c. plasma-scriptengine-python (4:4.6.2a-0ubuntu5)

4. From the KDE desktop, clicked icon in the upper right corner "Panel Tool Box, then "Add Widgets" then "Get New Widgets" then "Download New Plasma Widgets" then type "Hughesnet" in the search bar. "FAP Status" by Dustin Widmann should appear, click on install. It will then show up in the "Add Widgets" toolbar in your "Panel Tool Box." Just doubleclick it and it should appear in your panel at the bottom (or top) of your desktop.

---

### Post by kuja on 2012-07-11
Old though this thread may be, I feel like passing on the news. fap-status is now replaced by [hn-status](http://qt-apps.org/content/show.php?content=152301). In additon to being cross-platform it's more reliable as well.

---


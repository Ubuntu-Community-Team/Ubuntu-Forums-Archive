---
title: "Upgrade failed, now folders open with ... Banshee?"
date: 2010-08-24
forum: General Help
---

### Post by DaveChild on 2010-08-24
I ran "aptitude update" on my machine, which hung part-way through and went unresponsive. I left it, not wanting to stop it mid-way through, and hoping it was just having a senior moment. 

Next morning it was unchanged, so I restarted. Couldn't boot into X. It turned out there was some text content in the middle of the X binary. Weird, but I put it down to the failed upgrade.

A couple of weeks on, and I have fixed the damage - a few files had weird bits of other files in them, but almost everything is running smoothly again. With one exception - opening folders is not working.

If I open a folder from my gnome panel under places, I get Banshee. Banshee doesn't try to do anything with the folder, as far as I can tell, but it does open. If I try to open a folder from my Docky panel, same thing - I get Banshee. If I open a folder from my desktop, I get a normal folder. And if I open a folder from within a folder, that works too.

I'm not particularly advanced when it comes to fixing these sorts of things on Linux. Could someone please point me towards the right place to start looking for the cause of this?

---

### Post by plucky on 2010-08-24
What version of Ubuntu are you using?

Normally if this happens all you have to do is open Nautilus from a terminal and then right click on a folder and select "Open with another Application" and in the window that opens,select "Open Folder".

Once opening folders is associated with "Open Folder" it will continue to do so.

Good Luck

---

### Post by DaveChild on 2010-08-28
Sorry for my slow response. I'm using 10.04.

That's fixed it. Thanks! Weird though, that it would open folders correctly from one place but not another.

---


---
title: "Gnome Shell - Printing Feature."
date: 2011-10-14
forum: General Help
---

### Post by Roasted on 2011-10-14
I noticed in 11.10/Unity when I go to System Settings - Printer - I see a logical menu with all of the features I need. The ability to add printers based on IP, etc.

I also noticed in 11.10/Gnome Shell when I go to System Settings - Printer - I see a very plain menu with few options available. When my network printer wasn't automatically found on the list, I had no idea what else to do. I mean, I couldn't add the printer by IP as the options that existed in 11.10/Unity were not there.

So I had to resort to CUPS in the web interface. Sure, it's not a big deal, but what the hell? Why would very usable features be stripped like that? Where are my options to add network printers?

EDIT - just found this. Relevant discussion is at the bottom. [http://fedoraunity.org/Members/bookwar/gnome-3-tips](http://fedoraunity.org/Members/bookwar/gnome-3-tips)

---

### Post by crdlb on 2011-10-14
I think the idea is to build a good UI for the simple cases, and then try to fit in the hard cases without making the simple cases more difficult. There certainly need to be additions for complex setups, but I think the UI is a good start.

---

### Post by Roasted on 2011-10-14
> **crdlb said:**
> I think the idea is to build a good UI for the simple cases, and then try to fit in the hard cases without making the simple cases more difficult. There certainly need to be additions for complex setups, but I think the UI is a good start.

I think it's good too. But here's my frustration.

Two network printers on network.
Gnome Shell found one, but not the other.
I wanted the other.
So what do I do?
WELL I can't install the printer via LPD because, well, it's not an option.
Show stopper right there.

Sure... for ME it's easy to go to localhost:631 and fire it up. In fact, I kind of prefer that method. But I'm trying to look at this from the point of view of relatives of mine who are beginning to use Ubuntu/Gnome Shell. They can figure things out by going to the control panel, oh hey there's a printer icon. Oh hmm this printer has an IP, let me see if I can punch it in here. Oh wow it worked!

There's no indication or instructions guiding them to localhost:631. If that is the defacto standard to use here, it should be displayed as such. 

To be honest, what would make more sense is just having an "Advanced" button which retains these features. I mean, "Advanced" = parses "system-config-printer" and bam the menu comes up. Simple solution... and I sure hope we see it. Little things.

---


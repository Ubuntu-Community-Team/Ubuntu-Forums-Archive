---
title: "Problem setting system default keyboard"
date: 2012-05-04
forum: General Help
---

### Post by SwampFalc on 2012-05-04
So, I wasn't totally happy with the standard BE layout, a few keys were dead keys when I didn't want them to be, but the variant without dead keys went too far the other way.

To try and fix that, I edited the /usr/share/X11/xkb/symbols/be file and I changed the standard layout the way I wanted.

I know this isn't a very clean approach, but I'd just like to reiterate that I **edited** the very same layout I was using at the time. You'll get why I'm emphasizing that soon.

Now, those modifications did not take effect right away. Understandable.

But they didn't even show up after I rebooted. If I use the tool to change layouts, it works! But if I check 'Use system default', it just doesn't.

Puzzled by this, I googled and found some information about dpkg-reconfigure keyboard-configuration

So I executed that and lo and behold, it did indeed change the system default keymap. Apparently, that must be a copy or something that's stored somewhere.

However, I now want to make another change to my keymap. So I went and did the same thing again: edited the symbols file, executed the dpkg-reconfigure. Think it works now?

Nope.

My system default is still the old edited version and no amount of reconfiguring changes anything. Yes, using the GUI tool I can use my new edited version, but I can't seem to install that as system default. Why? Where is that system default keymap? Some google results say that it's compiled into the kernel, but the first successful reconfigure did **not** require recompilation of anything. But why did the reconfigure work once, but not twice???

This is the sort of black magic I expect from Windows...

Can anyone shed some light on this?

---


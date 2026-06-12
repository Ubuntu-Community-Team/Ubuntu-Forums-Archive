---
title: "Chrome &quot;Aw, Snap!&quot; message when opening every single page"
date: 2011-08-29
forum: General Help
---

### Post by fcsabihu on 2011-08-29
Hi all
If anybody has been facing the same problem, I'd be glad if you shared your workaround.
Google Chrome on Ubuntu Natty gives the error message "Aw, Snap!" every time I try to open a page (even the initial page at startup). Running Chrome from terminal outputs:
```
Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `ChromeGtkFrame::scrollbar-slider-prelight-color' of type `GdkColor' from rc file value "((GString*) 0xb73f320)" of type `GString'
Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `ChromeGtkFrame::scrollbar-trough-color' of type `GdkColor' from rc file value "((GString*) 0xb73f6d0)" of type `GString'
Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `ChromeGtkFrame::frame-gradient-color' of type `GdkColor' from rc file value "((GString*) 0xb73f430)" of type `GString'
```The above messages were identical when Chrome used to work fine, no new messages appear.
Found this post at Google:
[http://www.google.com/support/chrome/bin/answer.py?hl=en&answer=95669](http://www.google.com/support/chrome/bin/answer.py?hl=en&answer=95669)

Here is how I tried the steps written on the above site:
[B]
1. Check your anti-virus and firewall applications[/B]
I have no anti-virus and firewall apps installed.
  [B]
2. Check your extensions[/B]
I tried to go to Tools->Extensions but Chrome replied "Aw, Snap!" :mad:
  [B]
3. Check for malware[/B]
I guess I dont have any, nor the pages I tried to open.
  [B]
4. Create a new user profile[/B]
Yes, I have created it but still "Aw, Snap!"

Any ideas out there?

Neils

---

### Post by MARP1961 on 2011-08-29
I suppose you've checked your connection to the router? If you are using wi-fi, is it connected to your router and not trying to connect with another nearby one?

Does another internet browser work? Try Firefox, or try uninstalling then reinstalling Chrome and see what happens.

---

### Post by fcsabihu on 2011-08-29
> **MARP1961 said:**
> I suppose you've checked your connection to the router? If you are using wi-fi, is it connected to your router and not trying to connect with another nearby one?

Does another internet browser work? Try Firefox. or try uninstalling then reinstalling Chrome and see what happens.

Hey, thank you for your help! Reinstalling Chrome just fixed it, I'd been so stupid not trying this first! Thank you!

---


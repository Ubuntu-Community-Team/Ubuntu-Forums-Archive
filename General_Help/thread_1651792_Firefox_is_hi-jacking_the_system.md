---
title: "Firefox is hi-jacking the system"
date: 2010-12-23
forum: General Help
---

### Post by lazylew on 2010-12-23
Using Firefox 3.6.13 has become impossible (Ubuntu Meerkat).
Usually not all tabs finish loading, and then everything freezes; sometimes including the cursor, sometimes the cursor will still move but not work on anything, including anything on the OS.
Every time I have to shutdown the pc cold (with the start button on the machine I mean).
I looked here [http://ubuntuforums.org/showthread.php?t=1640989]("http://ubuntuforums.org/showthread.php?t=1640989") and followed the advise of > go to &#8220;Edit >> Preferences >> Security&#8221;, uncheck &#8220;Block reported attack sites&#8221; and &#8220;Block reported web forgeries&#8221;.and installed the NoScript extension and AdBlock Plus.
It seemed fixed, but the problem came back in no time.
I wanted to follow further suggestions about the IPv6 (whatever that may be; it's mentioned in the same post) but can't get there anymore because of the Firefox freezing.
I'm glad earlier today I installed Chromium, so I can at least ask for help in the forum.

---

### Post by mghis on 2010-12-23
This probably will solve your problem, but you'll lose your bookmars.
```

mv ~/.mozilla ~/.OLD.mozilla
```

---

### Post by lazylew on 2010-12-23
> **mghis said:**
> This probably will solve your problem, but you'll lose your bookmars.
```

mv ~/.mozilla ~/.OLD.mozilla
```Thanks, but I sure hope there's another option, since the amount of bookmarks is in the hundreds.

---

### Post by lazylew on 2010-12-23
Meanwhile I tried again, starting Firefox from terminal, and was able to > disable ipv6 on Firefox Preferences, by setting the network.dns.disableIPv6 preference to true.
Type about:config in the address bar, press Enter.
Find network.dns.disableIPv6 in the list.
Right-click -> Toggle.
Restart Firefox and try again.All looked good till I closed Firefox and re-started it to watch the behavior; froze the whole system again :-(

---

### Post by RedRat on 2010-12-23
> **lazylew said:**
> Thanks, but I sure hope there's another option, since the amount of bookmarks is in the hundreds.
Not saying that this is the problem, but hundreds of bookmarks might be the source of your freeze up. You can export that bookmark list and then start adding them back after you do the .mozzila trick mentioned above.

---

### Post by lazylew on 2010-12-23
> **RedRat said:**
> Not saying that this is the problem, but hundreds of bookmarks might be the source of your freeze up. You can export that bookmark list and then start adding them back after you do the .mozzila trick mentioned above.I use xmarks, so hopefully when I modify mozilla on this pc (the main one, where they originate from) the bookmarks are still safe on my netbook? (where of course I use xmarks as well).
On the netbook I already did an export of the bookmarks, just in case, but I wonder why the amount of bookmarks (lines in the export html is 1970) could mess up my desktop and wouldn't bother a simple netbook?

---

### Post by RedRat on 2010-12-23
> **lazylew said:**
> I use xmarks, so hopefully when I modify mozilla on this pc (the main one, where they originate from) the bookmarks are still safe on my netbook? (where of course I use xmarks as well).
On the netbook I already did an export of the bookmarks, just in case, but I wonder why the amount of bookmarks (lines in the export html is 1970) could mess up my desktop and wouldn't bother a simple netbook?
It is conceivable that .mozilla directory is corrupted. I have had this happen in Firefox. If that trick works, then I would suspect corruption in the directory.

---

### Post by lazylew on 2010-12-23
> **RedRat said:**
> It is conceivable that .mozilla directory is corrupted. I have had this happen in Firefox. If that trick works, then I would suspect corruption in the directory.That makes me wonder... Nautilus has been acting weird lately too - very slow in opening some directories.
Could this be linked to the browser problem?

---

### Post by RedRat on 2010-12-23
> **lazylew said:**
> That makes me wonder... Nautilus has been acting weird lately too - very slow in opening some directories.
Could this be linked to the browser problem?
That might be indicative of a problem. How old is the hard drive? Have you had power surges or outages while the computer is on? A lot of things can corrupt a hard drive. I think Ubuntu has a "chkdsk" function, I have never used it, so perhaps someone here could help out on that. Hard drives do develop dropped bits in places, so perhaps a quick check of the disk might help.

---

### Post by lazylew on 2010-12-23
> **RedRat said:**
> That might be indicative of a problem. How old is the hard drive? Have you had power surges or outages while the computer is on? A lot of things can corrupt a hard drive. I think Ubuntu has a &quot;chkdsk&quot; function, I have never used it, so perhaps someone here could help out on that. Hard drives do develop dropped bits in places, so perhaps a quick check of the disk might help.

No power problems except me turning of the computer the very hard way (hardware button). I have meanwhile done the mv /.mozilla (etcetera) suggestion and managed to restore all bookmarks with xmarks from the netbook, so all is well I hope :-)  Meanwhile, I might add, I used Chromium for a short bit and was surprised at how fast it is and it doesn't look bad; might check it out further and after years of being faithful to the fox maybe switch...  Thanks all for helping! :-)

---

### Post by lazylew on 2010-12-24
> **RedRat said:**
> ... think Ubuntu has a &quot;chkdsk&quot; function, I have never used it, so perhaps someone here could help out on that. Hard drives do develop dropped bits in places, so perhaps a quick check of the disk might help.According to Wikipedia chkdsk is for microsoft. An equivalent on Linux is fsck, but the warnings of using it are enough to scare me away. Just saying this because even though I marked this thread "solved" last night, this morning the problem re-occurred :-( Now I threw out some add ons, hoping it'll help. The final solution for me might be to install Iceweasel instead of Firefox or use Chromium; I'll see how it goes.

---


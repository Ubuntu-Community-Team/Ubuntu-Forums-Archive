---
title: "White border around images in Firefox"
date: 2011-02-24
forum: General Help
---

### Post by Daevol on 2011-02-24
When I view an image directly in Firefox (but NOT when the image is embedded in a webpage), it has an annoying white gap around it:

[Screenshot]("http://dl.dropbox.com/u/13495464/Gorram_Border.png")

This happens in Firefox 4.0 beta (Minefield), and in 3.6 stable. It has been happening since I started using Ubuntu 10.04 and continued into 10.10. Changing the theme/appearance has no effect. I don't have this problem in Chrome or Opera.

What's going on?

Thanks!

**EDIT: Solved!**
Solution: Added "body { margin: 0px; }" to the end of **~/.mozilla/firefox[-4.0]/[profile]/chrome/userContent.css**. Apparently this is standard Firefox behavior, not an Ubuntu-specific quirk.

---


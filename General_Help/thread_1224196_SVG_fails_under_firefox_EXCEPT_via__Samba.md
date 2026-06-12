---
title: "SVG fails under firefox EXCEPT via  Samba"
date: 2009-07-27
forum: General Help
---

### Post by mikecalder on 2009-07-27
I got an odd one. AMD64, latest Jaunty, all updates.

I create web pages on an NSLU2 device on my network which have SVG pictures through <object> + <embed> tags.

If I link on my desktop via samba, firefox shows the HTML and SVG pictures as expected.

If I then open another tab on the same firefox session, but call the same page via the network link (dotted quad plus the path), the html displays fine but the SVG files are displayed as the SVG source in a box, and I get a headline popup to "Install missing plugins" - if I follow this it finds nothing.

Firefox bug, or what?


After more research, I find it's one of those bugs where the developers are digging in their heels and saying it's not a bug.  Apparently even if the web page says the mime type is "image/svg+xml" both in meta tags and the object tag itself, firefox refuses to recognise it unless there is ALSO a content header supplied by the web server which also says "image/svg+xml".  Unfortunately, the poor user/content creator can't affect that, so he's stuffed, and the html can't be presented properly.

So Firefox is borken, but they ain't going to fix it.

Fortunately, there's a bypass.

Konqueror works properly.

---


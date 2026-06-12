---
title: "SSL error renegotiation not allowed"
date: 2011-06-18
forum: General Help
---

### Post by carltonh on 2011-06-18
This may partly be a Firefox issue, but it is partly an operating system error.

To access Bank of America commercial banking site for my employment, only Firefox and Internet Explorer 7-8 are supported.  However, Firefox has a problem and says "SSL error renegotiation not allowed".  (Note that I've also tested Chromium and Opera, and it is correct that neither work.)

It had this problem on Windows XP also, however, there is a workaround in XP.  You can create an "environment variable" of "NSS_SSL_ENABLE_RENEGOTIATION" set to "1" as described here:
[http://groups.google.com/group/mozilla.dev.apps.seamonkey/browse_thread/thread/c82848f051b10159/28230b9ff15b3713](http://groups.google.com/group/mozilla.dev.apps.seamonkey/browse_thread/thread/c82848f051b10159/28230b9ff15b3713)

However, I don't know how to fix this on Ubuntu.  Are there similar "environment variables" I can create?

Aside, I also help maintain access to this website for ~100 office managers, and if any of them use Win7 with IE9, they are screwed unless I can also figure out how to make an environment variable to get Firefox to work on Win7 too.

---

### Post by carltonh on 2011-06-18
I think I may have found my answer. However, the website is down for the weekend for maintenance, so I can't check till Monday.

[http://dotomaz.tumblr.com/post/786443743/firefox-4-0b1-and-ssl-renegotiation](http://dotomaz.tumblr.com/post/786443743/firefox-4-0b1-and-ssl-renegotiation)

---


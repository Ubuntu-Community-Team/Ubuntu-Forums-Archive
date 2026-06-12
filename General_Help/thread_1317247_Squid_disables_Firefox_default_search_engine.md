---
title: "Squid disables Firefox default search engine"
date: 2009-11-06
forum: General Help
---

### Post by mac9416 on 2009-11-06
Hello, all!

I just installed Squid cache server. It was amazingly painless. The problem: when I type "ubuntu" in my location bar, instead of Firefox searching Google for "ubuntu", Squid gives returns a page reading "The following error was encountered while trying to retrieve the URL: http://ubuntu/"... so on.

Apparently, Firefox usually tries to find a server and if it fails, it just Googles the text in the location bar for me. Now with Squid handling DNS, Firefox doesn't know if the server exists or not, therefore whether to Google it for me.

I really want Squid, and I really want the default search engine feature. Any ideas?

Thanks,
-mac

---

### Post by vancouverite on 2009-11-06
Have you checked about:config to see what the value for browser.search.defaultsearchengine is?

just type about:config into the url bar and then filter the results with search.

Van

---

### Post by mac9416 on 2009-11-06
Hey, Van,

Thanks for the suggestion. I checked the default browser in about:config, and it's set to "Google". Also, when I switch off proxy support in Firefox (I have not enabled the proxy system-wide) it Googles automatically like it should.

Thanks again for the suggestion, but I'm afraid the search continues! :)
-mac

---

### Post by alecz20 on 2011-09-08
Still no solution for this?

What happens when using google chrome?

---


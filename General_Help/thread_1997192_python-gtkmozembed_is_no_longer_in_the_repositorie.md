---
title: "python-gtkmozembed is no longer in the repositories"
date: 2012-06-04
forum: General Help
---

### Post by olegio on 2012-06-04
I've upgraded to Ubuntu 12.04 and I cannot find python-gtkmozembed in the repository. I have a python program that depends on it and I cannot use it anymore. Any ideas?

---

### Post by olegio on 2012-06-05
It seems like gtkmozembed is no longer supported or available on Ubuntu 12.04 (still in 10.04 repositories). But I found a nice alternative: python-webkit, which acts very similar to gtkmozembed.

```

import webkit

web = webkit.WebView()#gtkmozembed.MozEmbed()             
settings = web.get_settings()
settings.set_property("enable-universal-access-from-file-uris", True)
web.open("google.com")     


```

---


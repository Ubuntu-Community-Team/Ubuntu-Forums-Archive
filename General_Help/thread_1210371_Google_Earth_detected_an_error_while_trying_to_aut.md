---
title: "Google Earth detected an error while trying to authenticate."
date: 2009-07-11
forum: General Help
---

### Post by Roasted on 2009-07-11
Not sure what I did to instigate this or if it was a problem that I didn't cause, but I just noticed Google Earth isn't working. I have 5.0 that I installed from a .bin file I got from Google's web site.

I couldn't figure out how to uninstall it since it wasn't in the repos but I noticed there were two hidden directories. .google-earth and .googleearth. I just decided to delete both and went to reinstall it again, but I got to the same part where I launch google earth and it gives me that error.

Not sure what the problem is.. any idea?

---

### Post by guidop on 2009-08-15
Are you running the amd 64 bit version of Ubuntu?

I had a similar error after building googleearth on debian amd64.
(I used the debian googleearth-package to build the .deb, using instructions found at:  [http://blog.irwan.name/?p=103]("http://blog.irwan.name/?p=103"))

It seems the fix for me was to install "lib32nss-mdns"

The debian bug report is at:  [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=477244]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=477244")

---

### Post by Rob_H on 2009-09-06
Thanks! I was getting the same error after installing the binaries from Google. This helped.

---


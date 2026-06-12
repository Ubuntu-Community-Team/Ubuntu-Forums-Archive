---
title: "google earth"
date: 2011-05-11
forum: General Help
---

### Post by Total Noob on 2011-05-11
Google Earth is not part of the repository, so I went to Google and followed its instructions to the letter on downloading and installing via Google and apt-get.

The process was smooth as silk. The download came in, the instructions were cut and pasted, and the compilation/installation at the end reported Success!

Only one minor glitch. 

Google Earth doesn't launch. And isn't in any packaging app so it can be deleted. 

What's next?

---

### Post by ghostborg on 2011-05-11
[https://help.ubuntu.com/community/GoogleEarth]("https://help.ubuntu.com/community/GoogleEarth")

I found this at the bottom of the above link:

Google Earth 6
Google Earth 6 not starting - /usr/lib/googleearth/googleearth-bin: not found

If you get this message, installing package "lsb-core" should help. It certainly did on my system (Ubuntu 10.10 with GoogleEarth 6.0.0.1735 (beta)), but there are several posting on the net that indicate that it may help with other combination of versions as well.

The Natty (11.04) version of googleearth-package now automatically installs the "lsb-core" package to fix this issue, it can be downloaded and installed on other Ubuntu releases from: [http://packages.ubuntu.com/natty/googleearth-package](http://packages.ubuntu.com/natty/googleearth-package)

Hope this helps you.

---

### Post by Total Noob on 2011-05-12
> **ghostborg said:**
> 

If you get this message, installing package "lsb-core" should help. 

Thanks, but I did not get that message or any other. I clicked on the menu and nothing happened at all.

I'll give lsb-core a shot though. Is it something found in a package manager or is there some very involved terminal procedure (which I am not really capable of handling)?

---

### Post by Total Noob on 2011-05-18
> **Total Noob said:**
> 
I'll give lsb-core a shot though.

That did it! Whomever is looking, add lsb-core when installing Google Earth, at least on 10.10.

Thanks.

---


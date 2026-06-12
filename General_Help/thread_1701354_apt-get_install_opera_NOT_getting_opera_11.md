---
title: "apt-get install opera NOT getting opera 11?"
date: 2011-03-06
forum: General Help
---

### Post by jtwdyp on 2011-03-06
I noticed that both my Arch Linux AND my PCLinuxOS installations have upgraded to opera 11 but my Lucid 10.04.2 LTS was still running opera 10.60

Yet apt-get install opera says: "opera is already the newest version."

So I did a google search and found:
[http://my.opera.com/desktopteam/blog/2011/01/21/a-second-opera-11-00-final-build-for-linux-freebsd](http://my.opera.com/desktopteam/blog/2011/01/21/a-second-opera-11-00-final-build-for-linux-freebsd)
which indicates that they've released an opera 11.0 that is:> This new build is squarely aimed at users of Ubuntu and other Debian based Linux distros.

I tried searching the forum with these search terms: "lucid install opera 11" But I didn't find a solution so...

[b] Do I really need to manually install opera 11 directly from my.opera.com?

Or is there something I can do so that apt-get sees it??[/b]
Note: *My sources list includes "deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable non-free"*

-- 
JtWdyP

---

### Post by lithopsian on 2011-03-06
The version you get depends on the repository you use.  See what Opera repository you are using.  "apt-cache policy opera" will tell you the version of Opera you have, the one you would get if you installed or upgraded now, and the repositories that they are from.

I have 11.01.1190 from [http://deb.opera.com](http://deb.opera.com) stable/non-free

---

### Post by Frogs Hair on 2011-03-06
Download the .deb from here if you have 64 bit. My Opera 11 alpha and beta did not update I had to install each one . The Opera stable source will show up in your list when installed. [http://www.opera.com/browser/download/](http://www.opera.com/browser/download/)

---

### Post by jtwdyp on 2011-03-06
[QUOTE=lithopsian]The version you get depends on the repository you use. See what Opera repository you are using. "apt-cache policy opera" will tell you the version of Opera you have, the one you would get if you installed or upgraded now, and the repositories that they are from.

I have 11.01.1190 from [http://deb.opera.com](http://deb.opera.com) stable/non-free
[/QUOTE]

Thanks for replying...

First let me say I feel like an idiot because when I said"

> *Note: My sources list includes "deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable non-free"*

I evidentaly was looking at opera.list.distUpgrade rather than opera.list Where it had been commented out when I upgraded from karmic to Lucid...

However Now that I fixed that. And installed opera 11.01 on both my desktop and my laptop, I noticed some error messages in the apt-get output

```

Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for menu ...
Processing triggers for packagekit-backend-apt ...
Generating mime/codec maps...
Processing triggers for software-center ...
Processing triggers for python-support ...
Processing triggers for python-central ...
Setting up opera (11.01.1190) ...
Error in file "/usr/share/applications/kde4/kfontview.desktop": "fonts/package" is an invalid MIME type ("fonts" is an unregistered media type)
Error in file "/usr/share/applications/gnumeric.desktop": "zz-application/zz-winassoc-xls" is an invalid MIME type ("zz-application" is an unregistered media type)
Error in file "/usr/share/applications/clamtk.desktop": "vms/exe" is an invalid MIME type ("vms" is an unregistered media type)

Processing triggers for menu ...


```

** Would anybody know why I get these? Should I worry about them? **

-- 
JtWdyP

---


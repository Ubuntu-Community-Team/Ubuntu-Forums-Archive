---
title: "Custom url-handlers fails to register in browsers"
date: 2011-05-04
forum: General Help
---

### Post by elundmark on 2011-05-04
Operating System: Ubuntu 11.04 w/ Unity-2D

I had serveral custom url-handlers setup using gconftool-2 in my old Ubuntu 10.10 setup, but now after reinstalling and updating to Ubuntu 11.04 I can't get a single one to work with Chrome (11.0.696.57) nor other browsers like Midori.

The only solution was to switch to Firefox and setup them manually using network.protocol-handler*

It seems (on the surface) that Chrome insists on opening the links with xdg-open ([COLOR="Red"]*and if I remember correctly in Ubuntu 10.10 Chrome said it opened the links using the apps set in gconf), but xdg-open only supports the most common http* and ftp* does it not?*[/COLOR] - Just learned that xdg-open is the default handler for all urls.

Does anyone have the same problem as I do? Any ideas?
I've tried everything, including searching through Chrome's config files, reinstalling Chrome, and tested changing the paths to my apps -  but without any luck.

*Note that I'm talking about links in Google Chrome, Firefox on the other hand doesn't even check the url-handlers so I had to set them up manually using about:config > network.protocol-handler**

So they work in Firefox when added, but in no other browsers.

Google Chrome opens the links with xdg-open [url] as depicted in the attacheds screenshot, but this throws in error, found in **.xsession-errors**:

```
gvfs-open: svtrip://example.com/: error opening location: The specified location is not supported
```

---

### Post by elundmark on 2011-05-08
(bad-forum-policy) Bump!

I've realized that it's xdg-open (xdg-utils) that causes this problem, why won't it update to include my custom handlers?

I've tripple-checked the spelling and so forth. And even reinstalled xdg-utils.

Still, run from the terminal I get

```
$ (xdg-open|gnome-open|gvfs-open) [customhandler://url]
: error opening location: The specified location is not supported
```

---

### Post by vilain_mamuth on 2011-05-27
try to find the .desktop file for the application that opens svtrip: links and add a MimeType key

see this bug for an example

[https://bugs.launchpad.net/bugs/788673](https://bugs.launchpad.net/bugs/788673)

---


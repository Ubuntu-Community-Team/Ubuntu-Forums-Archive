---
title: "Bing has hijacked my keyword search"
date: 2010-09-19
forum: General Help
---

### Post by chrisod on 2010-09-19
I keep editing URL:keyword back to the default (Google) and when I close and reopen Firefox it is back to Bing. I have disabled the Ubuntu Add-On for Firefox, so it's not some backroom deal between Canonical and MS causing this. If I search about:config for Bing the only place is comes up is the URL:keyword config option. I have also removed Bing from the search box options. This is happening in both Swiftfox and Firefox -whatever the most recent version of both is.

Does anybody have any idea what the hell is hijacking my browser and changing the keyword search default?

---

### Post by robsoles on 2010-09-20
No idea, ***yet***...

My first suspicion is extensions and plugins, have you added many to firefox?

Could you consider disabling every last plugin and extension for firefox, change back to 'google', quit firefox and re-open it?

If that makes it stay on 'google' then it is a matter of enabling a couple of extensions at a time till it does it and then weeding out the extension in particular that does it.

If it doesn't stay on google with all extensions and plugins disabled then I think I would like a squiz at your dpkg logs for suss installs. Although I should point out that binaries and '*helpers*' don't have to be installed by dpkg, we can only hope for a little luck...

---

### Post by cwwilson721 on 2010-09-20
Actually, there is a quick fix
To the left of the drop-down search box is a Down arrow, click that, "Manage search engines"

You can change your default in there (Move it to the top of the list, and can remove Bing completely, if you wish)

---

### Post by robsoles on 2010-09-20
> **chrisod said:**
> ...

I have also removed Bing from the search box options. ...

...

I'm operating on the idea they already did that.

---

### Post by Begin_learn on 2010-09-20
it is surely due to some firefox plugins.cant allege cannonical.anyways you can remove bing from manage search engines in the drop down at upper right corner

---

### Post by chrisod on 2010-09-22
I found a simple solution. Exported bookmarks and renamed the .mozilla directory. When it created a new .mozilla on start Bing was gone. I had to import bookmarks and reinstall my plug ins - but it wasn't that big of a deal.

---


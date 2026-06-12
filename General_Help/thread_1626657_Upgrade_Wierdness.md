---
title: "Upgrade Wierdness"
date: 2010-11-20
forum: General Help
---

### Post by PerfectReign on 2010-11-20
I have a laptop running 9.1 with standard GNOME environment.

I noticed the other day, I got a message, that stated, "Problem during package list update. The package list update failed with a authentication failure."

I was behind my corporate firewall so I didn't think much of it.  I got it again this morning and I'm at home with no proxy server between me and teh intraweb.  

The full message is: 

> Problem during package list update. The package list update failed with a authentication failure. This usually happens behind a network proxy server. Please try to click on the "Run this action now" button to correct the problem or update the list manually by running Update Manager and clicking on "Check".

There's a command button, stating **Run This Action Now**. I clicked it and got a subsequent message:

> W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://linux.dropbox.com](http://linux.dropbox.com) karmic Release: The following signatures were invalid: NODATA 1 NODATA 2

W: Failed to fetch [http://linux.dropbox.com/ubuntu/dists/karmic/Release](http://linux.dropbox.com/ubuntu/dists/karmic/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.


Searching got me nothing. Any ideas?

---


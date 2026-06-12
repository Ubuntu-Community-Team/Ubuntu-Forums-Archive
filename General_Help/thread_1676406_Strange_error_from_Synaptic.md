---
title: "Strange error from Synaptic"
date: 2011-01-27
forum: General Help
---

### Post by FokkerCharlie on 2011-01-27
Hi

Every time I hit 'reload' in Synaptic, I get this error:

Failed to fetch [https://private-ppa.launchpad.net/commercial-ppa-uploaders/vendetta-online/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](https://private-ppa.launchpad.net/commercial-ppa-uploaders/vendetta-online/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  The requested URL returned error: 401
Some index files failed to download, they have been ignored, or old ones used instead.

It's a bit odd.  I don't particularly want to install Vendetta just now, but it would be nice to know what's causing this.

Any ideas?

Thanks in advance.

Charlie

---

### Post by justleen on 2011-01-27
You added a repositry which requires authorization.. Seems to me its not a correct PPA repro.

---

### Post by FokkerCharlie on 2011-01-27
Hi Justleen

Thanks for your response.  I realised that the PPA URL has not come out properly in the forum, so here it is with the http missed out:

private-ppa.launchpad.net/commercial-ppa-uploaders/vendetta-online/ubuntu/dists/maverick/main/binary-amd64/Packages.gz

I did not add this PPA myself, but I think it may have been installed by the Software Centre.  I don't see it in the repo list in Synaptic, and I'd rather leave the 'for purchase' repos in place in case I need them later.

Any other suggestions?

Charlie

---

### Post by justleen on 2011-01-27
Yes, re-add is. It wrong the way it is now, as far as I can tell (the package.gz shouldnt be there), and its definitly an https site asking for auth. 401 error is an auth error.

---

### Post by FokkerCharlie on 2011-01-27
Right... so how do I go about re-adding the commercial repo?

---

### Post by justleen on 2011-01-27
How did you add it in the first place?  I'm assuming its on the vendetta site?

---

### Post by FokkerCharlie on 2011-01-27
No, that's the thing.  I think it was added automatically by the Software Centre.  If I had added it myself, I could figure this one out no problem!

Charlie

---

### Post by justleen on 2011-01-27
If it added it there automagicly, Im pretty sure you can remove it, and later it will be added again?

---

### Post by FokkerCharlie on 2011-01-27
Well, I found the entry in the software sources labelled 'Added by Software Centre', and unticked it.  The original Synaptic error has now gone.

However, if I try installing (as a test) Vendetta, I get the same error from the Software Centre.

Which is a bit strange.

Charlie

---


---
title: "Can't access medibuntu"
date: 2012-04-18
forum: General Help
---

### Post by abovett on 2012-04-18
As of this morning (18th April 2012) I can't access medibuntu. Trying to do an update (sudo aptititude update) gives:

 Unable to connect to packages.medibuntu.org:http:

I'm getting this on several PCs with both oneiric and precise, and I've not made any changes to them.

Anyone else having this problem, or know what's going on?

Andy

---

### Post by wojox on 2012-04-18
What if you ping it?

```
ping -c 3 packages.medibuntu.org
```

Tested and it works on my 12.04 install

---

### Post by oldfred on 2012-04-18
I thought it was not required now.

Did you install the restricted extras as part of the install?

If not:
apt-get update
apt-get upgrade
apt-get install ubuntu-restricted-extras

From synaptic:
> Installing this package will pull in support for MP3 playback and decoding,
support for various other audio formats (GStreamer plugins), Microsoft fonts,
Flash plugin, LAME (to create compressed audio files), and DVD playback.


---

### Post by abovett on 2012-04-19
> **wojox said:**
> What if you ping it?
It responds to pings, and I can even pull individual package lists down with wget, but when I do an update from aptitude or apt-get, I get a bunch of messages such as:
```
Err http://packages.medibuntu.org precise/free Sources
  Unable to connect to packages.medibuntu.org:http:

```
repeated for various package lists, and further down:
```
W: Failed to fetch http://packages.medibuntu.org/dists/precise/free/source/Sources  Unable to connect to packages.medibuntu.org:http:

```
I'm puzzled, because this succeeds:
```
wget http://packages.medibuntu.org/dists/precise/free/source/Sources
```
This is happening on several PCs, some running precise and some running oneiric.

Anyone know what's different between the way aptitude or apt-get connect and the way wget connects? I suppose I could run wireshark on it but I suspect this will get complicated pretty quickly.
> **oldfred said:**
> I thought it was not required now.

Did you install the restricted extras as part of the install?
Thanks, ubuntu-restricted-extras probably contains most of what I want, but the medibuntu project is still live (they've just added the precise repository) and I think it contains more than the ubuntu-restricted-extras package. I might consider switching for new installs but I'd prefer my existing installs to continue to work with medibuntu.

Thanks

Andy

---

### Post by abovett on 2012-04-20
A bug report has been raised on launchpad for this issue, Bug #985441: Medibuntu offline. The comments include some workarounds.

---


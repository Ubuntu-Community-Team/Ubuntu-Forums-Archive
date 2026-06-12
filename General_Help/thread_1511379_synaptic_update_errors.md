---
title: "synaptic update errors"
date: 2010-06-16
forum: General Help
---

### Post by panos_thes on 2010-06-16
Using 10.04 LTS (x64) for more than 2 weeks with no issues, but today when i hit "Reload" in Synaptic i got the following strange errors:
> W: GPG error: [http://archive.canonical.com]("http://archive.canonical.com/")  lucid Release: Internal error: Good signature, but could not determine  key fingerprint?!
W: GPG error: [http://packages.medibuntu.org]("http://packages.medibuntu.org/")  lucid Release: Internal error: Good signature, but could not determine  key fingerprint?!
W: GPG error: [http://security.ubuntu.com]("http://security.ubuntu.com/")  lucid-security Release: Internal error: Good signature, but could not  determine key fingerprint?!
W: GPG error: [http://ppa.launchpad.net]("http://ppa.launchpad.net/")  lucid Release: Internal error: Good signature, but could not determine  key fingerprint?!
W: GPG error: [http://ppa.launchpad.net]("http://ppa.launchpad.net/")  lucid Release: Internal error: Good signature, but could not determine  key fingerprint?!
W: A error occurred during the signature  verification. The repository is not updated and the previous index files  will be used.GPG error: [http://ppa.launchpad.net]("http://ppa.launchpad.net/")  lucid Release: Internal error: Good signature, but could not determine  key fingerprint?!

W: GPG error: [http://ppa.launchpad.net]("http://ppa.launchpad.net/")  lucid Release: Internal error: Good signature, but could not determine  key fingerprint?!
W: GPG error: [http://ppa.launchpad.net]("http://ppa.launchpad.net/")  lucid Release: Internal error: Good signature, but could not determine  key fingerprint?!
W: A error occurred during the signature  verification. The repository is not updated and the previous index files  will be used.GPG error: [http://ppa.launchpad.net]("http://ppa.launchpad.net/")  lucid Release: Internal error: Good signature, but could not determine  key fingerprint?!

W: GPG error: [http://ppa.launchpad.net]("http://ppa.launchpad.net/")  lucid Release: Internal error: Good signature, but could not determine  key fingerprint?!
W: GPG error: [http://ppa.launchpad.net]("http://ppa.launchpad.net/")  lucid Release: Internal error: Good signature, but could not determine  key fingerprint?!
W: GPG error: [http://download.virtualbox.org]("http://download.virtualbox.org/")  lucid Release: Internal error: Good signature, but could not determine  key fingerprint?!
W: GPG error: [http://gr.archive.ubuntu.com]("http://gr.archive.ubuntu.com/")  lucid Release: Internal error: Good signature, but could not determine  key fingerprint?!
W: A error occurred during the signature  verification. The repository is not updated and the previous index files  will be used.GPG error: [http://gr.archive.ubuntu.com]("http://gr.archive.ubuntu.com/")  lucid-updates Release: Internal error: Good signature, but could not  determine key fingerprint?!

W: Failed to fetch [http://ppa.launchpad.net/chromium-daily  ... id/Release]("http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/dists/lucid/Release")  

W: Failed to fetch [http://ppa.launchpad.net/ubuntu-wine/pp  ... id/Release]("http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/lucid/Release")  

W: Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/dis  ... es/Release]("http://gr.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release")  

W: Some index files failed to  download, they have been ignored, or old ones used instead.any ideas how to fix it pls?  :confused:

---

### Post by wojox on 2010-06-16
Try:

```
sudo apt-get install gnupg add-apt-key
```

---

### Post by lidex on 2010-06-17
Try this. In a Terminal="Applications->Accessories->Terminal"
```
sudo apt-get install --reinstall gnupg gpgv gnupg-curl
```

---

### Post by panos_thes on 2010-06-18
thanks both of you!! that did the trick :)
still cannot understand how the hell gpgv packet get corrupted...
):P

---


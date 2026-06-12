---
title: "Cannot update universe packages"
date: 2006-02-07
forum: General Help
---

### Post by Zeroangel on 2006-02-07
I've just installed Ubuntu as my main OS at home.

So now while trying to enable the universe repositories (for MP3 support) I keep getting stuck while trying to download the Breezy universe binary repositories.

Synaptic says that its 'Downloading File 11 of 11' and just stays there (the package and sources say 'hit', in the progress bars) until it eventually times out. So I did an apt-get to continue with the installation of the codecs but I am still getting errors.

I have a cable connection, have never noticed the presence of a firewall before. So I doubt that is the case.

Can anyone help me?

---

### Post by goatflyer on 2006-02-07
The ones that say Hit and 0 bytes are not responding.  If you cancel, you can still use Synaptic with the still-working repositories.

If some repositories remain consistently down, and you get annoyed with the delay (like I do), you can temporarily disable them by unchecking the boxes in Synaptic>Settings>Repositories.   Remember to try them later.

---

### Post by Zeroangel on 2006-02-08
I found the solution!

Synaptic was prepending "ca." (ie: [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com)) to all of the download URLs. So I went into Setting -> Repositories and removed the "ca." and voila! The new repositories are now working.

---

### Post by kaamos on 2006-02-08
Here is quick way to do that. Applications->Accessories->Terminal
```
sudo gedit /etc/apt/sources.list
```
after you have done the changes:
```
sudo apt-get update
```

---


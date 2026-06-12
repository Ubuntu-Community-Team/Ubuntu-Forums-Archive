---
title: "Serpentine"
date: 2010-09-30
forum: General Help
---

### Post by alan_uk on 2010-09-30
Has Serpentine (Audio burner) been removed from the repositories?
Using the Synaptic Package Manager I note that Serpentine is no longer available. I like this app a lot as it allows you to remove the 2 second gap between tracks, its reliability and its ease of use. I am using Ubuntu 10.4 Can anybody confirm this?

Thanks

Alan

---

### Post by gzarkadas on 2010-10-01
It should be in the universe repository; at least this is true for Karmic.

If after enabling the universe repository you type `serpentine' in the search box of the synaptic window and nothing comes up, then yes it has been removed. The truth is that the last serpentine package contained in the Ubuntu pool is dated from 4-May-2009.

However you can manually download it from [http://archive.ubuntu.com/ubuntu/pool/universe/s/serpentine/serpentine_0.9-6ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/s/serpentine/serpentine_0.9-6ubuntu1_all.deb) and use `sudo dpkg -i [full-name-of-the-deb-file].deb' to install it. Don't forget to verify-for safety reasons- the package's hash before installing it.

---


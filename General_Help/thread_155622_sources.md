---
title: "sources"
date: 2006-04-05
forum: General Help
---

### Post by Moses on 2006-04-05
Hi

I'm getting this message when I open Synaptic:

W: Couldn't stat source package list [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)


And all downloads I try to make, fail.

Could someone please send me their sources.lst (if that would help)


Thanks

---

### Post by Al3xanR0 on 2006-04-05
[QUOTE=Moses]Hi

I'm getting this message when I open Synaptic:

W: Couldn't stat source package list [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)


And all downloads I try to make, fail.

Could someone please send me their sources.lst (if that would help)


Thanks[/QUOTE]

Try going [here]("http://www.ubuntulinux.nl/source-o-matic"), this helped me out a great deal in my search for relevency.

---

### Post by kozmo on 2006-04-05
If you are using a proxy server make sure you specify the settings in Synaptic Package Manager.

---

### Post by Al3xanR0 on 2006-04-05
[QUOTE=kozmo]If you are using a proxy server make sure you specify the settings in Synaptic Package Manager.[/QUOTE]

Now that you mention it, proxy sounds like it may be at the root of your issue. If so you caould also edit your /etc/apt.conf by adding:

```

ACQUIRE {
    Retries "3";
    Http {
        Proxy "http://userid:passwd@proxy.address.something.com:80/"; 
    }
};

```

see if that works.

---


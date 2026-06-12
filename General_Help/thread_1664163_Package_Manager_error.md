---
title: "Package Manager error"
date: 2011-01-10
forum: General Help
---

### Post by Gabrias on 2011-01-10
I am getting the following error when trying to open the Package Manager.
This is Ubuntu 10.10

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E: Problem with  MergeList  /var/lib/apt/lists/br.archive.ubuntu.com_ubuntu_dists_maverick_main_binary-i386_Packages, E:The package lists or status file could not be  parsed or opened.'

My ubuntu is Portuguese, I took the liberty of translating to facilitate the understanding.

---

### Post by uyulala on 2011-01-15
Hi,

You could try this simple workaround: Delete the contents of "/var/lib/apt/lists/", and tyr again.

F.ex.using the following commands

$ sudo rm -f /var/lib/apt/lists
$sudo apt-get update


A lot of people are reporting this kind of error messages. For some of them (including myself) the reason was that update-manager had run once  while the computer was connected to a wireless hotspot which presents a login page (typical at hotels, airports, cafes). When the update-manager tried to download the "MergeList" mentioned, it got the wireless hotspot login page instead. You can check it by looking at the list mentioned in the error message, "/var/lib/apt/lists/br.archive.ubuntu.com_ubuntu_dists_maverick_main_b  inary-i386_Packages". Does it look like a list of package information, starting with "Package:". In my case it was a html-page with a login form.



Good luck!

Harald Stendal

---


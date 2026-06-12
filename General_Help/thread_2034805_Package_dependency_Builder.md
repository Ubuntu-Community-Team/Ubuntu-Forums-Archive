---
title: "Package dependency Builder"
date: 2012-07-29
forum: General Help
---

### Post by khalafuf on 2012-07-29
Hi, 

I was looking for a tool that does more than package dependency checking. It should, for example, take a package name (stored in var/cache/apt/acrhives) and build an archive combining all the .deb files it depends on.

I hope such a tool exists. :)

Any help would be appreciated.

Many thanks.

---

### Post by Cheesehead on 2012-07-29
Every time you run that kind of tool to add one 50kB new package, it will generate a 300MB or larger install archive, most of which will be unused. Possibly *all* of it will be unused - some users will erroneously download the wrong version of the package.

The tool has no way of knowing what is already installed, so it has to include *everything*, including hundreds of packages that are already included in ubuntu-desktop, ubuntu-standard, etc. Some users may have modified their base install, so the tool can't really assume anything safely.

Various offline-install methods like Synaptic or apt-zip use the offline system's package manager to produce a list of just the packages needed. That reduces the download size to a more useful size, and ensures the correct version.

What is it you are really trying to do? Someone may have figured out an easier way...

For example, the following command uses a bunch of sed to convert a Synaptic download script (needs a Linux system to work) into a page of hyperlinks (cross-platform, any browser will work). One command like this can save you hours of unneccesary downloading. The resulting list of HTML links can be opened in any web browser to download only the packages you actually need. Then use Synaptic;s File-->Add downloaded packages feature to install them.
```
cat download-script | sed -e '1d' -e 's|wget -c ||' -e 's|http.*deb|<a href="&">&</a>|' > download-links.html

# The command in detail:
cat download-script | \                     # Read the download script file (called "download-script")
sed -e '1d' \                               # Delete the first line "#!/bin/sh" 
    -e 's|wget -c ||' \                     # Delete the wget commands
    -e 's|http.*deb|<a href="&">&</a>|' \   # Covert the package url into an HTML link
> download-links.html                       # Write the output to a file (called "download-links.html")


```

Alternately, apt-offline generates download scripts that are compatible with Windows, and can also update/upgrade your system easily and reliably.

---

### Post by khalafuf on 2012-08-22
Sorry for the late reply.

My problem is as follows:

I often use Synaptic's feature (Generate Download Script) because of my  internet connection status. So, I make a folder for each package I  download (to include the dependency packages). But sometimes, some of  these dependency packages are already installed previously somewhere  else. So, What can I do if I want to install this package on another  machine, without unnecessary download?

---


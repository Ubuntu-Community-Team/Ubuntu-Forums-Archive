---
title: "Where do you find program executable files"
date: 2009-12-24
forum: General Help
---

### Post by webbdawg on 2009-12-24
I am trying to point My Fire Fox 3.0 to Thunderbird when I click a mailto: link.

Menu>Edit>Preferences>Applications choose mailto

I am able to navigate to the etc file and see the Thunderbird folder but I see no exe files.

Where are the exe files?

---

### Post by taurus on 2009-12-24
Thunderbird should be in /usr/bin.  Most of the programs are located in /usr/bin.

Applications -> Accessories -> Terminal
```
whereis thunderbird
```

---

### Post by lloyd_b on 2009-12-24
> **webbdawg said:**
> I am trying to point My Fire Fox 3.0 to Thunderbird when I click a mailto: link.

Menu>Edit>Preferences>Applications choose mailto

I am able to navigate to the etc file and see the Thunderbird folder but I see no exe files.

Where are the exe files?

The executable is "/usr/bin/thunderbird".  Most executable programs are located in that directory.  Note that on Linux, executables don't have the ".exe" extension.

Lloyd B.

---

### Post by teward on 2009-12-24
you should just be able to set your default mail client.  in 9.04, under System -> Preferences -> Preferred Applications, you can set what is/isnt your default program(s)

Not sure what distro you're using, though.

---

### Post by geirha on 2009-12-24
An important thing to note is that in unix/linux (which includes Ubuntu), applications are spread around the filesystems based on the filetype. In windows, an application mainly puts all its files under a folder in Program Files, but in Ubuntu, executables gets put it /usr/bin, libraries in /usr/lib, documentation in /usr/share/doc and /usr/share/man, images, icons, sounds and similar are put in equivalent folders under /usr/share/. Global configuration for the application (if applicable) goes into /etc, per-user configuration goes into your homedir in hidden folders. Typically .appname/, or now adays, the standard is to put it in .config/appname in your homefolder.

See this for more in-depth information: [http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

---


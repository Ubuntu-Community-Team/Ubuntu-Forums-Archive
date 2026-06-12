---
title: "Tabs just don't work the way they used to."
date: 2009-11-18
forum: General Help
---

### Post by commodore256 on 2009-11-18
On the last distro, you can use tabs to auto complete a command

Example:

You type in ```
sudo apt-
``` hit Tab twice and it will say ```
apt-cache             apt-extracttemplates  apt-key
apt-cdrom             apt-ftparchive        apt-mark
apt-config            apt-get               apt-sortpkgs
```

I want to use apt-get, so I add ```
ge
``` to the command and hit tab and it will say ```
sudo apt-get
```

I wanna install so I would normally add ```
 i
``` hit tab and it will say ```
sudo apt-get install
```

I wanna install Chromium, (after the ppa was added) so I add ```
 chromi
``` hit tab twice and normally, the output will be something like this:

```
sudo apt-get install chromium

chromium
chromium-bsu
chromium-bsu-data
chromium-data
chromium-testsuite-dbg
chromium-testsuite
chromium-codecs-ffmpeg-nonfree-dbg
chromium-codecs-ffmpeg-nonfree
chromium-codecs-ffmpeg-dbg
chromium-codecs-ffmpeg
chromium-browser-l10n
chromium-browser-inspector
chromium-browser-dbg
chromium-browser

```

OK, I want the Browser, so I add ```
-br
``` hit tab and it will say ```
sudo apt-get install chromium-browser
``` then I would hit enter, put in my password and install the package.

You can't do that anymore or at least not by default and it's hard to find "google friendly terms" to search up this issue.

I just want my tabs back.

---

### Post by hwttdz on 2009-11-18
That's called bash auto-completion.  

Usually one has something of this sort in their .bashrc
```
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi
```

Do you?

---

### Post by commodore256 on 2009-11-18
Whoops, This isn't an Ubuntu Problem, this is a Arch Linux Problem.

I had the same problem in Arch and I used the Home Partition from Arch and just installed ubuntu on my root partition. (Arch has nothing Pre-configured)

Thanks!

---


---
title: "Is there a standalone codec update package?"
date: 2012-01-06
forum: General Help
---

### Post by jacatone on 2012-01-06
I've got to install the codecs on a bunch of Ubuntu 10.04 and 10.10 machines. Is there a standalone update package for all the needed codecs without having to download and install them separately? Thanks.

---

### Post by 67GTA on 2012-01-06
All installed packages are cached in /var/cache/apt/archives. You could just save a copy of the packages to install offline. You could also create a script such as "sudo apt-get install <list_of_packages>" and run it on each machine.

---

### Post by jacatone on 2012-01-07
How would I create this script?

---

### Post by imachavel on 2012-01-07
try this if you don't know how to write scripts(which I don't either):

[http://www.noobslab.com/2011/10/install-mplayer-with-multimedia-codecs.html](http://www.noobslab.com/2011/10/install-mplayer-with-multimedia-codecs.html)

[COLOR=red]sudo apt-get install mplayer

[COLOR=Black]now if you install that, it should also install necessary codecs along the ways. I found a great video of installing codecs in linux mint online. The main problem there is, if you don't have a video decoder, how can you watch the video?? :KS[/COLOR]
[/COLOR]

---

### Post by 67GTA on 2012-01-07
A simple bash script would do. It will take a little work, but once it was done, it would be a matter of running the script on each machine to install all the wanted apps/packages. The only thing you would have to do would be to update the script if any of the package names changed between releases. Just copy and paste this into a new file, and then add the package names to it:

```
#!/bin/bash

sudo apt-get update && sudo apt-get install

```Save it as install_codecs or what ever you want. Make it executable with ```
chmod +x install_codecs
``` Then simply run this in a terminal and enter your password when prompted. If some of the codecs are from the medibuntu repo you could incorporate the medibintu script in to it like this:

```
#!/bin/bash

sudo -E wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update 
 
sudo apt-get install app-install-data-medibuntu apport-hooks-medibuntu
```Then add your packages after "apport-hooks-medibuntu"

---


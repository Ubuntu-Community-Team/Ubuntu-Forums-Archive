---
title: "medibuntu not found"
date: 2010-02-27
forum: General Help
---

### Post by CatchItBaby on 2010-02-27
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

I follow this guide in my fresh ubuntu and when i search for medibuntu it didn't show anything


[IMG]http://i48.tinypic.com/2ptwf80.jpg[/IMG]

where i m doing wrong

---

### Post by jmszr on 2010-02-27
Error

---

### Post by oldfred on 2010-02-27
Did you enable the repository. In my system I show 4 things installed.

But I do it from the command line and save my history from the command line (history) so I can rerun all the commands on a new install.

List copied from my history:

  28  sudo apt-get install flashplugin-nonfree
   29  sudo apt-get update && sudo apt-get install ubuntu-restricted-extras
   30  sudo apt-get update
   31  sudo apt-get install medibuntu-keyring
   32  sudo apt-get install w64codecs libdvdcss2
   84  wget [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg)
   85  sudo apt-key add medibuntu-key.gpg

this was from my other computer and now I do not know why they are different as I did both separately from various sources.
   86  sudo apt-get install flashplugin-nonfree
   87  sudo apt-get install medibuntu-keyring
   88  sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
   89  sudo apt-get install medibuntu-keyring
   92  sudo apt-get autoremove
   93  sudo apt-get --yes install app-install-data-medibuntu apport-hooks-medibuntu

   95  sudo apt-get install medibuntu-keyring
   96  sudo apt-get update && sudo apt-get upgrade
   97  sudo apt-get install w64codecs libdvdcss2

---

### Post by coffeecat on 2010-02-27
[Medibuntu home page]("http://www.medibuntu.org/")

...which links to.....

[Medibuntu repository howto]("https://help.ubuntu.com/community/Medibuntu")

Follow the directions in the second link and you should be fine.

---


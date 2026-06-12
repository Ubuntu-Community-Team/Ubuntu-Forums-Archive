---
title: "When will installing Google Earth not be so ridiculous?"
date: 2010-11-13
forum: General Help
---

### Post by Roasted on 2010-11-13
Each edition of Ubuntu comes with a new set of instructions. Normally, they work. Today, they did not. I'm on 10.10 and followed a simple 3 step guide. Google Earth opens, but the world area on the right is black. No globe. On the left you have the filters, layers, etc. All white. No options.

Come on...

---

### Post by wojox on 2010-11-13
have you tried this [Install Google Earth in Ubuntu 10.10 Maverick Meerkat]("http://www.liberiangeek.net/2010/09/install-google-earth-ubuntu-10-10-maverick-meerkat/")

---

### Post by Roasted on 2010-11-13
> **wojox said:**
> have you tried this [Install Google Earth in Ubuntu 10.10 Maverick Meerkat]("http://www.liberiangeek.net/2010/09/install-google-earth-ubuntu-10-10-maverick-meerkat/")

That was actually the EXACT guide I used that didn't work.

Where's the deb package at? :(

---

### Post by sohlinux on 2010-11-13
I installed from the bin file
[http://dl.google.com/earth/client/current/GoogleEarthLinux.bin](http://dl.google.com/earth/client/current/GoogleEarthLinux.bin)


or try the deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/)

---

### Post by Roasted on 2010-11-13
> **sohlinux said:**
> I installed from the bin file
[http://dl.google.com/earth/client/current/GoogleEarthLinux.bin](http://dl.google.com/earth/client/current/GoogleEarthLinux.bin)


or try the deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/)

Where's the deb at?

[http://packages.medibuntu.org/maverick/index.html](http://packages.medibuntu.org/maverick/index.html)

Binary Results:


Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 5.2.1.1588..............................................................
setup.data/setup.xml:1: parser error : Document is empty

^
setup.data/setup.xml:1: parser error : Start tag expected, '<' not found

^
Couldn't load 'setup.data/setup.xml'
jason@Area51:~$

---

### Post by sohlinux on 2010-11-13
bet you have some missing libs,for Maverick Meerkat 32 bits try the following

sudo apt-get install ia32-libs lib32nss-mdns

sudo apt-get install googleearth-package

make-googleearth-package --force

sudo dpkg -i googleearth_your_package_name

---

### Post by Roasted on 2010-11-13
> **sohlinux said:**
> bet you have some missing libs,for Maverick Meerkat 32 bits try the following

sudo apt-get install ia32-libs lib32nss-mdns

sudo apt-get install googleearth-package

make-googleearth-package --force

sudo dpkg -i googleearth_your_package_name

When I tried apt-get of that stuff, it said 0 needed or upgraded. Guess I have them?

Google - I hope you're listening.

---

### Post by jcolyn on 2010-11-13
> **Roasted said:**
> Where's the deb at?

Here ya go. Scroll to the bottom and choose which one best suits your system i386 or amd64 download to your home folder then click it for install it should also download a needed file while installing.

[http://packages.medibuntu.org/lucid/googleearth.html](http://packages.medibuntu.org/lucid/googleearth.html)

---

### Post by Roasted on 2010-11-13
> **jcolyn said:**
> Here ya go. Scroll to the bottom and choose which one best suits your system i386 or amd64 download to your home folder then click it for install it should also download a needed file while installing.

[http://packages.medibuntu.org/lucid/googleearth.html](http://packages.medibuntu.org/lucid/googleearth.html)

Bingo! Thanks!

What's funny is, it wouldn't let me install because a later version is already installed. So I ran apt-get remove --purge googleearth and it said 0 bytes to be removed, but ran anyway. Then I installed the deb and it worked fine. The only thing is, it was slow to connect at first. Like I saw the globe and was typing in Philadelphia PA and it just sat there. Then I got an error it couldn't connect to servers but before I could read the entire error, it began to zoom into Philly. 

"Google Earth could not establish a new session with the EarthServer. Although Google Earth will continue to operate, it will only display data available locally (in cache). Google Earth will try to re-establish a session periodically and will inform you when successful."

Each time I open it, it takes a few seconds to connect. Anybody else seeing this?

But hey, glad it's installed. Thanks!

---


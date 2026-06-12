---
title: "Trouble installing 'I HATE the Cashew' in Linux Mint 9 KDE!"
date: 2010-11-06
forum: General Help
---

### Post by Rytron on 2010-11-06
Hi.

I am trying to install "[I HATE the Cashew]("http://kde-look.org/content/show.php/I+HATE+the+Cashew?content=91009")" in KDE.

I get to ```
ccmake ..
``` and then I get this [picture attached]. How do I complete installation?

Thanks.

---

### Post by Rytron on 2010-11-06
I don't know if all of these are required!

```
sudo apt-get install apt-file build-essential cmake kde-devel libphonon-dev
```

cd iHateTheCashew
mkdir build
cd build
# Now we’re ready to compile the plasmoid:
cmake -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix` ..
make
make && sudo make install

Done! :)

---


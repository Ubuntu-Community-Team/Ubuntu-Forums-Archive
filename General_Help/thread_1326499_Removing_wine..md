---
title: "Removing wine."
date: 2009-11-14
forum: General Help
---

### Post by Lamez on 2009-11-14
Okay, well I am trying to get "Call of Duty 4: Modern Warfare" to work with wine, so I have been reading up on some tutorials that have worked. No luck so far. 

Anywho, I compiled wine-1.1.33 on my own, and installed it. Now I realized I made a mistake, and I miss my old wine version. So I tried to remove my current version with "apt-get remove wine". That did not work.

So, how do I remove wine after compiling it myself?

---

### Post by SPr on 2009-11-14
If you haven't got the directory you created when compiling Wine then download the version of the source have installed for wine. Extract it then
```

sudo apt-get checkinstall
cd /path/to/wine_source
make clean*
./configure
make
sudo checkinstall

```
checkinstall will create a .deb file which can be used to uninstall your version of Wine.

```

sudo dpkg -r wine.deb

```
or
```

sudo dpkg -p wine.deb

```
to remove.

I haven't used checkinstall for a few years so it may be a good idea to read about it first.

```

cd /to/wine_dir
./configure
make
sudo make uninstall

```
may also work.

* This could give an error but just ignore it. It's only of use if the files created from a previous compilation are present. Do not type the asterisk at the end of the line LOL

---

### Post by Lamez on 2009-11-14
I have tried this, but wine is still installed. I did 

wine --version

and it still returns a version number.


Not too sure, but this is really annoying.

---

### Post by Lamez on 2009-11-14
I solved it!

For those of whom are struggling from the same situation, here is what I did.

I currently have wine 1.1.33 installed, so I went to the wine archive, and downloaded wine 1.1.32.deb. (not the source, but a deb). Then I installed the deb file, over the newer installed one built from the source. Then I ran this: sudo apt-get remove wine

That did the trick! ;)

---


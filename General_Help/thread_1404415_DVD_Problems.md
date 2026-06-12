---
title: "DVD Problems"
date: 2010-02-11
forum: General Help
---

### Post by nothingface1 on 2010-02-11
I have been a long time Windows user and just recently switched to Ubuntu. At first it looked like everything was going great ... now I just seem to have lots of problems with stuff not working right or not working at all, there are lots of issues but first tings first. I can't seem to get any program to copy or burn any dvds or cds. I understand that you need certain codecs and css stuff which are already installed. Can anyone help??

---

### Post by kanikilu on 2010-02-11
Can you elaborate more on what you are trying to do? You don't need libdvdcss unless you are trying to do something with an encrypted/copy-protected DVD (e.g. a movie), and while it's certainly possible, is not included by default.

Are you trying to burn a data DVD? Watch a movie? Copy a movie? :confused:

---

### Post by nothingface1 on 2010-02-11
> **kanikilu said:**
> Can you elaborate more on what you are trying to do? You don't need libdvdcss unless you are trying to do something with an encrypted/copy-protected DVD (e.g. a movie), and while it's certainly possible, is not included by default.

Are you trying to burn a data DVD? Watch a movie? Copy a movie? :confused:

I want to copy, in Windows I used AnyDVD and Clone DVD, tried K9 copy but didn't work.

---

### Post by kanikilu on 2010-02-11
Can you **watch** the DVD in Ubuntu? If not, that would be the first step to solve before going any further...

You don't say what didn't work with k9copy, so I can't really help with that, but there are other programs, like DVD::RIP...heck, I'm pretty sure even DVDShrink works under Wine.

The first time I tried k9copy, I couldn't make heads or tails of it, but was able to get it to work after searching for a tutorial. I don't have the link handy, but just search for one, and see if anything useful comes up...

---

### Post by ushills on 2010-02-11
you need to sudo apt-get install libdvdread4, then sudo /usr/share/doc/libdvdread4/install-css.sh.  you  will then be able to read movies and use k9copy.

---

### Post by ghostborg on 2010-02-11
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

You need the underlying decrypting files in order to deal with protected movies.

First follow directions for adding the repository, where the files are located.
Then follow the directions for Playing Encrypted DVD's with the entire Medibuntu library.
Then the same for Non-free codecs.

---


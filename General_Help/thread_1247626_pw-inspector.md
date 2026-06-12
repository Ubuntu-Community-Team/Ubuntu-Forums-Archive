---
title: "pw-inspector"
date: 2009-08-23
forum: General Help
---

### Post by vu24hrs on 2009-08-23
I am rather new to ubuntu and I have a few text files I want to manipulate. I want to go through and remove all lines in a text file that are way too long and are less than a certain length. I have seen countless examples on the Internet showing something like this:

cat first.txt | pw-inspector -m 6 -M 128 > newfile.txt

I've seen where this is suppose to be basic linux use, but I can not get this to work at all on Ubuntu 9.04 (fully updated).

> bash: pw-inspector: command not found

any suggestions?

*I have two separate installs of Ubuntu 9.04 (both fully updated) that have the exact same problem or behaviour.

---

### Post by omgitsmit on 2009-10-01
> **vu24hrs said:**
> I am rather new to ubuntu and I have a few text files I want to manipulate. I want to go through and remove all lines in a text file that are way too long and are less than a certain length. I have seen countless examples on the Internet showing something like this:

cat first.txt | pw-inspector -m 6 -M 128 > newfile.txt



Let me break down what's happening here:

cat will list a file in terminal for you

| is a pipe, meaning you're piping the output from cat into something else

pw-inspector is a script, which you're piping the output from cat into

> is exporting everything into a txt file for you, so in the end you will have all your passwords sorted out.

**Answer**: You don't have the pw-inspector script installed. pw-inspector is part of the Hydra suite, if you install Hydra, you should get this simple script as well. Ubuntu doesn't have Hydra or pw-inspector in their repos (not surprised) but Hydra does come preinstalled with the Backtrack distro: [http://www.remote-exploit.org/backtrack.html](http://www.remote-exploit.org/backtrack.html)

If you have any further questions and need immediate help, jump onto OMGIRC or Freenode IRC chat (see my signature).

---

### Post by Kangarooo on 2010-12-02
Then where to find it? Where from to install it?

---


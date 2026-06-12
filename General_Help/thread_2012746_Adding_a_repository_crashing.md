---
title: "Adding a repository crashing"
date: 2012-06-29
forum: General Help
---

### Post by timetopat on 2012-06-29
I want to add a ppa but so far I cant.  
sudo add-apt-repository ppa:directhex/ppa 
brings an error where it cannot find a distribution template

Going to Synaptic-->settings->Repositories does nothing and then the os says that I should file a crash report

Going through the software center gives the same results

What should I do to add the ppa?

---

### Post by oldos2er on 2012-06-29
Which version of Ubuntu are you using? Looks like this PPA only has repos for Lucid and Precise.

---

### Post by timetopat on 2012-06-29
I am currently running 12.04 which I believe is precise.  
I followed a guide on [http://askubuntu.com/questions/81263/how-to-i-fix-software-center-after-installing-the-linux-mint-mate-desktop](http://askubuntu.com/questions/81263/how-to-i-fix-software-center-after-installing-the-linux-mint-mate-desktop)

And in the files i changed to 12.04 it said it i was on 12.10 quantum.
I am curious how it changed to those. I never remember touching those files.  Or doing anything that would.

---

### Post by oldos2er on 2012-06-30
If you're running Quantal, that would explain the ppa error. Can you run ```
lsb_release -a
``` and post the output here?

---


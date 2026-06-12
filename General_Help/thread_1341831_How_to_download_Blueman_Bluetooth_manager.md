---
title: "How to download Blueman Bluetooth manager"
date: 2009-11-30
forum: General Help
---

### Post by bmman on 2009-11-30
Can anyone tell me how to download Blueman 1.0 Free Bluetooth Manager for Ubuntu Linux on my Dell Inspiron 910? I had Bluetooth built into it, and have my cell phone set up and ready to go, but can't seem to get Blueman onto it (or a flash drive) to start using it. I live in Thailand and getting help locally is problematic. Any help, *in very simple terms, my computer skills are pretty minimal, especially with Linux*is greatly appreciated.
bmman

---

### Post by walmis on 2009-11-30
Which version of ubuntu are you running?

---

### Post by bmman on 2009-12-01
I'm running Ubunbtu 8.04

---

### Post by gradinaruvasile on 2009-12-01
Open a terminal (applications->accessories->terminal) and type:
sudo gedit /etc/apt/sources.list

Add to the end of the file this line:

deb [http://ppa.launchpad.net/blueman/ppa/ubuntu](http://ppa.launchpad.net/blueman/ppa/ubuntu) hardy main 

Save. Then:

sudo apt-get update && sudo apt-get dselect-upgrade
sudo apt-get install blueman

That should be it.

---

### Post by gradinaruvasile on 2009-12-01
Also i would advise to upgrade to a newer version (like 9.04). Has better drivers.

---

### Post by bmman on 2009-12-02
THANX!I'll follow up on both advices today.

---

### Post by bmman on 2009-12-05
Thanks for your earlier help. I thought I followed them to the letter, but still I'm not able to connect with Bluetooth. Once I added the line and clicked "Save", I wonder if this is where the problem was, as there was no notice of any kind that anything was saved. Checking the Synaptic Package Manager shows nothing there. Got any ideas where I'm screwing up?
bmman

---

### Post by bmman on 2009-12-05
Still having trouble downloading Blueman. Nothing shows up in the Synaptic Package Manager, I get the following Error report

E: Malformed line 15 in source list /etc/apt/sources.list (URI parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

What am I doing wrong??

---

### Post by Denny Johnson on 2009-12-06
Seems that either the suggestion you were given was not suitable for you or we didn't follow it correctly.
Have you opened the file again [step 1] and had a look?
When do you get the error msg?

gradinaruvasile.....I believe that we copied and pasted your line:
deb [http://ppa.launchpad.net/blueman/ppa/ubuntu](http://ppa.launchpad.net/blueman/ppa/ubuntu) hardy main 
at the end of the sources list, is that correct?

---

### Post by bmman on 2009-12-06
> **Denny Johnson said:**
> Seems that either the suggestion you were given was not suitable for you or we didn't follow it correctly.
Have you opened the file again [step 1] and had a look?
When do you get the error msg?

gradinaruvasile.....I believe that we copied and pasted your line:
deb [http://ppa.launchpad.net/blueman/ppa/ubuntu](http://ppa.launchpad.net/blueman/ppa/ubuntu) hardy main 
at the end of the sources list, is that correct?

Yes, correct. Later, I went back and tried it a different way (can't recall exactly how, now) and then checked the Synaptic file, still no Blueman but now the error. So now I appear to have 2 problems (1) reverse the error, (2) start over with Blueman and get it to Save.

---


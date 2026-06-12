---
title: "Where is Synaptics?"
date: 2006-02-03
forum: General Help
---

### Post by Mau on 2006-02-03
Hello everyone.
I'm new to the Linux community, and I have been trying to convert for a long time now, but I could never get my wireless support to work.  Kubuntu seems to have fixed that!

I cannot seem to find Synaptics (I believe that's what it's called). Where is it?  I want to download programs, but I don't believe that I can without this program (correct me if I'm wrong).

Thanks, everyone.

---

### Post by aysiu on 2006-02-03
Kubuntu uses Adept instead of Synaptic Package Manager, but you can easily install Synaptic, too: ```
sudo apt-get update
sudo apt-get install synaptic
```

---

### Post by Mau on 2006-02-03
[QUOTE=aysiu]Kubuntu uses Adept instead of Synaptic Package Manager, but you can easily install Synaptic, too: ```
sudo apt-get update
sudo apt-get install synaptic
```[/QUOTE]

Ah!  That would explain it.  Where can I find Adept then?

---

### Post by FlakJacket on 2006-02-03
Click on your application menu > System > Package Manager (adept).  You will have to enter your user (not root) password to get into adept. Then either scroll down to synaptic (the packages are in alphabetical order) or use the quick search filter to find it.  Then click on the synaptic item click the install button in the dropdown and click the checkmark button that says  commit changes.  You may want to run system updater in the System menu if you haven't already before installing synaptic.

If you'd like you can also type in the commands in the other user's post into Konsole it works just as well.

Hope that helps I'm pretty new to this myself.

Flak

---

### Post by Mau on 2006-02-04
I see.  I was looking for something that started with A, and I guess I was blinded by anything else. Thanks for the help guys. :)

---

### Post by chiisu on 2006-02-04
Install synaptic anyways, I can't stand using Adept  ;)

---

### Post by FlakJacket on 2006-02-05
Any time.

Chiisu what's wrong with adept? I've never tried Synaptic.

Flak

---

### Post by Mau on 2006-02-05
Adept seems to crash about 50% after it's done committing the changes.  The changes are still in effect -- all it means that is that I need to retype my password.

---


---
title: "Update Manager error"
date: 2011-11-09
forum: General Help
---

### Post by rapattack1 on 2011-11-09
This is the second time the update manager told me this this week. Not sure what it means. When i close this it updates ....anyway this is the second time this error has happened so if you can tell me what i should do i would appreciate the advice :0)

---

### Post by mörgæs on 2011-11-09
The dialog box mentions Intrepid. Which release are you using?

---

### Post by rapattack1 on 2011-11-09
I use a Distro called ArtistX

---

### Post by Old_Grey_Wolf on 2011-11-09
Enter these commands in a terminal ```

gpg --keyserver keyserver.ubuntu.com --recv 54422A4B98AB5139

gpg --export --armor 54422A4B98AB5139 | sudo apt-key add -
```
Then update and upgrade again.

---

### Post by rapattack1 on 2011-11-12
Hi things seemed to go well. How do i know for sure it worked? Thanks so much :0)

---

### Post by mörgæs on 2011-11-13
If you can download updates, it works.

I don't know ArtistX, but if it parallells Ubuntu, you are using a very old release (Intrepid = 8.10). Have you thought of a new installation?

---

### Post by rapattack1 on 2011-11-13
Hi as far as i have the lastest Artistx. I just looked at their website and the last release was in july. It was after that i downloaded and installed it.

I just did an update and upgrade via the terminal. There was nothing to upgrade.

---

### Post by Old_Grey_Wolf on 2011-11-14
> **mörgæs said:**
> If you can download updates, it works.

I don't know ArtistX, but if it parallells Ubuntu, you are using a very old release (Intrepid = 8.10). Have you thought of a new installation?

It looks like virtualbox for Intrepid was downloaded from the virtualbox.org website. It doesn't mean that the virsion of Ubuntu being run is Intrepid. 

rapattack1, if you use virtualbox, I would at least download the version of virtualbox that is suggested for the Ubuntu release that is being used. Virtualbox may not be offering updates for it anymore. I know you can't download the Intrepid version of virtualbox anymore.

---

### Post by rapattack1 on 2011-11-15
Hi i don't know what virtual box is

---


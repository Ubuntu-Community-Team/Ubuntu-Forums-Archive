---
title: "Can't install anything."
date: 2010-12-04
forum: General Help
---

### Post by Anonymous Rain on 2010-12-04
Every time I try to instal something from the software centre, I get this error. Can anyone help?
[IMG]https://dl.dropbox.com/u/5844105/Photos/Screenshot%20%281%29.png

---

### Post by matt_symes on 2010-12-04
Hi

Open a terminal and type

sudo apt-get install -f

enter your password. Nothing will be echoed on the screen. This is normal.

then type

sudo apt-get update
sudo apt-get upgrade

Does that fix it?

Kind regards

---

### Post by Anonymous Rain on 2010-12-04
Unfortunatley no, I keep getting this error when trying to do apt-get stuff;

"E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. "

---

### Post by Anonymous Rain on 2010-12-04
Ok here's another problem. I just did dpkg configure, and it let me do apt-get stuff, but then I get a message in the terminal saying "Configuring ttf-mscorefonts-installer", with "<ok>" at the bottom, but the "<ok>" can't be clicked, so I'm stuck.

---

### Post by matt_symes on 2010-12-04
Hi

I not 100% sure what you mean. Is the <ok> in the terminal?

If it is, try using the tab key to select <ok> and then hit enter.

Kind regards

---

### Post by drpjkurian on 2010-12-05
Hi 
What i presume is that the 'ok' which is displayed in the terminal window indicates that the system has configured the ttf mscorefonts installer successfully..

---

### Post by Anonymous Rain on 2010-12-05
Nope, because that's what I thought. But when I exit the terminal it says I'm killing the proccess, so obviously it wants me to confirm something.

---

### Post by Anonymous Rain on 2010-12-05
> **matt_symes said:**
> Hi

I not 100% sure what you mean. Is the <ok> in the terminal?

If it is, try using the tab key to select <ok> and then hit enter.

Kind regards

*facepalm*

This seems to have fixed everything... Thanks...

---


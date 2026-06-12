---
title: "Removed packages, can't boot up."
date: 2012-01-31
forum: General Help
---

### Post by redeigth on 2012-01-31
Hi. I am new here but have been using Ubunutu for about 3 years.

On Saturday I removed some packages (from my other computer) using Synaptic Package manager.When I booted on Sunday I only got to the Ubuntu screen and a white terminal window appeared in the top left corner.
I cant work out how to boot to the GUI.

Please help me get back up and running - at the moment I am stuck with a Win7 machine that keeps dying on me !

---

### Post by FormatSeize on 2012-01-31
Do you know exactly what packages you removed? It seems as if somehow you deleted your desktop environment along with it.

---

### Post by redeigth on 2012-01-31
Not really. I have had 10.04 running since April 2010 and was doing a clean up of all sorts of stuff that I hadn't used for a long time.

---

### Post by redeigth on 2012-01-31
OK, second question. If I install 11.10 (or 12.04) over 10.04 is there any chance of losing files ?
I know I should backup but I don't have the storage at the moment.

---

### Post by redeigth on 2012-01-31
OK, I fixed it with help from here :

 [http://tolearnfree.blogspot.com/2009/10/how-to-install-gui-desktop-environment.html](http://tolearnfree.blogspot.com/2009/10/how-to-install-gui-desktop-environment.html)

I just had to plug into the Internet (no wifi access without booting up).

Then I put [sudo apt-get install ubuntu-desktop]  into the terminal,put in my password and the packages that I had accidentally removed were reinstalled .

Restart and back to normal.

Phew ! Thank God Ubuntu makes sense.

Thanks for your input FormatSeize, it was your post that sent me looking for a desktop environment.

---


---
title: "lightDM problems"
date: 2011-10-14
forum: General Help
---

### Post by goneskiing on 2011-10-14
1) I get a black background which conflicts with the menu - tried making changes to the conf file but no success - maybe I'm using the wrong conf file ?   

2) where is the shutdown button on lightdm ?  All I see are session types.  

3) how do you get rid of user list ?

---

### Post by goneskiing on 2011-10-15
> **goneskiing said:**
> 1) I get a black background which conflicts with the menu - tried making changes to the conf file but no success - maybe I'm using the wrong conf file ?   

2) where is the shutdown button on lightdm ?  All I see are session types.  

3) how do you get rid of user list ?


fixed #1 which fixed #2 - needed to change lightdm.conf not to point to unity but to light-gtk-greeter 

still do not know how to get rid of users (#3).

---

### Post by Jose Catre-Vandis on 2011-10-17
In similar vein, gdm allowed a .face image in the home directory, lightdm just gives an image of a PC screen. I tried .face on its own and editing the .conf file to include logo=/home/user/.face but this didn't work (its not there by default.

---


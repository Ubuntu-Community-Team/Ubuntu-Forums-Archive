---
title: "dash home icon missing"
date: 2012-09-03
forum: General Help
---

### Post by lestat6205 on 2012-09-03
I installed edubuntu and then I decided to uninstall because it changed the look of everything. Everything is back to normal now except the dash icon has a question mark any ideas are welcome.

Thank you in advance and I did try the search and I came up with nothing.

---

### Post by jerome1232 on 2012-09-07
I to have this probelm! I figured out a solution.

On a computer that wasn't affected I created a tar of /usr/share/unity which I discovered is where the icons are stored, I transfered that tar to my desktop and extracted it over my desktops version with this command: (assuming you placed it in your home folder and you just open a terminal)

```
sudo tar xvf unity.tar.gz -C /usr/share/unity/
```I have attached the tar I used here, best of luck! Now I'm trying to figure out how to fix my greeter logo to be Ubuntu instead of edubuntu, and my grub splash as well. 


Curse you Edubuntu! There needs to be an easy way to revert permanent theme changes like that imo.

---


---
title: "Different permissions for UI and terminal"
date: 2012-08-27
forum: General Help
---

### Post by niranjan_rao on 2012-08-27
Brand new install of 12.04. I created my defautl login, immediately joined with active directory for *another* login which I use for my day to day work using centrifydc. I have also granted sudo rights to my active directory login.

I am now logged in with my active directory login.

What I am seeing is commands that need sudo rights are behaving differently. If I run for example

sudo apt-get update 

in a terminal, it asks for my password. I provide my active directory password and it works fine. If I use any GUI tool that needs sudo rights (e.g. add printer, synaptic, extra drivers etc), it asks me for the password, but does not accept my active directory password. I have to enter the password for default login I created. 

Why is there such a discrepancy? Both mechanisms should either accept or reject same password. I dont get to choose login name in either case.

---


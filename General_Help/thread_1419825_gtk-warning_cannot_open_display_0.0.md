---
title: "gtk-warning cannot open display: 0.0"
date: 2010-03-02
forum: General Help
---

### Post by Jamesdavy on 2010-03-02
Hello,

I've tried searching the forums for a solution to my issue. I've found several different posts with the same problem. Even ones that managed to find a solution. Unfortunatly, I'm a beginer in Linux and didn't understand the solutions suggested. 

I was hoping for more detailed help.

I've installed the latest version of ubuntu server (9.10) as a virtual machine to test a website and database setup. 

I am in the proccess of learning linux as the test setup evolves. 

I was hoping to be able to use firefox on this test setup to brows forums and download tools and packages for the software I'm working with.

installed firfox with apt-get, no problem.

but when I run it I got the error "gtk-warning cannot open display: 0.0"

originally it simply said "gtk-warning cannot open display"
(without 0.0)

During my troubleshooting I ran the command "export DISPLAY=0.0" 
it didn't help me any

I installed xorg as well, on a recommendation in a forum somewhere. 
Also didn't help.

I see people reffering to an 'X' of some kind in relation to something that could be the solution I'm looking for.

I don't know what 'x' is and was hoping someone could elaborate in as much detail as possible. (I've never used linux)

Thanks for any help you can provide.

---

### Post by Barriehie on 2010-03-07
FF runs as a GUI so you'll need a GUI environment, which by default isn't installed on the servers I'm pretty sure.  Try running FF again AFTER installing ubuntu-desktop.

HTH

---


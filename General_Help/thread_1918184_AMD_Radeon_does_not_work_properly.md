---
title: "AMD Radeon does not work properly"
date: 2012-01-31
forum: General Help
---

### Post by lucr on 2012-01-31
I been having some problems with my graphic card for a time now. But I had enough when I did'nt get Oil Rush to work on my HP Pavilion g6. The system has suggested hardware drivers for me, but the first time I installed them they pretty much ****** up the graphics. After some time I managed to get the computere to work properly (I thought) again. When the game did'nt work I tried to the hardware drivers for the graphic card anyway. First of all there was to possible choices insted of one, as the last time I installed the drivers (when it did'nt work out so good). The choices are:

1. ATI/AMDs proprietary video drivers FGLRX (update for edition)

and

2. Proprietary FGLRX-video drivers for ATI/AMD

I realized the drivers probebly are pretty much the same, so I tried the first one. But this did'nt work. Instead I was asked to "Look in to /usr/var/log/jockey.log". This did'nt helped me much. Instead I choiced the other one, wich was installed and after reboot there where some changes. First of all there was a lot more details for Unity that was'nt there before and some shortkeys are now working that did'nt before (like Ctrl + T and the Prt Sc-button). But overall everything doesn't work as it used to. Like when you browse between the workspaces it doesn't look the same. To get to the point: 
  it doesn't work well right now even if I got some things better and now will not Oil Rush (as I mentioned in the beginning) even start.

SO! Can someone give me any advice with this? I'm stuck. Can't manage to see whats wrong right now. Any help? My graphic card is AMD Radeon HD 6470M.

---

### Post by sunfromhere on 2012-01-31
Hi.

Can you please post output of aticonfig --lsa (if you have installed proprietary drivers).

The thing is: I have a pavilion g7, and they come with a switchable graphics, which doesn't work in Linux, unless you flash your BIOS with the newest upgrade so you can change the graphics card being used, which you cannot do unless you have Windows 7.

I too have been thinking that my graphics is AMD Radeon HD 6470M, while in fact the one being used was Mobility Radeon 4200 Series. I have been in contact with hp support, they apologized from here to Jupiter, but the switch cannot be done without Win7.

---

### Post by lucr on 2012-01-31
Right now I'm in a process trying to make it work with a suggestion from here: [http://askubuntu.com/questions/100255/how-do-i-get-my-graphic-card-to-work-properly](http://askubuntu.com/questions/100255/how-do-i-get-my-graphic-card-to-work-properly). So it's not installed right know, but I will post the outpot of aticonfig --lsa if this doesn't work out.

---


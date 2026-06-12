---
title: "Windows inside linux Virtualization--Help"
date: 2009-10-03
forum: General Help
---

### Post by jayeshbhat55 on 2009-10-03
[FONT=&quot]I am new user of ubuntu and would like to use windows inside linux using some worthwhile VT tools like virtualbox or Vmware. The problem is that my processor is core 2 duo T6500 and from its updated specifications it doesn’t support hardware virtualization!. Does that mean I cannot use VT at all ??. In some website its said that without hardware VT, 64bit OSs cannot be virtual guests, does that mean I have 32 bit OS guests. I plan to use ubuntu 9.04 64 bit ( jaunty jackalope) and any windows OS (XP or more; 32 bit or 64 bit plz guide)..[/FONT]
[FONT=&quot]
[/FONT]    Any help is appreciated

---

### Post by urugTON on 2009-10-03
First, relax!  You sound worried.

You're fine.  I run VirtualBox and VMware Server on systems without virtualization hardware including a Core Duo laptop.

Start with [http://ubuntuforums.org/showthread.php?t=973756](http://ubuntuforums.org/showthread.php?t=973756) to get a feel for things.

My advice after your reading is to try VirtualBox.  I have the closed source version from Sun.  There is an OSE version available in the Ubuntu repositories.  There are valid philosophical reasons for sticking with the OSE version.  I wanted the latest version when it came out, so I guiltily grabbed it from the Sun website.:redface:

I have been very happy with VirtualBox.  It has been reliable and easy to use.  It's a good place to start.  I have been less pleased with VMware Server although 2.0 has worked far better for me than any of the 1.x versions.

FWIW, I have Windows 7 running in VBox on a laptop with a lot less firepower than your system.  I also have legit OSes like CentoOS running in VBox on that laptop.  

I am also starting to use KVM on an Intel Quad 6600 system.  That is not a place to start your virtualization journey.  

Enjoy the trip.

---

### Post by misfitpierce on 2009-10-03
Also so you know... There is NO need to make MULTIPLE threads for the same problem... Maybe every few hours put a post in it that says BUMP FOR HELP but don't do it every hour or under and spam boards up. Just saw you posted this thread name multiple times. No need to do this and please refrain from doing so in future. Thanks.

On side note, welcome to the boards.

---

### Post by jayeshbhat55 on 2009-10-07
@ urugTON
Thank you very much for link man. I did help a lot! I installed Virtualbox amd64 OSE with WIN7 beta as my VM. Its been quite a great experience. The VM performs well to my needs. :). I believe with VT-x enabled, performance mayb even better. Isnt it?

@misfitpierce  
Wat can i say? I was desperate and wanted a soln as soon as possible. Thanks to the GREAT online support, got my question resolved within hours.:) I can assure you that I wont repeat it.

---


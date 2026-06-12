---
title: "breezy n netstation 100 problems"
date: 2006-06-01
forum: General Help
---

### Post by charlesw on 2006-06-01
not sure where this should go but here it is :) 

this will be long ](*,) 

im using breezy 5.10 trying to follow along with the netstation how to's at various places online.

ive setup nfs and xdmcp my netstation downloads it kernel fine then loads its built in chooser showing a windows that says: 

Default Hosts

ubuntu  TCP - Linux 2.6.12-9-386 

then if i click on ubuntu it will say ubuntu in a Host: box next to that we have NET with the tcp option selected and Type: Host or Indirect 

now when i click ok with host selected it says there are 1 running programs and 0 remote programs close window it dosent matter if i click yes or no this option does nothing but make the chooser (the nestations chooser) go away and i have to reboot it.

however if i choose the Indirect option the chooser goes away and a vertical rectangular box pops up on the screen with no text on it and it has what appears to be a text entry box on the bottom.. this box displays on the screen for about 1 second before it reloads shows for 1 second then goes back to the ibm's chooser window. 

now im not sure if i have misconfigured xdmcp gdm or nfs or something else im  not even aware of. 

but if i click the messages box on the netstations (it has a built in X display) 
it shows some errors :

asking host "ubuntu" for XDMCP session
TCP session started on host "ubuntu"
host "192.168.0.1" connected with MIT-MAGIC-COOKIE-1 authorization
client attempted to use non-existent extension "XKEYBOARD"
client attempted to use non-existent extension "XINERAMA"
client attempted to use non-existent extension "XFIXES"
client attempted to use non-existent extension "XKEYBOARD"
shutting down
connection closed by X server 

i dont know if that means ubuntus X or the netstations X 
and i dont know where to go from here if anyone can help i would appreciate it

---


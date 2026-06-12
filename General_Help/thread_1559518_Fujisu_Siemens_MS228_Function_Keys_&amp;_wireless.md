---
title: "Fujisu Siemens MS228 Function Keys &amp; wireless"
date: 2010-08-23
forum: General Help
---

### Post by leehamer on 2010-08-23
Afternoon guys, 

I have been using Ubuntu quite happily on my desktop PC and have finally  convinced my gf to allow me to put 10.04 on her laptop instead of  vista. All seems to be going well at the moment, however there are a  couple of issues I need to resolve before she will accept it as  working.. 

1) I cant get the function keys to work and I have searched to no avail
2) The wireless is not enabled on boot, you need to use a function key.  However I have found a short script to get it enabled in terminal which  is:

     Quote:
                                                 sudo modprobe -rv ath5k
sudo modprobe acer-wmi
sudo modprobe -v ath5k                                 
I have read there is a way to get this to run at boot by editing the rc.local

Can anyone help me out with this?

Many thanks for your help in advance

---

### Post by leehamer on 2010-08-24
Its alright I solved the wireless function, cant be bothered with the other function keys as they aint needed

---


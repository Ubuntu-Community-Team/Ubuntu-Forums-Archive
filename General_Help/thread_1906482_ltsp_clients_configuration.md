---
title: "ltsp clients configuration"
date: 2012-01-09
forum: General Help
---

### Post by samurai76 on 2012-01-09
Hi my name's Samuele from Italy. Sorry for my English...I nee help!
I'm working to do a new computer lab for a primary school. I use ubuntu 10.04 64bit with ltsp protocol on the server. There are 15 clients(11 pentium III and 4 pentium IV). This is the problem: when I login with PIII I haven't any problem while with PIV's I login only with first user that I created in the server. I can't login with the other users. If I login with another user PIV try to login, I see the Ubuntu desktop and login sound but after 2 seconds PIV return to the login window.
 
Any solutions?
 
This is my lts.conf configuration:
 
[default]
LDM_DIRECTX=True
X_COLOR_DEPTH=16
LOCALDEV=True
SOUND=True
NBD_SWAP=True
SYSLOG_HOST=server
XKBLAYOUT=de
 
[00:0:B7:20:AB:1B]
XSERVER = vesa
[00:50:04:65:D7]
XSERVER = vesa
[00:50:04:0B:51:45]
XSERVER = vesa
[00:50:04:BB:070]
XSERVER = vesa
[00:01:02:B0:27:E7]
XSERVER = vesa
[00:13:21:06:89:FD]
XSERVER = vesa
 
#[00:13:21:06:A7:E3]
# XSERVER = vesa
# NBD_SWAP= False 
 
#[00:14:C2:03:4E:20]
# XSERVER = vesa
# NBD_SWAP= False 
 
#[00:13:21:06:A8:1B]
# XSERVER = vesa
# NBD_SWAP= False 
 
#[00:13:21:06:A7:17]
# XSERVER = vesa
# NBD_SWAP= False 
 
The last 4 macaddress are PIV(the others are PIII with integrated video card) but with this configuration(if I remove comment #) the login windows is black and I can't login with any users!
 
The PIV's integrated video card is INTEL®82915G/GV/910GL EXPRESS CHIPSET FAMILY
 
Thank you for your responses.

---


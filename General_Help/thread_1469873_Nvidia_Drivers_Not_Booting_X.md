---
title: "Nvidia Drivers Not Booting X"
date: 2010-05-02
forum: General Help
---

### Post by Dr_Krullivan on 2010-05-02
I'm running ubuntu 64x and I have just re-installed, here's my problem.

1. Installed nvidia drivers on other installation and it just brings me to a terminal that tells me to login and I manually need to start x from there

2. Yes, this happens with the current and older drivers provided by ubuntu via the restricted drivers application

3. I know I must not be the only one, as many people use nvidia cards.. 

Any solutions to this problem?

---

### Post by Dr_Krullivan on 2010-05-02
Bump? 

Anyone care to help a new user here :'(

---

### Post by dino99 on 2010-05-02
lucid ?

which driver installed ? recognized ? (system admin hardware driver)

only ubuntu genuine repo ? (into synaptic repo)

which card ? (into console: lshw)

---

### Post by Dr_Krullivan on 2010-05-02
Yes ubuntu 10.04 lucid. 

I tryed the current driver and the 100 something driver that ubuntu provided via the restricted drivers application

description: VGA compatible controller
          product: C61 [GeForce 6150SE nForce 430]

I'm currently going to try the 195 drivers that are on the nvidia website for 64x

---

### Post by dino99 on 2010-05-02
so its an nvidia card

do the following step by step into console:

sudo rm -f /etc/X11/xorg.conf

goto synaptic (system admin synaptic), 
if not installed: sudo apt-get install synaptic
and: 
remove/purge each nvidia packages installed, then
install: nvidia-current, nvidia-current-modaliases, nvidia-common, nvidia-settings

sudo dpkg-reconfigure jockey
sudo dpkg --configure -a
sudo apt-get install -f

reboot

---

### Post by Dr_Krullivan on 2010-05-02
Doing right now, will post results when I reboot.. hopefully X will work! 

Thank you for responding to my thread, I greatly appreciate it.

---

### Post by dino99 on 2010-05-02
hey, i remember the time when i was asking for every thing too :P

---

### Post by Dr_Krullivan on 2010-05-06
Hello, I am sorry I was gone for a while.. I had a few network issues at home. I am now going to try your solution, cheers!

---

### Post by Dr_Krullivan on 2010-05-09
No luck with your way, think of any other solutions?

---

### Post by Dr_Krullivan on 2010-05-09
Anyone?

---


---
title: "firewall"
date: 2009-07-25
forum: General Help
---

### Post by loosescrew on 2009-07-25
Hello,I'm new to ubuntu. I would like to know of a good firewall for ubuntu ? I have heard that you do not need an anti-virus, but I assume that you definitely need a firewall. Thanks Joe

---

### Post by masterkoppa on 2009-07-25
No matter what you have in a computer, if its going to be on a network a firewall is allways a good idea. You could try out Firestarter or Guardog. You might also find these usefull: [https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw](https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw) [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

---

### Post by loosescrew on 2009-07-25
Thanks masterkoppa. I appreciate the reply. I will investigate farther. Joe

---

### Post by wojox on 2009-07-25
UFW is installed by default you just need to turn it on. Here's the doc's for it:

[https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw](https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw)

---

### Post by jmszr on 2009-07-25
loosescrew,

To get a GUI for the ufw firewall configuration tool for the iptables firewall, go to System > Administration > Synaptic Package Manager > Search > gufw > right slick on gufw > click on "Mark for Installation > click on Apply.       
 
It will be under System > Administration when installed.

Edit: Edited to reflect jerome1232's post

---

### Post by dlmarti on 2009-07-25
I use firestarter, I'm very pleased with it.

Its kinda like the firewall for dummies, and while I have written firewall rules by hand before, I'm very pleased with firestarter.

---

### Post by loosescrew on 2009-07-26
Thanks,everyone. I appreciate all the input. Joe

---

### Post by jerome1232 on 2009-07-26
I just thought it would be beneficial for you to know that all of these programs are actually not the firewall, they are just configuration front ends to the built in firewall called iptables.

---


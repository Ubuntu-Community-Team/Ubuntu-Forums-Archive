---
title: "Does Gammu support Nokia 3110 ?"
date: 2010-05-26
forum: General Help
---

### Post by monetteski on 2010-05-26
I am using windows environment at the same time  I installed Sun Virutal Box so I could install Ubuntu on my laptop.  It was successful and installed gammu as instructed in one of the sites i saw.  When I tried to connect my nokia 3110 on my laptop using USB cable and executed "lsusb" command it says the following:

Bus 002 Device 001:ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001:ID 1d6b:0002 Linux Foundation 2.0 root hub

What does it mean?  I only have 3 USB port and nothing was connected except my nokia.

Then i tried executing gammu --identify with configuration of port = /dev/ttyUSB0 and connection = dku2 and the result was:

Error during reading from the device

CAn someone please help me find out the right configuration and what does the error message means?  I am having same problem with Gnokii so I decided to shift to Gammu but still it didnt work out.  I tried to attached the USB cable and my phone on windows environment and its working fine (this is just to test if there is a problem on my phone and cable).  So i think there is no problem with my phone and cable so what could be the problem?

Thank you for whatever help you can extend me.  I really need your support!

---

### Post by alexfish on 2010-05-26
hi

Installing Wammu , a front end to Gammu will give better control of what your doing

as for nokia support I would recommend looking here.

[http://wammu.eu/gammu/](http://wammu.eu/gammu/)
[http://wammu.eu/support/](http://wammu.eu/support/)

also have a look through the man pages , there pretty loooong, making a copy in the home directory then using something like open office makes for easier reading.

Code:

man gammu

man wammu 

regards 
alexfish

---

### Post by monetteski on 2010-05-26
Hi, Thank you for your kind help.  I will try Wammu.  But can I ask again some question?  Can Wammu be connected to a database like MySQL? Because I want to make some program that will automatically send information to my mobile once the mobile phone send message to my laptop.  Will it still be possible? 

Thank you so much!

---

### Post by alexfish on 2010-05-27
hi

under wammu data can be saved as backups 

Save , Save Messages , Import , Export ,Export Messages to Emails ,Export Messages to XML

hope this helps

regards

alexfish

---

### Post by monetteski on 2010-05-27
Hi, Thank you for that wonderful information.  But Like Gnocky, it has the same process can save, store messages, import and export but it can be done manually by the user.  What I want is that If i will send message from my mobile to my laptop, there is an interface that will automatically search that message to my database and if the message or text was found, it will automatically retrieve the information and send it back to my mobile. is this possible?

Thank you again for not getting tired of answering my queries.

---

### Post by alexfish on 2010-05-27
Hi

don,t Know if that is possible with wammu

is it possible with gammu ? , yiu are using it 

the only other way would be to write a script to access the modem directly, but that is beyond this post

there is a program called modem-cmd it is run from the command line
it will access the modem with AT Commands , so you could write a script that would loop for ever and then act on the new messages received, if you can script , start scripting .

for a few tips on how to access the modem can be found here

[How To : Mobile Broadband Connections [ Ubuntu  10.04 : 9.10 : 9.04 ]]("http://ubuntuforums.org/showthread.php?t=1466490")

 read all , including the links etc 

regards
alexfish

---

### Post by monetteski on 2010-05-28
Hi again.  Thank you for that information. It is really very useful especially if it concerns broadband.  I forgot to tell you that I am focusing on sending sms without the use of internet.  That means I would either use sms gateway or just USB cable to communicate my laptop with my nokia.

Thank you again for bearing with me.

---

### Post by alexfish on 2010-05-28
hi

just been looking through the man pages of gammu

nothing stopping writing a script to use gammu and using its functions

---

### Post by monetteski on 2010-05-30
Hi again... I am so happy that finally Gnokii was able to recognized my nokia 3110 classic and identify as well.  But Gammu can't.  I don't know why.  But want to ask the following questions:

1. I am here in Japan and my mobile phone does not recognize the network here in Japan.  So do you think its the reason why i can't send message using Gnokii? The error message says "Aborted core dumped".  I thought using USB cable even without the signal can still receive messages.  The signal I was referring to was the Telecommunication signal or the SMS center.

2. Does gnokii has the capability to recognize not only the device but also the mobile number?

Thank you for whatever help you can give me...

---

### Post by pkot on 2010-07-10
Ad 1. You cannot send SMS when the phone is not registered in any network. How do you imagine it could work? As for the core dump problem it is fixed in gnokii 0.6.29

Ad 2. You mean own number? Yes, but only if your phone provides this information. As far as I remember gnome-phone-manager takes advantage of this feature. Sorry, can't remember the command at the moment.

---


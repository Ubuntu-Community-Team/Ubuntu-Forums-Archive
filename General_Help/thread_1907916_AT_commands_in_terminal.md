---
title: "AT commands in terminal"
date: 2012-01-12
forum: General Help
---

### Post by donpeter06 on 2012-01-12
Hi
I am currently working on a project and i need to interface with a gprs modem. And i know i can control ( read and send sms ) with AT commands. I have used an application called gammu.
But i need to be  more flexible in carrying out the operations.
So i would appreciate someone to help me in guiding me on how to use or execute AT commands from our linux terminal(ubuntu).
Thanx.

---

### Post by ernied on 2012-01-12
Try using the minicom package. It works well as a serial port interface not only to modems and GPRS devices, but to Cisco routers and other networking devices that use a serial port.

---

### Post by donpeter06 on 2012-01-13
so there is option our linux terminal is supporting AT commands in a native manner atleast!!!
oke
Please tell me is or would you give a link to the perfect guide into making a .sh file

---

### Post by matogrosso on 2012-03-07
Donpeter06,

What exactly do you intend to do ?

I have written a few scripts for sending AT commnands. They are for remotely controlling handsets so that I can send SMS, make and terminate voice calls using AT commands. They may be useful to you.

It has been submitted as a post and should be available in this forum soon.

Thanks

---

### Post by donpeter06 on 2012-03-07
I was fed up with the terminal not supporting gsm modems directly
then i started using gammu.
Now i started studying python and its an amazing language. and i am now able to perfectly control the gsm modem with it.

---

### Post by matogrosso on 2012-03-08
Thank you, Donpeter06.

Please let me know more about gammu. What is it ? And I would like to have a look at the python scripts you have as they might be useful to me.

You can find my python scripts here:

[http://linux-101.org/script/python-code-sending-sms-messages-usb-connected-mobile-phone]("http://linux-101.org/script/python-code-sending-sms-messages-usb-connected-mobile-phone")

They allow you to make calls and send SMS from a Nokia phone controlled by the python scripts porsted. If you have anything else on that line (e.g. web browsing) in that kind of scenario I would be very thankful.

Kind Regards,
Matogrosso

---

### Post by donpeter06 on 2012-03-08
i am sorry that all that i did in my script was to sent and recieve sms data.
I was part of my project and am happy that python came to my aid.
If i am getting time to code more on browsing and etc .I will be happy to post the script over here.
thanx

---

### Post by srknthmk on 2013-04-12
hi friends,i have to send AT commands to the Bluetooth module AUBTM-20 through minicom terminal in ubuntu trough serial port. I had succeeded in sending AT commands through hyper terminal in windows xp. please help methank you

---


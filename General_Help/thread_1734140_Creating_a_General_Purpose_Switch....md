---
title: "Creating a General Purpose Switch..."
date: 2011-04-19
forum: General Help
---

### Post by jspecht on 2011-04-19
Hello,

I want to create a general switch that I can use to send a signal to my ubuntu server when it is activated/deactivated. Here's an example: I want to know when a certain door is open, so I can have a switch closed when the door is closed and opened when the door is opened. When opened or closed, the computer will receive a signal and I can have some software intercept this signal and process it to my liking (i.e. ring a bell/text message me/email me/etc).

I know I will have to create a simple driver, software to make use of this signal, etc... I am willing to do whatever it takes to make it happen. I'm just wondering if anyone can point me in the right direction as far as which interface I should use to communicate with my server (i.e. usb, serial), which references I should read, and any personal experience you have with something like this...

Please let me know if you want me to clarify something.

P.S. Here is a simple diagram of what I want (S=the switch, I=the interface to the computer): [http://img.photobucket.com/albums/v205/jspechts/comp_switch.png](http://img.photobucket.com/albums/v205/jspechts/comp_switch.png)

---

### Post by An Sanct on 2011-04-20
Welcome to the forums!

There are a lot of circuits on the internet, that make you computer manage "open" and "closed" doors. 
To get a feel, try searching for the terms "pc", "relay", "circuit" and "controller". This should bring a lot of rs232, serial and parallel solutions, choose the best for you, given, that you have a port like that. ;)

PS. [a simple version]("http://www.rentron.com/pc-relay.htm"), [a more complex - 8 channel relay station]("http://freeelectricalsandtools.blogspot.com/2009/12/8-channel-lpt-relay-circuit.html").

---

### Post by dragonfly41 on 2011-04-20
depending on how complex your final application is .. you can experiment with an academic licence of NI LabView

[http://www.ni.com/data_logger/whatis.htm](http://www.ni.com/data_logger/whatis.htm)

but for a simple application (as you write) this might be overkill

---

### Post by jspecht on 2011-04-20
Thanks for the quick responses! I will read your guys' resources and let you know what happens. I really appreciate it.

---


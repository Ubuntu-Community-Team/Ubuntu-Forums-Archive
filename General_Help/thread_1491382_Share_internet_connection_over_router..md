---
title: "Share internet connection over router."
date: 2010-05-23
forum: General Help
---

### Post by metaltroubador on 2010-05-23
I have a mobile broadband usb modem that I get my internet connection from, and I would like to share this connection through a router that is connected to the same computer via ethernet. I'm running Ubuntu 9.10.  Any help would be appreciated.

---

### Post by jamesisin on 2010-05-23
This should give you a good start:

[http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

---

### Post by metaltroubador on 2010-05-23
I'm following those steps, but I've run into a problem.  That thread seems to be dead now though.  When I use 

# apt-get install ipmasq

It says that the package has no installation file or that it doesn't exist.

---

### Post by jamesisin on 2010-05-23
Yeah, my 8.10 system has it (in Synaptic) and my 9.10 system does not.  Must have been dropped from the repos.

These instructions should help you get around that:

[http://ubuntuforums.org/showthread.php?t=1309218](http://ubuntuforums.org/showthread.php?t=1309218)

---

### Post by Miljet on 2010-05-23
Maybe I am not understanding what you want to do, but the most common configuration is to connect the USB modem to the input of the router and connect the outputs of the router to whatever computers you want to connect. In other words disconnect the cable coming from the modem from the computer and instead plug it into the input jack on the router. Then either use cables to connect the outputs of the router to multiple computers or connect the computers wirelessly.

---

### Post by jamesisin on 2010-05-24
Miljet - That would potentially allow the computers to see one another, but the OP is trying to use the first computer's Internet connection to serve the Internet to those other machines.

---

### Post by Miljet on 2010-05-24
OK, guess I didn't understand after all. But I don't see any advantage to sharing the connection through the computer rather than the router.

---

### Post by jamesisin on 2010-05-25
I take this:

"I have a mobile broadband usb modem that I get my internet connection from"

to mean that the OP only has access to the Internet through one machine's USB connection to that device.

Perhaps that's not what he meant though.

---

### Post by Miljet on 2010-05-25
Well, I assumed something entirely different from the title of the thread which does mention that he has a router.

Maybe we both need to wait and see if the OP better explains what they are trying to accomplish.

---


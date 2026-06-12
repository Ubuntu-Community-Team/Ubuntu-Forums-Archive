---
title: "Transfer contacts from Siemens CX75 to Ubuntu?"
date: 2010-06-10
forum: General Help
---

### Post by alexthunder on 2010-06-10
**I can't transfer contacts from Siemens CX75 to Ubuntu over bluetooth.**

I've managed to launch **XMPM** 1.3, but it doesn't detect my phone. Haven't found any other versions of XMPM,

**Wammu** doesn't detect my phone automatically and I have problems setting it up manually.

Can't launch **GSMxx** at all

And I don't really know how to set up **KMobileTools** . What devices should be entered when I connect my phone via Bluetooth?

---

### Post by dino99 on 2010-06-10
have you searched "phone" into synaptic ?

found with our nice friend google, an old howto, but should work:

****
7. My Siemens CX75 in Ubuntu 8.04:

       Aaahh!! At last my CX75 started talking with my Vaio. This is cool!!! The media here is "Wammu"

Here`s how i made it happen:

Step 1: Installed "gammu"

Step 2: Installed "wammu"

Step 3: Configured "gammu". How: 

                       i. create a file named .gammurc in your home directory. I created .gammurc in my /home/zico/

                      ii. open .gammurc with any text editor. I used vim. And enter these into your .gammurc. Here i want to let you know that, i wrote this for my *siemens*. So.. dude... you have to choose your own, i am not sure but i think it will be different for Nokia,Motorola or something other brands. Anyway, i inserted:

                       [gammu]
                       port=/dev/ttyUSB0
                       connection=at115200
                       name=Siemens CX75 

                      iii. save & get out from terminal.

                      iv. open "wammu" from Aplications->Accessories->Wammu

 

        & enjoy!!  
****

---

### Post by alexthunder on 2010-06-10
Could you please tell me how to find what port is used when connecting via bluetooth?

---


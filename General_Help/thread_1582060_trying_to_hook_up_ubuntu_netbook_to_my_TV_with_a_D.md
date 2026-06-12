---
title: "trying to hook up ubuntu netbook to my TV with a DVI cable"
date: 2010-09-25
forum: General Help
---

### Post by user1397 on 2010-09-25
my CRT 1080i Samsung TV has a DVI connection, and my Dell mini netbook has a VGA port, so I bought a DVI cable and a VGA-to-DVI adapter.  I'm not getting anything on my TV when I plug it in to my netbook...do I have to configure anything?

---

### Post by mrhhug on 2010-09-25
i recall my days of testing laptop lcds and usually i had to hit FN 7 or something to enable that port and disable the integrated screen - all the laptops were different and usually a picture of a CRT monitor on the key in blue (or whatever color the FN key is colored)

what the model do you have????

this might help [http://www.mydellmini.com/forum/general-mac-os-x-discussion/4043-mini-9-external-monitor-internal-off.html](http://www.mydellmini.com/forum/general-mac-os-x-discussion/4043-mini-9-external-monitor-internal-off.html)

i think on most PCs the integrated lcd would go off after switching to output video port

> my CRT 1080i Samsung TV has a DVI connection ^- crt? is that right?

whats the model to your tv?

---

### Post by robsoles on 2010-09-25
CRT stands for Cathode Ray Tube and that is the old style of monitors and TVs. I think mrhhug knows that and assumes OP knows it too but I think it's not unreasonable to wonder if anybody really knows anything, particularly me.

Anyway, the makers of such TVs can complicate the method of selecting which input you are looking at, are you absolutely certain that you have successfully selected DVI Input on the TV?

Open your display preferences (from 'System' menu, can be under 'preferences' or 'administration' depending on your manufacturer and drivers installed) and check whether it indicates the second monitor or not - if it's indicating the second monitor and allows you to enable it and configure it's output then it's more likely the TV is the problem end of the exercise.

---

### Post by mrhhug on 2010-09-25
> **robsoles said:**
> CRT stands for Cathode Ray Tube and that is the old style of monitors and TVs. I think mrhhug knows that and assumes OP knows it too but I think it's not unreasonable to wonder if anybody really knows anything, particularly me.

Anyway, the makers of such TVs can complicate the method of selecting which input you are looking at, are you absolutely certain that you have successfully selected DVI Input on the TV?

Open your display preferences (from 'System' menu, can be under 'preferences' or 'administration' depending on your manufacturer and drivers installed) and check whether it indicates the second monitor or not - if it's indicating the second monitor and allows you to enable it and configure it's output then it's more likely the TV is the problem end of the exercise.

mearly noting that CRTs and DVIs are different generations DVI means digital and digital CRT is .... 

i would note that most times on laptops (especially netbooks) will display on integrated LCD or output DVI/HDMI and not both, so to see an image on the integrated LCD would indicated that the video output is currently not outputting

---

### Post by user1397 on 2010-09-26
So I've tried a few more things which make my situation a little weirder.

I tried hooking up my desktop to the TV, through my graphics card's DVI port (so the adapter wasn't used) and it worked perfectly, no configuring required.

I tried it also with my dad's uber laptop, which doesnt have a dvi port so i had to use the adapter again, and (this is the weirdest part) it recognized the TV and everthing, I can see it in the nvidia control panel and in the regular settings, but it still won't show up on the TV no matter how I configure it.

Note that both my desktop and my dad's laptop run windows 7.

So I cannot say that the adapter is to blame completely, because through my dad's laptop it recognizes the TV, even though it still doesn't function properly...

Also on my netbook, it doesn't even seem to recognize the TV at all in the system > preferences > monitors program...

So yea if any of that made any sense, please help me :)

I'll post the TV model later, but my netbook is a Dell Mini 10v.

Thanks for the replies so far.

---

### Post by mrhhug on 2010-09-26
ok,,, so youve established that you can use the TV as a monitor (TVs are monitors + a tuner)

and your desktop has auto switching for the output-- most desktop card automatically detect what output to use.... your netbook with an integrated LCD doesn't need to do that - you need to tell the netbook that your "intending to use the DVI out instead of integrated LCD"

...... maybey this will help : DVI = HDMI - sound
VGA is just inferiour to both ...

---

### Post by dcstar on 2010-09-26
VGA is Analogue, DVI can have Analogue and Digital output. A lot of DVI cables/connectors only use the Digital connections.

Unless you have a unit that can receive DVI Analogue signals - as well as cables that actually have the **all** the pins of the DVI connector wired - then a converted VGA signal will not work (although a DVI Digital will).

---

### Post by mrhhug on 2010-09-26
> **dcstar said:**
> VGA is Analogue, DVI can have Analogue and Digital output. A lot of DVI cables/connectors only use the Digital connections.

Unless you have a unit that can receive DVI Analogue signals - as well as cables that actually have the **all** the pins of the DVI connector wired - then a converted VGA signal will not work (although a DVI Digital will).

this is why i freaking questioned you on a CRT that was digital.... WTF dude.... to convert digital to analog you need a box or computer or whatever you want to call it.... u need to do some math.....

---

### Post by robsoles on 2010-09-26
> **mrhhug said:**
> this is why i freaking questioned you on a CRT that was digital.... WTF dude.... to convert digital to analog you need a box or computer or whatever you want to call it.... u need to do some math.....

dcstar is not the OP and made only fair and true comment to make about the connections in question.

does the Desktop PC have a VGA output ubuntuman001? If so you might be able to further test the capability of the adapter and the cable you are using. If it doesn't do it through the adapter and cable from the desktop PC then it's not the laptop's fault...

---

### Post by jocko on 2010-09-26
> **ubuntuman001 said:**
> my CRT 1080i Samsung TV has a DVI connection, and my Dell mini netbook has a VGA port, so I bought a DVI cable and a VGA-to-DVI adapter.  I'm not getting anything on my TV when I plug it in to my netbook...do I have to configure anything?

1. Does the TV have DVI-A (analog), DVI-D (digital) or DVI-I (both analog and digital)?
Check your TV's manual for detailed specifications. If it's DVI-D (like most monitors that have both DVI and VGA) there is no way you can connect an analog signal to it.
2. Is your DVI cable DVI-I, DVI-A or DVI-D?
DVI-I and DVI-A have four pins for analog signals (above and below the flat ground pin), DVI-D have no wires or pins for analog signals.

---

### Post by user1397 on 2010-09-26
> **jocko said:**
> 1. Does the TV have DVI-A (analog), DVI-D (digital) or DVI-I (both analog and digital)?
Check your TV's manual for detailed specifications. If it's DVI-D (like most monitors that have both DVI and VGA) there is no way you can connect an analog signal to it.
2. Is your DVI cable DVI-I, DVI-A or DVI-D?
DVI-I and DVI-A have four pins for analog signals (above and below the flat ground pin), DVI-D have no wires or pins for analog signals.

meh, I guess my TV's is DVI-D, because it doesn't have the holes for the 4 pins.  My cable is DVI-I, but yea I guess I cannot use an adapter for it :( Oh well the adapter was only like $2.50...

---

### Post by user1397 on 2010-09-27
I guess I should mark this as solved :(

---


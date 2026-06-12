---
title: "Someone help me please"
date: 2010-05-21
forum: General Help
---

### Post by leonela.fulgencio on 2010-05-21
Hi 

i just installed ubunto 10.4 in my dell inspiron 1318 , and when i try  to activate wi-fi   using the on-off  button but doesn't turn the light  on and doesnt connect internet.  could you please help me , im new at  these.

greets

---

### Post by nothingspecial on 2010-05-21
You need to post your wireless card. In your menu go Accessories > Terminal and type into it
```

sudo lshw -C network
```

You will have to type your password which you will not see.

Copy and paste what the terminal says in a new post here.

---

### Post by coffee412 on 2010-05-21
According to the Dell setup guild for your laptop there is a wireless switch that is located on the right side of the laptop. Push the switch towards the back of the laptop to turn on wireless. Then Reboot your laptop to see if its recognized. The switch should click into place. 

If wireless is not recognized on reboot then perhaps the wireless chipset is not supported or the drivers are not available. In a terminal window you can type the following in :

sudo lspci -v

Post the details to see if your wireless internal card is recognized.

If there is a LED light that shows if your wireless is activated and its not lighting up perhaps your switch is bad on the side of the laptop and needs replacement.

coffee

---

### Post by leonela.fulgencio on 2010-05-21
Hi

i did what you and the only way i could show it is in images, i atached them here , thanks for your help.
[IMG]file:///G:/Pantallazo-2.png[/IMG]



> **nothingspecial said:**
> You need to post your wireless card. In your menu go Accessories > Terminal and type into it
```

sudo lshw -C network
```You will have to type your password which you will not see.

Copy and paste what the terminal says in a new post here.

---

### Post by nothingspecial on 2010-05-22
Get a wired connection. Open a terminal again and type ```
sudo apt-get install b43-fwcutter
```

Then reboot.

---

### Post by leonela.fulgencio on 2010-05-23
Hey , 

Thanks for  yor help , i got internet  , and my wirles signals are ok

---

### Post by nothingspecial on 2010-05-23
That`s good to know. Happy ubuntuing :)

---


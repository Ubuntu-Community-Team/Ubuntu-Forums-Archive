---
title: "What changed on my internet?"
date: 2010-07-11
forum: General Help
---

### Post by WOOHOOHOO on 2010-07-11
Hi,

i lost my internet/sound applet ages ago. But, sound and internet still works. for the past week, my internet won't start automatically when i turn on my PC. My housemate told me to type:

'sudo dhclient eth0'
'sudo ifconfig eth0 up',

and this works. But, i have to do it everytime. How can i make it auto?

Thanks!

J

---

### Post by WOOHOOHOO on 2010-07-29
Anyone?

---

### Post by davidmohammed on 2010-07-29
question - do you mean that the network manager icon is not starting automatically?

Can you check if you are running network manager as a startup application - N.B. it should have a command line of

nm-applet --sm-disable

---

### Post by WOOHOOHOO on 2010-07-29
No, i haven't seen my internet sylmbol for ages, nor my volume icon in the panel. It is selected on the menu list, but doesnt show. I believe my network manager applet was deleted when i was trying to do something else. 

Even without it, i managed to still get auto internet access when i turned on my laptop. But, for some reason, it just stopped working auto and now i have to type the above code in everytime i log in to use the net. It's a bit annoying.

---

### Post by dino99 on 2010-07-29
check settings into gconf-editor

sudo apt-get install -f
sudo dpkg --configure -a

---

### Post by dineshs on 2010-07-29
If you have Network manager pl try this.Hope you are using 10.04
Right click on the top panel-click add to panel-select notification area -click add
If the icon is back configure IP manually as follows
Right-click on the NM icon(two opposite arrows on top right) and then click on Edit Connections. 
Select the tab, wired 
select the ethernet connection you want and click edit(you can add the ethernet connection if not listed) 
select ipv4 
method-manual 
click add 
address [COLOR="Blue"]192.168.1.100 [/COLOR]
mask [COLOR="Blue"]255.255.255.0 [/COLOR]
gateway [COLOR="Blue"]192.168.1.1[/COLOR] 
then hit enter 
DNS [COLOR="Blue"]4.2.2.1[/COLOR]
then click apply 
Note :The addresses in [COLOR="Blue"]blue[/COLOR] are examples.you can substitute your values

---

### Post by WOOHOOHOO on 2010-07-30
> **dineshs said:**
> If you have Network manager pl try this.Hope you are using 10.04
Right click on the top panel-click add to panel-select notification area -click add
If the icon is back configure IP manually as follows
Right-click on the NM icon(two opposite arrows on top right) and then click on Edit Connections. 
Select the tab, wired 
select the ethernet connection you want and click edit(you can add the ethernet connection if not listed) 
select ipv4 
method-manual 
click add 
address [COLOR="Blue"]192.168.1.100 [/COLOR]
mask [COLOR="Blue"]255.255.255.0 [/COLOR]
gateway [COLOR="Blue"]192.168.1.1[/COLOR] 
then hit enter 
DNS [COLOR="Blue"]4.2.2.1[/COLOR]
then click apply 
Note :The addresses in [COLOR="Blue"]blue[/COLOR] are examples.you can substitute your values

Hi, i did the above, it automatically brought up the volume control icon and internet icon. The internet was disconnected when i did the above though. There was no set wired connection, so i added one, but i dont know where to add the mask,address etc?

Thanks for all your help, has been a pain for a while now.

J

---

### Post by dineshs on 2010-07-30
Are you using 10.04?
Did you right click the network icon and then edit connections.... as I suggested.On which step did you encounter problem?> but i dont know where to add the mask,address etc?
There is a tab ipv4(Right click NM icon-edit connections-wired-select the connection you just created-edit-ipv4-)

---

### Post by WOOHOOHOO on 2010-07-30
right, i re-read and tried againa dn it worked. I will mark this as solved. One small, off topic question: onmy bottom panel, the different apps i have open dont show, i have to move between then using  ALt Tab. How can i get these to show up down there?

Thanks for your help!

---

### Post by Raymond2201 on 2010-07-30
right click on the panel "Add to Panel" > Window List

---

### Post by WOOHOOHOO on 2010-07-30
Perfect, all fixed. Thanks for your patience and replies!
Jim

---


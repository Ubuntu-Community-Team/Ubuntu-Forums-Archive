---
title: "Cario-dock does not work?"
date: 2009-11-11
forum: General Help
---

### Post by Adrenochrom3 on 2009-11-11
ok i upgraded to ubuntu 9.10 and it installed like a different thing of cario-dock with (open-GL), and it doesnt work. its starting to make me mad because i used to use the dock a lot, and now i cant... can anyone tell me why it decided not to work anymore, and how i can fix it. cause id really like it back. thanks

---

### Post by RabidWeezle on 2009-11-11
Can always download and compile cairo-dock from their website's source, in fact, it's the only way I use cairo-dock since it's very active atm.

---

### Post by PrarieD0G on 2009-11-11
You should still (hopefully) have the original installed too. Just go to System>Preferences>Startup Applications, find GLX-Dock (Cairo Dock) and edit it so that the command is "cairo-dock -c" (without quotes). That should make it load the old Cairo-dock at startup instead of the openGL version.

Let me know if that works for you or not.

---

### Post by Adrenochrom3 on 2009-11-11
no it does not work.

see what happens when i start it is: this big window comes up thats called < Maintenance mode > 

it kinda looks exactly like the CompizConfig settings window. except it has different options and menus.

but then ever i click 1.) apply: nothing happens.  or 2.) Ok: the window closes and opens again. 

and after that point i get mad and try and close it, and it just keeps opening, making me have to force quit the application. 

so i hope that gives you a little more insight on my problem here.


also while the window is open, the dock does not appear. in fact i havent seen my dock since i upgraded to 9.10

---

### Post by Adrenochrom3 on 2009-11-11
> **RabidWeezle said:**
> Can always download and compile cairo-dock from their website's source, in fact, it's the only way I use cairo-dock since it's very active atm.

and as far as compiling goes, i suck horribly at it. i need much more practice. the only way i get things compiled, is by looking for guides. so yea. that will probably be my last option.

---

### Post by JustinR on 2009-11-11
Thats odd - because when I installed Ciaro Dock it put two menu items in the applications menu, to start with OpenGL and to start normally.

---

### Post by fabounet on 2009-11-12
which version of the dock are you using ? I strongly recommmend to use the one in the official repository, not the Ubuntu one
your version should be 2.1.1 then, and it fixes some bugs related to Karmic.

if you already has the 2.1.1, try 
```
mv ~/.config/cairo-dock/current_theme ~/.config/cairo-dock/current_theme.bak
```
then start the dock. Maybe you have a too much old theme.

---

### Post by Adrenochrom3 on 2009-11-12
i have installed version 2.0.9-0ubuntu1

i assume i have the later version. how do i update to 2.1.1, cause the update manager hasnt given me that update yet

---

### Post by fabounet on 2009-11-13
you have to add the Cairo-Dock's repository :
[http://www.cairo-dock.org/ww_page.php?p=From%20the%20repository&lang=en]("http://www.cairo-dock.org/ww_page.php?p=From%20the%20repository&lang=en")
I recommend that, because the project evolves very fast, and the updates in Ubuntu are really slow.

---

### Post by Adrenochrom3 on 2009-11-16
ok i had a problem adding the repository, when i added the address, it wouldnt let me add it. whats the address for your repository?

---

### Post by Adrenochrom3 on 2009-11-16
never mind. i added: deb http ://repository.cairo-dock.org/ubuntu jaunty cairo-dock  even though i dont have jaunty jackalope anymore, it worked. so thanks for all your help :)

---


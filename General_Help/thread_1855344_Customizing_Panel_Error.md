---
title: "Customizing Panel Error"
date: 2011-10-06
forum: General Help
---

### Post by JoshuaMiller0 on 2011-10-06
On Ubuntu 10.04 I am trying to customise the top Panel. I basically wanted the panel to be bigger so I can have larger icons. As I made the panel larger, instead of increasing the size of the system theme program bar image it simply tiled the smaller image. I did not like the look of this.

To fix this I did the following:
[LIST=1]
[*]Right-clicked on the panel
[*]Clicked 'Properties'
[*]Clicked the tab 'Background'
[*]Opened 'Take Screenshot'
[*]Selected 'Select area to grab'
[*]Clicked 'Take Screenshot'
[*]Grabbed the upper tile of the panel
[*]Save the screenshot
[*]Went back to 'Panel Properties'
[*]Selected 'Background image:'
[*]Selected the saved screenshot
[/LIST]

After all this this is the image I got:


[IMG]http://i.imgur.com/g2Emb.png[/IMG]

This is not what I wanted as I still have the tiled image on both sides of the panel where the menus are, and where my profile, Wireless etc. are.

The screenshot I took of the  upper tiled image of the panel:
[IMG]http://i.imgur.com/HUd9v.png[/IMG]

What needs to be changed:
[COLOR="Red"][IMG]http://i.imgur.com/iUskK.png[/IMG]
[SIZE="4"][FONT="Comic Sans MS"][B]I want these to have the
background of my custom 
screenshot.[/B][/FONT][/SIZE][/COLOR]

---

### Post by Krytarik on 2011-10-06
Actually, everything that you need to do is:

[LIST=1]
[*]Disable the custom background again.
[*]Make a backup of "/usr/share/themes/Ambiance/gtk-2.0/panel_bg.png".
[*]Scale the former to the height you set the panel to.
[*]Re-apply the theme.
[/LIST]
Greetings. :D

---

### Post by JoshuaMiller0 on 2011-10-06
> **Krytarik said:**
> 
3. Scale the former to the height you set the panel to.


Unfortunately I am not very good at using the Ubuntu image editors....... yet and I do not know how to change the pixel sizes for images.

Too help me could someone please either;
1. Attach a file with the .png completed (instructions above)
OR 2. (less preferred) Tell me step-by-step how to do it for myself.


> **Krytarik said:**
> 
Greetings. :D


What do you mean greetings? I find that offensive!!! I have been using Ubuntu for over a month! haha

---

### Post by Krytarik on 2011-10-06
Well, if you take my really friendly greetings phrase as an offense, I guess you need to figure it out on your own. ;-)
I was just happy to provide you a really easy solution, as opposed to what you've tried before.

But I give you two hints:

[LIST]
[*] ```
gksudo nautilus
```
[*]GIMP -> Image -> Scale Image
[/LIST]
 Btw., my "Greetings." is derived from the game "[Warlords II]("http://en.wikipedia.org/wiki/Warlords_%28game_series%29#Warlords_II")"; "Greetings, Warlord!", I love this phrase there! :D

But thanks to you I'll turn to using "Regards." instead for now, might be more appropriate anyway. :P

Regards.(!)

---

### Post by JoshuaMiller0 on 2011-10-06
haha ok! =D

---

### Post by JoshuaMiller0 on 2011-10-06
> **Krytarik said:**
> 
[LIST]
[*] ```
gksudo nautilus
```


All that did was take me to the "/root" folder containing only 'Desktop'.

When I did [ctrl] + [H] there were the following folders:
[LIST]
[*].config
[*].dbus
[*].gconf
[*].gconfd
[*].gnome2
[*].gnome2_private
[*].nautilus
[*].pulse
[*].synaptic
[*].wapi
[*].bashrc
[*].profile
[*].pulse-cookie
[*].recently-used
[*]Desktop
[/LIST]

and '.nautilus' was empty even with [ctrl] + [H]

---

### Post by JoshuaMiller0 on 2011-10-13
> **Krytarik said:**
> Actually, everything that you need to do is:

[LIST=1]
[*]Disable the custom background again.
[*]Make a backup of "/usr/share/themes/Ambiance/gtk-2.0/panel_bg.png".
[*]Scale the former to the height you set the panel to.
[*]Re-apply the theme.
[/LIST]
Greetings. :D

I have found a problem with your suggestion.

What I wanted was the top panel image to be double the size. Your suggestion would make not only the top panel but the lower panel and all windows double the size. I only want the upper panel to be double the size...

---

### Post by Krytarik on 2011-10-14
> **JoshuaMiller0 said:**
> What I wanted was the top panel image to be double the size. Your suggestion would make not only the top panel but the lower panel and all windows double the size. I only want the upper panel to be double the size...
Ok, I didn't get that from reading your OP. In that case, you can disable the default panel background image in the theme completely, by following this guide:

[http://www.tuxgarage.com/2011/06/customize-appearance-of-gnome-panel.html](http://www.tuxgarage.com/2011/06/customize-appearance-of-gnome-panel.html)

..., and then set the background image for either panel individually; the bottom panel to the default one, and the top panel obviously to the resized one.

---

### Post by JoshuaMiller0 on 2011-10-15
> **Krytarik said:**
> Ok, I didn't get that from reading your OP.

...well... I never mentioned the lower panel... so it could be either way... anyway... dw!

Thanks for suggestion I will do at some point and once I have and it works I will add a 'HOWTO:' and mark as solved :)
(I'm busy............. being lazy...)

---


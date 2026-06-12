---
title: "Apple Alu BT Keyboard and Ubuntu 9.04? Need Help!"
date: 2009-07-11
forum: General Help
---

### Post by vickoxy on 2009-07-11
Hi again. Under Hardy (dell) Apple BT Keyboard worked very well. I paired it now with my new installed Ubuntu 9.04 but there are some issues.

After start up it won´t pair automatically. There stays in bluetooth setup that the keyboard is paired. So, i have to push few times off/on button on keyboard, and after some time it works. Anyone has experience with this? Is there any way possible to make Apple Keyboard to work so elegant as under 8.04?


So, please help me-i write a lot but it is a little bit frustrating having it not working properly.
Thanks

---

### Post by vickoxy on 2009-07-12
Ok, i installed blueman to see what is going on...But, when i click on bluetooth manager to show me apple keyboard, it says that everything is normal, and that the connection is optimal. And really, if i make restart, and press keyboard, the green light blinks once (as it should be), but it does not connect.

So, each time i have to: 
1) press on/off switcher for a long time (as i switch it off)
2) press on just once (green light blinks)
3) than hold on on/off switcher few seconds an release it just before the keyboard shut off.

So, i think it is connected, but it want do typing at a first. So, if someone can help me...

And then the keyboard is working again. And after standby it works just fine.

---

### Post by vickoxy on 2009-07-12
UPDATE: i found one more elegant solution. After startup i went to devices setup (i use now blueman, although i think that bluez-gnome will do the same)-and disconnect apple keyboard, and then i pressed connect-and it connects immideatly and starts typing. Before that, have to press any key on keyboard (it will be connected, but not typing)

So, as it seems, bluetooth connection is working, but at startup it won´t start typing.

So, if anyone has any idea...

---

### Post by Bloupikkewyn on 2009-08-07
I have exactly the same problem. Plus I use the mighty mouse as well. When paired through Bluez-Gnome as you described, they work perfectly! Scroll buttons, special keys the works! However, at startup the mighty mouse tends to connect (I say tends, since it doesn't always!) and the keyboard often takes either a long while to connect, or doesn't! Funny enough sometimes the keyboard connects, but the mouse doesn't!! :confused:

When I log in (While they are still unpaired) I see Bluez says they are! Even hidd says they are paired! It is only when I disconnect and reconnect with bluez-gnome that they work!

And they do work well!! Even when switching users in Gnome they work fine...

ELP!

---

### Post by P4man on 2009-08-07
Similar problems here with a BT mouse. Its a known bug and Ive been waiting for a fix since.. forever. 

[https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/343727](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/343727)

There might be workarounds in there that work for you, the only thing that really helped me was typing:

sudo hidd --search

in the terminal. 99% of the times that cures it. Still annoying (especially when its your keyboard that stops working I imagine!).

You can also try this:

> 1) install the bluez-compat package with terminal

sudo apt-get install bluez-compat

2)Pair the mouse with the bluetooth manager. The manager will say that the pairing is "successfull"
Although the mouse won't worked... this step has to be down...

3) In the terminal, type :

sudo hidd --search

You should see something like

Searching ...
Connecting to device 00:XX:XX:XX:XX:XX (your mouse MAC)

Done. Your mouse should be working now.

---

### Post by vickoxy on 2009-08-07
So, this is what i do now (almost the same as before). As soon as i reboot, i press any key on keyboard (it connects itself then to computer, but it will not type)-then i open bluetooth setup-disconnect the keyboard.
After that - as i press any key - the Apple BT Keyboard connect automatically.

So, as long there is no other fix, this will be ok for me. But, on Hardy (8.04) i had no such problems-once i made set up it worked all the time just fine...

---

### Post by Bloupikkewyn on 2009-08-08
*SIGH* I even compiled Bluez 4.42. Still doesn't work! Has anyone tried maybe forcing the older versions used in Hardy? I haven't done that before. I haven't used Ubuntu in a long while. It networks so well and synaptic is a wonder for my work. But one always finds SOMETHING to complain about. Seems that is part of the fun I guess. Now why can't I just use a normal keyboard and mouse... hehehe

---


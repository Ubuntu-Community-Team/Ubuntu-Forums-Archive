---
title: "Mic not working and nothing helps"
date: 2010-04-02
forum: General Help
---

### Post by Petersteele111 on 2010-04-02
Ok so I have tried everything I know and read tons of pages on this. Nothing people suggest helps. My mic won't work at all no matter what I do and I get no volume control thing either? When I click the speaker on the toolbar at the top of the screen I get sound prefrences. Well I can't do anything in there for my mic. All I get is input but no setting ever works. Even when i plug my mic into the pink port on my computer tower I get nothing.I have it plugged next to my speakers atm on the sound card. Since everyone says to click edit in volume control I got a little worried because I have no such thing. So I typed in terminal gnome-volume-control well this is what I got

peter@peter-steele:~/Desktop$ gnome-volume-control

** (gnome-volume-control:2914): WARNING **: Bad setup, install the freedesktop sound theme

(gnome-volume-control:2914): Gtk-CRITICAL **: gtk_tree_model_get_iter_first: assertion `GTK_IS_TREE_MODEL (tree_model)' failed

Ok what the heck does this mean? Just above this code I autoremoved gnome-media and reinstalled it. So I don't know whats going on but it is driving me insane. Sometimes switching the hardware on my the sound preferences will get me some sort of input but when i close out and try to record in the sound recorder it does nothing. Nothing is muted and my speakers work just fine plugged into the sound card. I also typed alsamixer in terminal and it opened but I couldn't change anything or do anything but look and close it out. I tabbed over and it said mic and had two bars that were empty. Above it said capture ALL. So whats going on? I have two mics hooked up to this old pos computer. One is built into the monitor and the other is a Logitech Desktop Microphone 600(not the USB one). I really am at a loss on how to fix all of this. I am newer to linux and like it so far except all the problems I am having getting everything to run correctly. It recognizes my sound card but I cant get any mics to work on this computer. I am running an old hp pavillion xt926 900mhz AMD duron proccesor with 256mb ram. Its an old junker that I got going again with Xubuntu but this mic thing is making me very irritated. Maybe someone on here knows how to get this to work? maybe there is a package or something i forgot to download i don't know but I really need yall's help. Also note that i just took this computer apart and it said creative labs for the sound card. Well alsamixer says...
Card: Ensoniq AudioPCI                                                                 &#9474;
&#9474; Chip: SigmaTel STAC9708,11                                                             &#9474;
&#9474; View: [Playback] Capture  All                                                          &#9474;
&#9474; Item: Master [dB gain=0.00, 0.00]
now ill show you a pic of the sound card..
[http://s836.photobucket.com/albums/zz281/petersteele111/Computer/?action=view&current=Soundcode3.jpg](http://s836.photobucket.com/albums/zz281/petersteele111/Computer/?action=view&current=Soundcode3.jpg)
[http://s836.photobucket.com/albums/zz281/petersteele111/Computer/?action=view&current=Soundcard.jpg](http://s836.photobucket.com/albums/zz281/petersteele111/Computer/?action=view&current=Soundcard.jpg)

Here is a link to what my sound card is and its specs
[http://www.netcomdirect.com/crlactsoblsb.html](http://www.netcomdirect.com/crlactsoblsb.html)
[IMG]http://s836.photobucket.com/albums/zz281/petersteele111/Computer/?action=view&current=Soundcode3.jpg[/IMG]

---

### Post by irishbreakfast on 2010-04-02
I know the feeling - it took me a long time (in real time not the total number of hours) to get my mic working. I am not an expert in this at all.
Couple of thoughts: Since you get errors with gnome-volume-control from a terminal. I'd consider purging it and then reinstalling it.
alsa-mixer: when you tab over to the item you want, you should be able to us the arrow keys to raise/lower the value. If you want you can install gnome-alsa-mixer, the gui is a bit easier.
As for me, it was raising the values using alsa-mixer that finally did the trick. However, I would swear I tried that several months ago and it didn't work, but now it does. Oh well.
Sorry I can't help more.

---


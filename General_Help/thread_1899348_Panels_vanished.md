---
title: "Panels vanished"
date: 2011-12-23
forum: General Help
---

### Post by Agent26 on 2011-12-23
Hi there all, Just a quick thing today.
For some reason my pannels dissapeared in my xubuntu 10.4.2 and I cant see how to get them back, is there a terminal code I could use please? both my upper and lower panels just went and never returned??
Thankyou and i'm sure this will turn out to be very easy.

---

### Post by Toz on 2011-12-23
Check if xfce4-panel is running:
```
ps -ef | grep xfce4-panel | grep -v grep
```
If not, try starting it:
```
xfce4-panel &
```
If still nothing, post back any error messages that might show up in the terminal or in ~/.xsession-errors

---

### Post by Agent26 on 2011-12-23
Hi Toz and thanks for the reply, After typing the first line nothing happens and the running info is not dissplayed. After adding the second code it brings back the panels and this....
(xfce4-cpugraph-plugin:1849): Gtk-CRITICAL **: gtk_container_set_border_width: assertion `GTK_IS_CONTAINER (container)' failed

(xfce4-mixer-plugin:1847): libxfce4mixer-CRITICAL **: xfce_mixer_get_track: assertion `GST_IS_MIXER (card)' failed

(xfce4-mixer-plugin:1847): xfce4-mixer-plugin-CRITICAL **: xfce_mixer_plugin_set_card: assertion `GST_IS_MIXER (card)' failed

(xfce4-mixer-plugin:1847): xfce4-mixer-plugin-CRITICAL **: xfce_mixer_plugin_set_track: assertion `GST_IS_MIXER_TRACK (track)' failed

Unfotunatly as soon as I close terminal the panels just dissapear again.

Thankyou for the help

---

### Post by Agent26 on 2011-12-23
Hi there, some more background on the prob.

It was just after I installed the free spotify in wine I got the trouble.
Wine installed spotify ok but as soon as I open it spotify was just a black screen.
Then as I was closing down thats when the panels just went.

I never seem to have any luck with wine.

---

### Post by dino99 on 2011-12-23
use the latest wine from ppa: 
[https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=8514](http://appdb.winehq.org/objectManager.php?sClass=application&iId=8514)

---

### Post by Toz on 2011-12-23
> **Agent26 said:**
> Hi Toz and thanks for the reply, After typing the first line nothing happens and the running info is not dissplayed. After adding the second code it brings back the panels and this....
(xfce4-cpugraph-plugin:1849): Gtk-CRITICAL **: gtk_container_set_border_width: assertion `GTK_IS_CONTAINER (container)' failed

(xfce4-mixer-plugin:1847): libxfce4mixer-CRITICAL **: xfce_mixer_get_track: assertion `GST_IS_MIXER (card)' failed

(xfce4-mixer-plugin:1847): xfce4-mixer-plugin-CRITICAL **: xfce_mixer_plugin_set_card: assertion `GST_IS_MIXER (card)' failed

(xfce4-mixer-plugin:1847): xfce4-mixer-plugin-CRITICAL **: xfce_mixer_plugin_set_track: assertion `GST_IS_MIXER_TRACK (track)' failed

Unfotunatly as soon as I close terminal the panels just dissapear again.

Thankyou for the help

Try Alt+F2 to open the run box and run it from there. If on re-login it fails to start again, you may need to reset your sessions cache:
```
rm -rf ~/.cache/sessions
```

---

### Post by Agent26 on 2011-12-23
Thanks again Toz.
I have to go to work now but will try this when I get home thankyou for the help.

---

### Post by Agent26 on 2011-12-24
Hi Tos and Dino, thanks again for the help. Ive got that new wine now.

You was right Toz I had to reset my sessions cache first  and then run from that little box.
thankyou very much as I appriceiate any tips even small ones like this.

Thats 3 or 4 new terminal codes now learnt.
Thankyou.:)

---


---
title: "Some Giada N20 remote control buttons do not work"
date: 2011-08-21
forum: General Help
---

### Post by idan.reller on 2011-08-21
I recently installed Ubuntu 11.04 on a Giada N20.
This computer comes with an integrated IR receiver and an IR remote, which can be seen here:
[http://www.pcmag.com/slideshow_viewer/0,3253,l%253D256651%2526a%253D256568%2526po%253D6,00.asp?p=n](http://www.pcmag.com/slideshow_viewer/0,3253,l%253D256651%2526a%253D256568%2526po%253D6,00.asp?p=n)

The computer can be turned on via the remote, so I don't think it's just a simple IR receiver. Furthermore, lircd is not running.

My problem is that some of the remote buttons do not work. I tried the buttons with xev, but there was no response.

I also tried:
'showkey -a'
'showkey -s'
'showkey -k'
and still, nothing.

The buttons which do not work are the colour buttons (red, green, blue, yellow), the menu button (the one above the OK button), the channel buttons (to the right from the mute button) and the 'txt' button (above the green button).

I know that the remote transmits something when I press these buttons, because the light in the computer turns on.

And there's another thing:
pressing the "*" (asterisk) button prints a "8" in a text editor; In xev, "*" seems like a bunch of presses, not just "8".
Something similar happens with the "#" (hash) button.

I don't want to add a separate IR receiver and remote. I want to use the remote which came with the computer, as it can turn it on.

My plan is to use this remote as a "keyboard" while running mythTV (this is why I'd like all buttons to work).

Any help will be highly appreciated.


Regards,
Idan

---


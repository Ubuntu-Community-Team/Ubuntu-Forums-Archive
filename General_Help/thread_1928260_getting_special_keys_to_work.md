---
title: "getting special keys to work"
date: 2012-02-19
forum: General Help
---

### Post by BuddyThirteen on 2012-02-19
Keyboard model: Microsoft Wireless Keyboard 2000

[IMG]http://ecx.images-amazon.com/images/I/61dciLP47VL._AA1000_.jpg[/IMG]
(sorry about the big pic, it comes right from amazon)

My computer serves as the entertainment center of the living room, dvd's, hulu, music, et cetera. So I got this fairly cheap wireless keyboard (came with a mouse, too) to simplify things.

If I physically push the button on the DVD drives, sometimes the discs don't unmount properly, and the next disc inserted won't trigger the launch of VLC. But using the eject command via terminal removes this inconvenience, as it unmounts the disc.

So I was looking into how to assign ejection to the keyboard keys. As I'm not on Windows (that computer isn't even dual boot), those little numbered keys at the top are useless. They do nothing. I wanted to assign the "1" and the "2" to eject the first and second drives, respectively.

But Ubuntu can't even see these buttons. Literally every other button on this keyboard is recognized. The media buttons work perfectly for volume, track skipping, play/pause (except in VLC, for which we just use the spacebar). Even the calculator button works. The one with the star sends the command "favorites" but doesn't seem to open any programs. But at least that means it's recognized.

In the end, I assigned them to the Home and Mail buttons on the far left, but it's not ideal. I don't use email on this computer, but someday I might. So I'd really like to be able to use buttons "1" and "2" for this. And knowing how to do it would also open up the other keys for custom commands as well, which might be useful.

As per one website, I tried "acpi_listen" in the terminal, and it didn't see these keypresses.

It is fun to sit across the room and hit these buttons and watch the trays go in and out, though.

So, any thoughts?

[edit]: It's Oneiric, btw.

---

### Post by bibble235 on 2012-02-19
Maybe this will help?

[http://askubuntu.com/questions/72562/how-can-i-get-media-keys-working-on-my-keyboard](http://askubuntu.com/questions/72562/how-can-i-get-media-keys-working-on-my-keyboard)

---

### Post by BuddyThirteen on 2012-02-22
Nope. Didn't work. It's not the Curve 2000, although that is the model that I just replaced. The media keys work fine. These keys seem to be some other class of keys.

---


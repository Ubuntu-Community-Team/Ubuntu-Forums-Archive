---
title: "Hangul key of korean keyboard is not working as expected"
date: 2011-12-16
forum: General Help
---

### Post by gpraveenya on 2011-12-16
Hello all,
 
I am using ubuntu 9.04. I connected a usb korean keyboard (dubeolsik). All keys are working fine except 2 keys( hangul and hanja) those are extra when compared to normal keyboard. Hangul key exist between spacebar and right alt key and hanja key exists between spacebar and left alt key. 
Actually when hangul key pressed, typing language should switch from english to korean or viceversa. But this function is happening when we press right alt key. I want to remap hangul key to work as expected. 
 
This is the actual problem. If anyone have idea of how to get it solved please help.
 
I tried something but did not worked. Let me explain what I tried, correct me If I am going in wrong direction.
 
I tried to find keycode of Hangul key using xv and showkey but they are not able to read events from those 2 keys. So I tried to find scan codes and map scancodes to keycodes manually using 2 ways 1. using setkeycodes command and 2. using keymap utility of udev. I found that scancodes for the 2 keys are 0xf1 and 0xf2 as per showkey command and also by some search on web. But when I run,
setkeycodes f1 121 , it gives error KDSETKEYCODE invalid argument and 
when I run,
keymap input/input4 hangulkey.map , it gives error EVIOCGKEYCODEinvalid argument. ( I just entered scancode and keycode in hangulkey.map file)
 
Thanks

---


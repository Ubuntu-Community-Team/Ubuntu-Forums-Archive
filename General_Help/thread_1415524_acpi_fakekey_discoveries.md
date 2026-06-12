---
title: "acpi_fakekey discoveries"
date: 2010-02-24
forum: General Help
---

### Post by jeff.sadowski on 2010-02-24
I have been having difficulties selecting keycodes for some of my keys and took time to see what keycodes I could send with acpi_fakekey here is how I tested what keys worked.

first I mapped my Fn+F7 / [x] key to run /etc/acpi/lockbtn.sh using /etc/acpi/events/asus-eee-lock

someone else could use another key that only shows up as an acpi event while pressed.

to see what acpi event is produced use acpi_listen

my Fn+F7 / [x] key outputs event
hotkey ATKD 00000016 0000016e

The last number "0000016e" is how many times I pressed the key since last reboot.

then I created the file /etc/acpi/events/asus-eee-lock
containing

> # Handle Asus Eee PC volume down key.
event=hotkey (ATKD|HOTK) 00000016
action=/etc/acpi/lockbtn.sh

then make it executable via "chmod a+x /etc/acpi/events/asus-eee-lock"

you can see that I used the first 3 fields from acpi_listen with a modification from ATKD to (ATKD|HOTK). It wasn't working for me without that change. I saw that change in other events.

then I modified /etc/acpi/lockbtn.sh to read as follows

> #!/bin/bash
test -f /tmp/lastkeycode || echo 0 > /tmp/lastkeycode
keycode=`tail -n 1 /tmp/lastkeycode`
let keycode=$keycode+1
echo $keycode >>/tmp/lastkeycode
acpi_fakekey $keycode

then make it executable via "chmod a+x /etc/acpi/lockbtn.sh"

then I went to tty1 (don't go here till you know how to get back. Ctrl+Alt+F1 to go there Alt+F7 to get back)
Then I started "showkey"
then I pressed Fn+F7 till it stopped showing a keycode.
Then I wrote what keycodes did show
when I came to a patch that didn't show keycodes I went till I found keycodes. echoing previous numbers to /tmp/lastkeycode like so
> echo 186 > /tmp/lastkeycode
when it came to patches or I was unsure if showkey exited while I was pressing the key. I went back to the last keycode that showed or didn't show depending on what I was looking for.

After that I used /usr/share/acpi-support/key-constants to see what key names to keycode translations where.

here are codes that showed for me

1-83
85-100
102-119
121-128
140
142-143
155-159
163-166
172-173
183-185
226

I am pretty sure keycodes stop at 255 so I stopped checking after 255.

My questions are:

1. Are the available keycodes the the same for everyone? (people with laptops other than eeepc or desktops) people with desktops could use the power button to press if they edit the power buttons events not to do anything else.

2. If not how do I get the keycodes I am missing to show? (if you know)

3. Is this a kernel issue? (again if you know)

Thanks for reading my questions and I hope at least one other finds this usefull.

-------------------------------------------------------------

Trying to find keys I can use that are not premapped to functions I don't want to use or maybe keys that are already mapped to function I would like them to do.

Out of the keycodes that come through ones that are mapped already to other keys I'd like to leave alone. The following are premapped to events already.

KEY_STOP=128
KEY_PAUSE=119
KEY_MAIL=155
KEY_CALC=140
KEY_HOMEPAGE=172
KEY_BACK=158
KEY_FORWARD=159
KEY_PLAYPAUSE=164
KEY_REFRESH=173
KEY_BOOKMARKS=156
KEY_NEXTSONG=163
KEY_PREVIOUSSONG=165
KEY_STOPCD=166

the following if they are mapped to functions I'd like to know maybe its for a program I don't use. I've been trying to figure out translations of some of the keys.

KEY_ZENKAKUHANKAKU=85
KEY_102ND=86
KEY_RO=89
KEY_KATAKANA=90
KEY_HIRAGANA=91
KEY_HENKAN=92
KEY_KATAKANAHIRAGANA=93
KEY_MUHENKAN=94
KEY_MACRO=112
KEY_POWER=116
KEY_KPPLUSMINUS=118
KEY_HANGUEL=122
KEY_HANJA=123
KEY_YEN=124
KEY_WAKEUP=143
KEY_COMPUTER=157
KEY_F13=183
KEY_F14=184
KEY_F15=185
KEY_MEDIA=226

I think F13-F15 are safe to use since most keyboards do not have these keys.
I have a key that looks like a running man I mapped to computer (shows in xev as my computer)
The keys on my eeepc that need visible keycodes are
Fullscreen1 (looks like a fullscreen button)
Fullscreen2 (looks the same but on F4)
Mouse (looks like a mouse with a slash through it probably to enable/disable the mouse)
I mapped my second lock key button on F7 to Stop

---

### Post by tgalati4 on 2010-02-25
Most thinkpads have the extra keys mapped through the module thinkpad_acpi.  They have default functions defined but you can remap them.  Some are tied to the BIOS (for nightlight, brightness, video switch, TV-out, wireless on/off etc) Others simply run scripts to do things like sleep and hibernate.

The [www.thinkwiki.org](www.thinkwiki.org) has a complete description of these keys.  I don't think there is any standardization between manufacturers.

---

### Post by jeff.sadowski on 2010-02-25
> **tgalati4 said:**
> Most thinkpads have the extra keys mapped through the module thinkpad_acpi.  They have default functions defined but you can remap them.  Some are tied to the BIOS (for nightlight, brightness, video switch, TV-out, wireless on/off etc) Others simply run scripts to do things like sleep and hibernate.

The [www.thinkwiki.org](www.thinkwiki.org) has a complete description of these keys.  I don't think there is any standardization between manufacturers.

I have no doubt that they have different keys and that different people may map them differently. I am asking if the allowed keycodes are the same?

---

### Post by Johnny B on 2010-02-25
for 2 did you try: > xmodmap -pke 

---

### Post by jeff.sadowski on 2010-02-25
> **Johnny B said:**
> for 2 did you try:

xmodmap remaps keycodes to do different things you can remap keycode 24 to type an "a" instead of a "q" ie you can make a Dvorak keyboard and arange your keys appropriatly however that is a user mapped way. What I am asking is how do I get keycodes that are not showing up. Its like some are being filtered. If I send keycode 84 using "acpi_fakekey 84" it doesn't show as a pressed key no matter how I map it via xmodmap. besides I'm working on getting it displayed to the console to showkey.

---

### Post by tgalati4 on 2010-02-26
Each laptop's BIOS filter's keys differently.  You need the correct acpi kernel module for a specific brand/model.  Thinkpad_acpi is just an example.

---


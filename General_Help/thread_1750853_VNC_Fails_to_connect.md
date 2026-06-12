---
title: "VNC Fails to connect"
date: 2011-05-05
forum: General Help
---

### Post by galego on 2011-05-05
It has been a long time since I have been here and even longer since I ran Ubuntu as my primary OS. I really like the progress of this distribution and Linux as a whole. It seems like last week I was learning code to get my desktop to work with "Beryl" and all the fancy effects. Now, they are in the code.

Ok sorry! 
New install (a couple of times) 11.04 fully updated and just a couple of added programs. Using 'Remmina' as my remote desktop viewer (which is awesome btw) but for some reason a VNC connection just will not happen. I can connect and I see the exchange (netstat shows it on both computers) but when I click connect the screen flashes gray and dies. I saw some errors, about unknown RFB connection, but not sure what is unknown. Google did not produce anything and nothing in the forums. Anything, which may be helpful on at least why vnc crashes would be awesome.

thank you.

---

### Post by galego on 2011-05-06
bump!! :(   ???

here is some more info if it helps:

```

alegalle@emcrdub11:~$ remmina    
Remmina plugin RDP (type=Protocol) registered.
Remmina plugin RDPF (type=File) registered.
Remmina plugin RDPS (type=Preference) registered.
xkbLayout: us	xkbVariant: 
xkbLayout: us
	xkbVariant: 
find_keyb[CODE]
```oard_layout_ioard_layout_in_xorg_rules: 409
detect_keyboard_layout_from_locale: 409
Using US (0x00000409)
Loading keymap evdev
xkbfilepath: /usr/share/freerdp/keymaps/evdev
Loading keymap aliases(qwerty)
xkbfilepath: /usr/share/freerdp/keymaps/aliases
kbd_init: detect_and_load_keyboard returned 1033
Remmina plugin VNC (type=Protocol) registered.
Remmina plugin VNCI (type=Protocol) registered.
Remmina plugin SFTP (type=Protocol) registered.
Remmina plugin SSH (type=Protocol) registered.
(remmina-applet avahi-browser) Found service 'alegalle's remote desktop on emcrdub11' of type '_rfb._tcp' in domain 'local'
(remmina-applet avahi-browser) Found service 'alegalle's remote desktop on emcrdub11' of type '_rfb._tcp' in domain 'local'
(remmina-applet avahi-resolver) Added service '[emcrdub11.local]:5900'
[/CODE]

---

### Post by saintslaughter on 2012-03-08
Did you get this resolved? I'm having the Exact same problem.

---


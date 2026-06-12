---
title: "Bios update, Kernel errors"
date: 2009-12-29
forum: General Help
---

### Post by Crixler on 2009-12-29
I updated my bios on my Gigabyte EP45-UD3R to the latest version, and now when I try loading Ubuntu, it fails at various points. The farthest I've gotten is the login screen, where I input my information and it made me enter it again, and then it logged me in, but without the GUI. I was sent directly into a terminal. It only got that far once, all other tries it gave me various errors, often relating to the kernel. I tried both the latest, and the older real time kernel used for ubuntu studio. I tried the recovery mode things in grub that I don't actually for sure know what they're for, but they looked helpful. The recovery for the newer kernel gave me a ton of errors and just sat there, while the real time kernel's recovery mode brought me to a simple menu screen. I tried the fix broken sectors option, and it did some stuff, and brought me back to the menu. Wanting to be sure things worked out, I did it again, and it did some more stuff. When it brought me back to the menu again, I chose the boot normally option (or something like that, anyway), and it brought me straight to the terminal. This was actually before the previous terminal incident. I've tried loading the cd in hopes of simply doing a clean install to fix this whole mess (the installation's only about a day old anyway, so I wouldn't be losing anything), but when I choose install on the disc menu, it loads the ubuntu logo, then after a while brings up a blinking underscore and just sits there. I let it sit there for about half an hour, thinking it was just being slow, but it didn't change. I tried a few more times, and it did the same thing. When I tried booting Linux from the live cd, it gave me all the same errors as when I tried loading it through grub. I should probably mention now that I've been talking about 9.10. 3 times, however, I actually made it into ubuntu through the live cd, and the first two times I tried loading firefox to look for help, and about a minute in, it would suddenly bring me to the login screen, only my login info wouldn't work. The third time, I decided I would try avoiding firefox, and it didn't bring me to that screen again. However, it gave me a few errors about serious kernel errors and crashes. So now I kinda regret that bios update, because things were working a lot better before (although I was still having some issues with my soundcard being recognized). What can be done about all of this? :confused:

---

### Post by Crixler on 2009-12-29
I now suspect the problem may be my RAM. I ran memtest86+, and it spit out a ton of errors. I looked at my ram settings in my bios, and there was only one option on that I don't recall being on before, so I tried turning it off, but it didn't change anything. Memtest still fails me.

Edit: Ok, I figured it out, my ram doesn't want to run at 1066 anymore, so I had to underclock it to 800. I've read there's not a huge difference anyway.

---


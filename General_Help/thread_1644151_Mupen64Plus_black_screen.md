---
title: "Mupen64Plus black screen"
date: 2010-12-12
forum: General Help
---

### Post by joelstitch on 2010-12-12
I have been using Mupen64Plus for a few days now with absolutely no problem. Out of nowhere Mupen64Plus stopped playing some roms and some would work after opening and closing the a few times. But my main problem is that some roms work but after a few minutes of gaming the screen goes black, the game is still going but with a black screen. 

Here is video of what happens:

[http://www.youtube.com/watch?v=aY7LLuDtRus](http://www.youtube.com/watch?v=aY7LLuDtRus)

---

### Post by cipherboy_loc on 2010-12-12
Try running it from a terminal, and post the output.

---

### Post by joelstitch on 2010-12-12
Nothing came up on the Terminal when the screen went b;ack. But this is what I got:

> pag@pag-laptop:~$ mupen64plus
 __  __                         __   _  _   ____  _             
|  \/  |_   _ _ __   ___ _ __  / /_ | || | |  _ \| |_   _ ___ 
| |\/| | | | | '_ \ / _ \ '_ \| '_ \| || |_| |_) | | | | / __|  
| |  | | |_| | |_) |  __/ | | | (_) |__   _|  __/| | |_| \__ \  
|_|  |_|\__,_| .__/ \___|_| |_|\___/   |_| |_|   |_|\__,_|___/  
             |_|         [http://code.google.com/p/mupen64plus/](http://code.google.com/p/mupen64plus/)  
Version 1.5

Config Dir:  /home/pag/.config/mupen64plus/
Data Dir:  /home/pag/.local/share/mupen64plus/
Cache Dir:  /home/pag/.cache/mupen64plus/
Install Dir: /usr/share/mupen64plus/
Plugin Dir:  /usr/lib/mupen64plus/

Rescanning rom cache.
Scanning... /home/pag/Documents/Nintendo 64/
Rom cache up to date. 11 ROMs.
Compression: Uncompressed
Imagetype: .v64 (byteswapped)
Rom size: 33554432 bytes (or 32 Mb or 256 Megabits)
MD5: 2A0A8ACB61538235BC1094D297FB6556
80 37 12 40
ClockRate = f
Version: 144b
CRC: 5354631c 3a2def0
Name: ZELDA MAJORA'S MASK
Manufacturer: Nintendo
Cartridge_ID: 535a
Country: USA
PC = 80080000
EEPROM type: 0
init timer!
[RiceVideo] Disabled SSE processing.
[blight's SDL input plugin]: version 0.0.10 initialized.
memory initialized
[RiceVideo] Disabled SSE processing.
[RiceVideo] Found ROM 'ZELDA MAJORA'S MASK', CRC 1c635453f0dea203-45
[RiceVideo] Enabled hacks for game: 'ZELDA MAJORA'S MASK'
InitExternalTextures
Texture loading option is enabledFinding all hires texturesInitializing OpenGL Device Context
(II) Initializing SDL video subsystem...
(II) Getting video info...
(II) Setting video mode 1024x768...
NVIDIA Corporation - GeForce 7150M / nForce 630M/PCI/SSE2 : 2.1.2 NVIDIA 195.36.24
[RiceVideo] OpenGL Combiner: Fragment Program
[JttL's SDL Audio plugin] version 1.5 initalizing.
[JttL's SDL Audio plugin] Initializing SDL audio subsystem...
[JttL's SDL Audio plugin] Allocating memory for audio buffer: 65536 bytes.
[blight's SDL input plugin]: Couldn't open joystick for controller #0: There are 0 joysticks available
Starting r4300 emulator
R4300 Core mode: Dynamic Recompiler
R4300 core: starting 64-bit dynamic recompiler at: 0x7f3a9005c200.
^AR4300 core finished.
[JttL's SDL Audio plugin] Cleaning up SDL sound plugin...
[RiceVideo] Found ROM 'ZELDA MAJORA'S MASK', CRC 1c635453f0dea203-45


---

### Post by cipherboy_loc on 2010-12-12
A few questions:

1) What ROM are you using.
2) Does the ROM file work on other computer?
3) Does it happen with other ROMS on the same computer?
4) Have you tried this ROM in a different emulator?


Thanks,
Cipherboy

---

### Post by joelstitch on 2010-12-12
> **cipherboy_loc said:**
> A few questions:

1) What ROM are you using.
2) Does the ROM file work on other computer?
3) Does it happen with other ROMS on the same computer?
4) Have you tried this ROM in a different emulator?


Thanks,
Cipherboy

Its happening with all the ROMS. I dont know if it works on other computers but it was working fine on mine a few days ago. I even try openning a game that I finished a few days ago and it wont open. I havent tried another emulator cause I dont know another one for Ubuntu.

---

### Post by joelstitch on 2010-12-13
So I guess the problem was that the game was loading into a new lever, so the screen went black but after a bit it came back on the next level.

---

### Post by joelstitch on 2010-12-13
I am still unable to open a most of the ROMS...

---

### Post by joelstitch on 2010-12-13
Here's what I get on the terminal when I try to open another ROM that wont open:

> |  \/  |_   _ _ __   ___ _ __  / /_ | || | |  _ \| |_   _ ___ 
| |\/| | | | | '_ \ / _ \ '_ \| '_ \| || |_| |_) | | | | / __|  
| |  | | |_| | |_) |  __/ | | | (_) |__   _|  __/| | |_| \__ \  
|_|  |_|\__,_| .__/ \___|_| |_|\___/   |_| |_|   |_|\__,_|___/  
             |_|         [http://code.google.com/p/mupen64plus/](http://code.google.com/p/mupen64plus/)  
Version 1.5

Config Dir:  /home/pag/.config/mupen64plus/
Data Dir:  /home/pag/.local/share/mupen64plus/
Cache Dir:  /home/pag/.cache/mupen64plus/
Install Dir: /usr/share/mupen64plus/
Plugin Dir:  /usr/lib/mupen64plus/

Rescanning rom cache.
Scanning... /home/pag/Documents/Nintendo 64/
Rom cache up to date. 12 ROMs.
Compression: Uncompressed
Imagetype: .z64 (native)
Rom size: 33554432 bytes (or 32 Mb or 256 Megabits)
MD5: E03B088B6AC9E0080440EFED07C1E40F
80 37 12 40
ClockRate = f
Version: 1449
CRC: 41f2b98f b458b466
Name: Perfect Dark
Manufacturer: Nintendo
Cartridge_ID: 4450
Country: Unknown (0x145)
PC = 80001000
EEPROM type: 1
init timer!
[RiceVideo] Disabled SSE processing.
[blight's SDL input plugin]: version 0.0.10 initialized.
memory initialized
[RiceVideo] Disabled SSE processing.
[RiceVideo] Found ROM 'Perfect Dark', CRC 8fb9f24166b458b4-45
InitExternalTextures
Texture loading option is enabledFinding all hires texturesInitializing OpenGL Device Context
(II) Initializing SDL video subsystem...
(II) Getting video info...
(II) Setting video mode 1024x768...
NVIDIA Corporation - GeForce 7150M / nForce 630M/PCI/SSE2 : 2.1.2 NVIDIA 195.36.24
[RiceVideo] OpenGL Combiner: Fragment Program
[JttL's SDL Audio plugin] version 1.5 initalizing.
[JttL's SDL Audio plugin] Initializing SDL audio subsystem...
[JttL's SDL Audio plugin] Allocating memory for audio buffer: 65536 bytes.
[blight's SDL input plugin]: Couldn't open joystick for controller #0: There are 0 joysticks available
Starting r4300 emulator
R4300 Core mode: Dynamic Recompiler
R4300 core: starting 64-bit dynamic recompiler at: 0x32a6200.
PC->addr < last_addr
PC->addr < last_addr


---


---
title: "laptop brightness too high for me on minimum"
date: 2010-09-24
forum: General Help
---

### Post by mackereeno on 2010-09-24
Hi I have ubuntu 10.04 installed on a Toshiba A210 Satellite notebook.(dual boot with vista)
The f6 and f7 keys work fine for altering the screen brightness but the minimum brightness is not as low as I can get it in vista which causes me a problem during the evenings.

Is there any method I can use to reduce the minimum brightness in Ubuntu 10.04?

I am willing to try all command line options.

Thanks

---

### Post by robsoles on 2010-09-25
Welcome to UF.

Please don't rush into executing commands in terminal.

Maybe a dark theme with a little tweaking can do it for you. Please right click an empty part of your desktop and choose 'Change Desktop _B_ackground' from the list of choices presented and then go through the window that opens very thoroughly.

You should be able to set page backgrounds that are usually 'white' to 'grayish' or whatever dark color you like better than bright white.

---

### Post by kleskjr on 2010-09-25
and if you decide to use the terminal, here is what I use sometimes:
```
sudo -s
echo -n 1 > /proc/acpi/video/VID/LCD0/brightness
```
this command simply writes the value 1 into the *brightness* file.
You might check whether your file has the same path (it's possible that the part ../VID/LCD0/... could be different in your system)

---

### Post by mackereeno on 2010-09-25
Thanks for the suggestions guys. 

The command line option didn't work on my system - the path didn't exist - so i'll investigate what path is used on my system.

Meanwhile i tried the change desktop back ground route and have a slightly easier on the eyes set up. This also made me experiment with the background settings in Firefox (this is a real killer for my eyes during the evening) and I have a more usable set up now.

I'm really straining on the leash for command line use :) as it reminds me of my BASIC days on the Acorn Atom. Ubuntu linux has injected much excitement for me back into the use of computers - top of the xmas present list this year will be a bash scripting how to book.

---

### Post by robsoles on 2010-09-25
A simple enough tip I can give you about the command line in terminal is that if someone tells you to 'sudo' something to your system there is no harm in popping their command into Google and make sure there aren't strong warnings against doing it in the results.

Take it easy but certainly do give it a bash :)

---


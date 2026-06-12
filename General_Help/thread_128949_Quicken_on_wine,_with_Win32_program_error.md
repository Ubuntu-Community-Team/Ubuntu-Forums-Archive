---
title: "Quicken on wine, with Win32 program error"
date: 2006-02-12
forum: General Help
---

### Post by Yleeyas on 2006-02-12
Hello folks,

I just installed wine (v.9.7) to run QuickenXG (Canadian version of 2003).

The Quicken install/setup ran with lots of 'info/errors'. There was some setup dialog, at one point it asked if I wanted to install IE, but I said no. It kept going despite lots more  printout to the terminal. Nothing looked fatal so I pressed on.

When I ran Q from a terminal window, it fires up and gives me an 'Activate Quicken' popup at which I enter my installation key. There's some info saying that to complete the installation Q will try to contact Intuit via internet or tell me to phone them. I press OK

A second popup 'Quicken Internet Features' tells me that Q will now detect how to connect to internet. I press continue and end of story.

The following error is on the terminal widow behind these popups.

$ wine "C:\Program Files\Quicken\qw.exe"
err:virtual:map_image Image was mapped at 0x7b360000: standard load address for a Win32 program (0x00400000) not available
err:virtual:map_image Do you have exec-shield or prelink active?
fixme:wininet:INET_QueryOptionHelper Stub! 40

Any ideas what I can do???  :( 
It came so close to running. :rolleyes: 

Yleeyas

---

### Post by dcstar on 2006-02-12
[QUOTE=Yleeyas]Hello folks,

I just installed wine (v.9.7) to run QuickenXG (Canadian version of 2003).

The Quicken install/setup ran with lots of 'info/errors'. There was some setup dialog, at one point it asked if I wanted to install IE, but I said no. It kept going despite lots more  printout to the terminal. Nothing looked fatal so I pressed on.
.......[/QUOTE]
Search for the "winetools" utility and install that (which will allow you to install IE and lots of other Windows goodies),  or try this:

[http://www.tatanka.com.br/ies4linux/](http://www.tatanka.com.br/ies4linux/)

You may need to re-install Quicken after you get IE working.

---

### Post by Yleeyas on 2006-02-12
Hi dcstar,

Thanx for the pointer, I'll followup after my nap :-D 

Yleeyas

---


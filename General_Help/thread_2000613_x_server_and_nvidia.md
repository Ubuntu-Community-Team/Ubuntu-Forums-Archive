---
title: "x server and nvidia"
date: 2012-06-09
forum: General Help
---

### Post by deadpixel23 on 2012-06-09
Hello, so I'm new to Linux/Ubuntu and I'm about to pull my hair out.

I've got an old Nvidia card in my system that Ubuntu didn't like right away (Gforce MX 4000) so I've downloaded the driver from Nvidia but when I try to run it it tells me that x-server needs to be off. When I disable x-server (sudo service lightdm stop) I get a black screen with text that hangs at something about battery levels.

From the research I've done this seems to be an error to do with faulty video drivers. The problem is, I need x server off to fix the driver issue.


BONUS ISSUE:
As a bonus I keep getting a weird issue where, when typing Ubuntu becomes unresponsive to keystrokes and right clicks. I find I can get control back by pretty much mashing my numpad keys. When I gain control a icon appears at the top right of the screen, seen in the attached screenshot, I'd really like to fix this because it happens sporadicly.

Thanks for any and all help!!

---

### Post by deadpixel23 on 2012-06-10
Update:

Got a hack to allow me to install custom Nvidia 96 drivers. But now when loading into Ubuntu I get "Starting LightDM Display Manager [fail]"

I've uninstalled and reinstalled LightDM with no luck.

---


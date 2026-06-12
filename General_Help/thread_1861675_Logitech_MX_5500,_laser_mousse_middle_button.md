---
title: "Logitech MX 5500, laser mousse middle button"
date: 2011-10-15
forum: General Help
---

### Post by jonsmirl on 2011-10-15
The Logitech MX 5500 is programmable from a Windows app. The default behavior of the middle button is not recognized by Ubuntu unless I reprogram it using the windows app. Every time I forget to charge the mouse I have to boot windows to reprogram it.

The hidraw message for the middle button when programmed is:
0000150 0402 0000 0000 0000 0002 0000 0000 0000

Without being programmed the message is:
00003f0 0002 0000 0000 0000 0002 0000 0000 0000

So when the mouse is programmed the middle button is button 4? And when it isn't programmed it is button 0?

Is there some way to tell X that the middle button is button 0 instead of button 4?

---

### Post by HarcourtMarketing on 2011-10-15
> **jonsmirl said:**
> The Logitech MX 5500 is programmable from a Windows app. The default behavior of the middle button is not recognized by Ubuntu unless I reprogram it using the windows app. Every time I forget to charge the mouse I have to boot windows to reprogram it.

The hidraw message for the middle button when programmed is:
0000150 0402 0000 0000 0000 0002 0000 0000 0000

Without being programmed the message is:
00003f0 0002 0000 0000 0000 0002 0000 0000 0000

So when the mouse is programmed the middle button is button 4? And when it isn't programmed it is button 0?

Is there some way to tell X that the middle button is button 0 instead of button 4?

Now I wish I got a half rack instead of six pack.

---


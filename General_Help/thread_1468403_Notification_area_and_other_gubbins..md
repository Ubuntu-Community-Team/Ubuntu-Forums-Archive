---
title: "Notification area and other gubbins."
date: 2010-05-01
forum: General Help
---

### Post by Berk on 2010-05-01
So, I upgraded to 10.04 overnight, logged back in and found I had some sort of keyboard manager on my panel. So I removed it, then wondered why I didn't have a network notifier on my panel. 
After trying a few random things it seems they're all linked to the notification area, so I have my network notifications back, but I'm now stuck with a keyboard switcher and universal access button. How can I get rid of what I don't need?
In a similar vein, where has my volume indicator gone?

---

### Post by Berk on 2010-05-02
Any ideas anybody, any quick links to an already solved thread I've been unable to find?

---

### Post by sunk8 on 2010-05-02
Go to System >> Preferences >> Keyboard.
Uncheck the 'Accessibility features can be toggled with keyboard shortcuts.'

Tell me if that solves the issue...

---

### Post by Berk on 2010-05-02
Thank you, that got rid of the Universal Access button, and a stab in the dark at removing USA from the list of layouts got rid of the keyboard switcher.
Thank you for the guidance.
Any ideas on how to get a volume button back?

---

### Post by Elfy on 2010-05-02
I think the volume button is in Indicator Applet - you then have the envelope thing as well - if you don't want that then remove the indicator-messages package - restart the panel or it will be there till a reboot/logout from memory.

---

### Post by Berk on 2010-05-02
Thank you, that got me the volume notification back, removing the indicator-me package got rid of that IM style notification bit, which saves me hunting for that. I still have the envelope though.

---

### Post by sunk8 on 2010-05-02
> **Berk said:**
> Thank you, that got me the volume notification back, removing the indicator-me package got rid of that IM style notification bit, which saves me hunting for that. I still have the envelope though.

To remove the envelope, remove the package *indicator-messages*.

---

### Post by Berk on 2010-05-02
Hot stuff, thank you.

---

### Post by Elfy on 2010-05-02
> **sunk8 said:**
> To remove the envelope, remove the package *indicator-messages*.

Thought I'd removed indicator-me :) - and now I read Berk's post I realised why I did that too :)

Edited above post now ...

---


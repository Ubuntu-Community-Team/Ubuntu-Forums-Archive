---
title: "Sound Icon Gone Missing"
date: 2011-02-06
forum: General Help
---

### Post by sillywindows on 2011-02-06
Hi Guys,

I got rid off Empathy off my toolbar and it has taken away the sound icon aswell. How do I get the sound icon back? I am using Ubuntu 10.10.

Thanks in advance ;)

---

### Post by tea for one on 2011-02-06
Good morning

Right click top panel
Select "Add to panel"
Scroll down and select "Indicator Applet"
Click "Add"
Close

It should be there now

---

### Post by sillywindows on 2011-02-06
> **tea for one said:**
> Good morning

Right click top panel
Select "Add to panel"
Scroll down and select "Indicator Applet"
Click "Add"
Close

It should be there now
Thank You Thank You Thank You! It seems far more spaced, how do I decrease the space between the icons?

---

### Post by tea for one on 2011-02-06
Right click icon
If "Lock to Panel" is ticked, then remove tick
Right click and select "Move"

Then you have to decide whether you wish to "Lock to Panel" 

Just a further thought:-

If you want to keep the sound icon and remove the envelope icon, you have to enter the following command in the terminal followed by your password.

```
sudo apt-get remove indicator-messages
```

Then, log out and log in again and you should have a sound icon without the envelope icon.

---

### Post by sillywindows on 2011-02-06
I know about the move option but that doesn't change the spacing between them, it only changes the order.

---

### Post by tea for one on 2011-02-06
I am a little perplexed when you say the "Move" option does not alter the spacing between icons on the panel.

As a suggestion, you could create a brand new panel (without removing your existing panels) and then add and remove various applets to see how they all interact with each other.

For example, some applets have only one function wile the indicator applets have multi functions that seem to misbehave on occasions if different themes are used.

I have installed the Gion icons from Gnome Art and I get a different menu with the Shutdown icon when compared to the Shutdown menu if the default Ambiance theme is being used.

I find that Themes, Panels, Icons and Applets are not completely intuitive.

---


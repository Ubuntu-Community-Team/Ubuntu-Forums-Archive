---
title: "How to Restore Missing Volume Button to System Tray After Upgrade?"
date: 2011-01-02
forum: General Help
---

### Post by Its_Rishi on 2011-01-02
I'am Using UBUNTU 10.10 version i upgraded my os then the volume control button on system tray and the previous "Indicator Applet" were gone. Now i added the volume control button by adding "Indicator Applet" from Add to Panel option at tray.
But i also tried the following:

"Use Alt+F2 to open the Run Application app, paste gnome-volume-control-applet into the text field, and click the Run button"

Then i had two volume control buttons after that i tried to remove the volume button which is came by the command line Not from the Indicator Applet

Next i tried the following code in terminal to remove the volume button which was came from command line:

"sudo apt-get purge indicator-sound"

But the wrong thing is the volume button on Indicator Applet was gone :(

I also add the indicator applet but the volume button doesn't coming back with the applet

Now i want the Original Volume button along with the applet Not the other button

So, please anybody help me out here!!!

---

### Post by SnickerSnack on 2011-01-02
> **Its_Rishi said:**
> Next i tried the following code in terminal to remove the volume button which was came from command line:

"sudo apt-get purge indicator-sound"


This didn't just remove the applet, it uninstalled it from your computer.  Run

sudo apt-get install indicator-sound

then add it to the panel using only one of the methods you tried.

Why did you try adding it again when you already had one?

---

### Post by Its_Rishi on 2011-01-02
> **SnickerSnack said:**
> This didn't just remove the applet, it uninstalled it from your computer.  Run

sudo apt-get install indicator-sound

then add it to the panel using only one of the methods you tried.

Why did you try adding it again when you already had one?
Hey Thank you Thanks alot yaar
its done...

---

### Post by SnickerSnack on 2011-01-02
Glad to help.  Don't forget to mark the thread as SOLVED under Thread Tools (near top right corner).

---


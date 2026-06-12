---
title: "Which is the last native non-unity ubuntu?"
date: 2012-07-27
forum: General Help
---

### Post by Nixarter on 2012-07-27
Compiz is buggy on 12.04 and a few of the newer releases, and I want to put this on a laptop that I want stable.

And two... I don't think the wifi driver for my laptop will work with a version more than a year old, so how do I figure out which one I need so I can install it without internet?

---

### Post by kurt18947 on 2012-07-27
You know about Xubuntu and Lubuntu?  Neither use Unity.  I don't know how they get along with compiz though.  There's also Mint which use Cinnamon or MATE, no Unity.  There was also a version that substituted gnome-shell for Unity.  I'm not sure the status on that. 11.04 is the last release to use gnome 2 which is what I suspect you're asking about.  It will reach end-of-life in 3 months.

---

### Post by 2F4U on 2012-07-27
I would also suggest that you try Xubuntu or Lubuntu. Both come without Compiz and XFCE (Xubuntu) has an integrated solution. It is easy to try them as liveCD's, which also allows you to verify if WiFi works. If lightweight is not a necessity, you could also try Kubuntu, which uses KDE as its desktop environment.

---

### Post by Ralph L on 2012-07-27
I think the last one without unity was Mavrick. 

I am in the process of ugrading and after a lot of study and trial and error I stuck with ubuntu 12.04.  I have got it running pretty well without unitiy.  I installed gnome-panel and am running Classic (no effects). 

Here are couple excerpts from my notes that I was keeping for friend:  (Note that I have a Broadcom 4318 wireless chipset.)

 16  If wired Ethernet is available make sure it is plugged in and proceed.  If no Ethernet is available then b43-fwcutter and b43 firmware can be downloaded on a Windows (or other) computer and moved by by memory stick to ubuntu.  Alternatively b43-fwcutter can installed from the installation CD or memory stick, but the drivers/firmware must be downloaded from linux repositories.  
 16.1  [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx) describes how to install b43 firmware without Internet access from the Live CD and from linux repositories that contain the Broadcom drivers/firmware.
 16.2  Skip the next step if b43 was loaded in this step as shown above.
 17  Find and bring up the Ubuntu Software Center from the menu on the left side of the screen.  In the Search box type in b43 and install it.  
 17.1  It is also possible to use Synaptic to install b43 firmware.  In this is desired go to the Dashboard, type in Synaptic, and install it.  Then bring up Synaptic from the Dashboard and install the b43 firmware.
 18  After waiting a few minutes it should be possible to select a wifi using the icon on the top panel.  Type in the password and wifi should work.

 20  Install gnome-panel or gnome-session-fallback using either the Ubuntu Software Center or Synaptic.  I installed gnome-panel and, along with a large number of other packages, it also installed gnome-session-fallback.  I also tried selecting gnome-session-fallback using Synaptic, and it installed gnome-panel among other items.  Restart, then logout and at login time click the icon on the login panel to select what Classic (no effects) or just Classic.
 21  Install gnome-tweak-tool.  It appears in Main menu>Applications>System Tools>Preferences as Advanced Settings.
 22  Install dconf Editor (dconf-tools) using either Synaptic or Ubuntu Software Center.
 22.1  There is also an older version of dconf available on Synaptic.  Package Properties shows that it conflicts with dconf-tools so I didn't install it.
 23  Disable the overlay scrollbars by one of several methods.
 23.1  Go to Main menu>Applications>System Tools>dconf Editor.  In dconf Editor go to org>gnome>desktop>interfaces and uncheck ubuntu-overlay-scrollbars.  Note:  This method did not completely work.  I am going to have to use one of the other methods below--probably uninstall the overyay-scrollbar, etc.
 23.2  In Terminal enter &#8220;gsettings set org.gnome.desktop.interface ubuntu-overlay-scrollbars false&#8221;.
 23.3  Add the line &#8220;export LIBOVERLAY_SCROLLBAR=0&#8221; (no quotes) to the file ~/.xprofile (create one, if it doesn't exist).
 23.4  For globally disabling scrollbars Create a file /etc/X11/Xsession.d/99disable-overlay-scrollbars and add  &#8220;export LIBOVERLAY_SCROLLBAR=0&#8221; (no quotes) to the file
 23.5  Uninstall overlay-scrollbar, liboverlay-scrollbar-0.2-0, and liboverlay-scrollbar3-0.2-0 using synaptic.
 24  Install Clearlooks Phenix theme from  [http://gnome-look.org/content/show.php?content=145210](http://gnome-look.org/content/show.php?content=145210) .
 24.1  Determine if you have GTK 3.0, GTK 3.2 (use Clearlooks-Phenix 1),or GTK 3.4 or newer (use Clearlooks-Phenix 2).   If you use a Gnome application (gedit, Nautilus, File Roller, Evince, etc.), you can open it and go to Help > About. For example, if you have gedit 3.2.3, then you have GTK 3.2.  I have GTK 3.4 so I use Clearlooks-Phenix 2.
 24.2  For Clearlooks-Phenix 2 the following packages are needed:  packages gtk2-engines (if GTK2 applications are used), gnome-themes-standard and gtk3-engines-unico.  Check in Synaptic for these.
 24.3  Readme in the Clearlooks-Phenix 2 download describes how to install it.
 24.3.1  Change the name of the extracted folder to Clearlooks-Phenix.
 24.3.2  Copy the Clearlooks-Phenix folder to /usr/share/themes.
 24.4  Bring up System Tools>Preferences>Advanced Settings, set GTK+ theme to Clearlooks-Phenix, Windows theme to Clearlooks-Phenix and Icon theme to Ubuntu-mono-light (or whatever you like).
 25  Clearlooks-Phenix restores the stepper arrows if standard scrollbars are restored (as we did above).  However, if you choose another theme, it is still possible to restore the stepper arrows (classic scrollbars must have been previously restored):
 25.1  To restore the stepper arrows put the following in the ~/.gtkrc-2.0 file ([http://askubuntu.com/questions/34214/how-do-i-disable-overlay-scrollbars](http://askubuntu.com/questions/34214/how-do-i-disable-overlay-scrollbars)) :
style "default" {
engine "murrine" {
stepperstyle = 0
}
}
 25.2  and the following into the file ~/.config/gtk-3.0/gtk.css:
scrollbar {
-GtkScrollbar-has-backward-stepper: 1;
-GtkScrollbar-has-forward-stepper: 1;
}

---

### Post by Nixarter on 2012-07-27
Thank you all for your suggestions.  I have already tried both Lubuntu and Xubuntu.  They were both great, but I couldn't get compiz to function properly.  It still felt like it was a bit buggy and didn't quite belong.

Also, thanks for the info on compiz with 12.04.  I have another 12.04 install that I am keeping on another computer, and I will check my notes with those to see if there is anything else I can do for it on there.

After the Mint suggestion, I think I will try the MATE version of Mint 13 on the computer first.  Since it has native Compiz support it looks like it may be the best option for my purpose, since I also would like gnome.  I'll update once I get everything set up and tested for a bit.

---

### Post by HiImTye on 2012-07-27
you can install GnomeShell from Ubuntu and just choose it from the menu
```
sudo apt-get install gnome-shell gnome-session-fallback
```

---


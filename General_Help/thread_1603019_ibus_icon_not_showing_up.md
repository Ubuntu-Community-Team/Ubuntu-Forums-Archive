---
title: "ibus icon not showing up"
date: 2010-10-22
forum: General Help
---

### Post by Bytesource on 2010-10-22
Hi all,

After upgrading to Kubuntu 10.10 the icon for the ibus input method is not showing up anymore.

I checked the ibus-daemon is running, but I have no idea how to use ibus without an icon.

Does anybody know how to solve this problem?

---

### Post by kumaryu on 2010-10-22
Can you access Ibus Preferences?

 “System” > “Preferences” > “IBus Preferences” (Keyboard Input Methods).

In Ibus preferences, there are options for:

Show language Panel
Show Icon on System Tray

---

### Post by Bytesource on 2010-10-22
Yes, I can access the IBus preferences:

*Show icon on system tray* is marked
*Show language panel* is set to *always*

These settings, therefore, do not seem to be the source of the problem.

---

### Post by kumaryu on 2010-10-22
Ibus switching icon normally resides in the "System Tray" which in turn is located on the "Panel".

Is it possible your "System Tray" isn't on your Panel? If so, you should be able to add by right-clicking on the Panel..

---

### Post by Bytesource on 2010-10-22
My system tray is in the panel showing other icons. 

The ibus icon is also not listed as an entry of the system tray.

---

### Post by kumaryu on 2010-10-22
I've just tested this using a clean installation of Kubuntu 10.10. Ibus (1.3.7) was obtained by installing the Japanese input module (Anthy) from "Locale" (Country/Region & Language) settings.

1. Immediately following the installation, Ibus icon was visible on the Panel but not in the System Tray. ie Its a Panel applet.

2. Opening the "Keyboard Input Methods" (IBuse Preferences) controls has the effect of making the Ibus icon on the Panel disappear.

3. Toggling the "Show icon in system tray" option does not restore the icon on the Panel.

4. The "Show language panel -Always-" option also does not appear to have any effect on invoking the floating language bar on the Desktop.

5. The only method found of restoring the IBus icon on the Panel was to restart the computer (Restarting the session had  no effect) after every mode change on "Show icon in system tray" option. This means that following a loss of the icon on the invocation of IBus Prefs, two restarts are required to bring it back.

I think this may be a bug with IBus (1.3.7) and Kubuntu (10.10). This document appears to indicate that some changes were afoot in Kubuntu 10.10 for IBus.
[https://wiki.kubuntu.org/KeyboardSettings?action=show&redirect=KeyboardMenu](https://wiki.kubuntu.org/KeyboardSettings?action=show&redirect=KeyboardMenu)

I'm using IBus 1.3.7 (w/ Anthy) on Ubuntu Maverick (10.10) with no issues. If you have no other dependencies, it may be an idea to use Ubuntu until they sort this out.

---

### Post by Bytesource on 2010-10-22
I cannot switch to Ubuntu right know. Therefore I have to keep looking for a solution to the icon problem.

---

### Post by Bytesource on 2010-10-23
I finally managed to solve the problem.

I removed *ibus-qt4* and installed *ibus-gtk*. 

Then I killed *ibus-daemon* and restarted ibus.

Now I have the ibus icon back in the system tree!

By the way, if ibus only works with some applications or always shows *no input window* you can try the following instructions using the *kalternatives* program:

[https://bugs.launchpad.net/ubuntu/+source/ibus/+bug/522814/comments/5](https://bugs.launchpad.net/ubuntu/+source/ibus/+bug/522814/comments/5)

Stefan

---

### Post by kumaryu on 2010-10-23
I tried your solution (of replacing ibus-qt4 with ibus-gtk). On reboot, IBus displayed both the icon on the Panel as well as the floating language bar on the desktop.

As soon as IBus Preferences were invoked however, they both disappeared. The only way to restore them was to reboot the computer.

---

### Post by Bytesource on 2010-10-23
> **kumaryu said:**
> I tried your solution (of replacing ibus-qt4 with ibus-gtk). On reboot, IBus displayed both the icon on the Panel as well as the floating language bar on the desktop.

As soon as IBus Preferences were invoked however, they both disappeared. The only way to restore them was to reboot the computer.

That did not happen in my case. 

The ibus icon not showing up is really an annoying issue, especially if you depend on non-English input.

---

### Post by ambeginnersearchinginfo on 2010-10-27
Sorry, I have a couple of basic questions.
In Kubuntu 10.04 in the KDE I click the first botton left  and then I find system settings.
Clicking on that leads to a window with a variaty of options, where I can click languages.
Then I can chose between keyboard layouts and the menue for selecting the system language. But I don't understand, where exactly the ibus should show up. Could you please describe, where exactly where the ibus is. Thank you very much. 
Sorry for not understanding.
Is panel the very bottom of the screen also called task bar
and the system tray its right side also called notification area?
What is the language Panel? Is it where is written EN for English and KO for Korean and so on, where you can click on it and switch between maximum four languages?
What is *ibus-qt4* and [I]ibus-gtk.

[/I]I use Mozilla and I read that iibus-gtk is used by Mozilla.
Do I have to download it and from where?
I searched on Ibus page but didn't find it.
But there I found a ibus-hangul, what does this mean?
It says:<<
It is a Korean input engine for IBus.>>

---

### Post by ambeginnersearchinginfo on 2010-10-27
erased, I don't how to erase. 
It was written doubel.

---

### Post by Bytesource on 2010-10-27
Let me try to answer some of your questions.

The Ibus icon should appear in the system tray which is located at the bottom right of the screen. You will also find the language switch icon there.

To be able to switch between four different languages, you first have to add these languages in the system settings:
System Settings -> Locale -> Country/Region & Language: Add Language

ibus-gtk is normally used in a GNOME deskop enviroment (which Ubuntu uses).
ibus-qt4 is normally used in a KDE desktop enviroment (which Kubuntu uses).
Although ibus-qt4 gets automatically installed on Kubuntu when installing ibus, I replaced it with ibus-gtk because I found out that (at least in my case) the Ibus icon appeared in the stystem when using ibus-gtk.

To remove ibus-qt4 you type the following at a terminal (the terminal used in Kubuntu is called *Konsole*):
```
sudo apt-get remove ibus-qt4
```

After that you can install ibus-gtk:
```
sudo apt-get install ibus-gtk
```

Please let me know if you have any further questions.

Stefan

---

### Post by ambeginnersearchinginfo on 2010-11-10
Thank you very much for your information!
There is a search function in Kubuntu, one time search for ibus and indeed Kubuntu found it.
But I changed to Ubuntu because I couldn't get Kubuntu to run.
Only problems, loading the missing languages packages got all the time stuck and didn't finished the loading process or the display turned black and the system was stuck or no ibus or or or... And everything very timeconsuming!
According to the advice of another user in this forum I changed to ubuntu.
I found a post explaining in detail how to get the language keygoard layouts.
The layouts I tried so far are working, so now I can begin to write,
but it is annoying changing the keyboard layout because of a limitation of four languages built in the system.
So I was adviced to make up a launcher for every language and got an explanation how to do it. So I could get launcher icons on the top panel and could indeed switch the languages by clicking on them.
But I am new to ubuntu and I don't know the most basic things.
Everytime I ask a question I get sample commands for the terminal.
But I couldn't find out: Where is the documentation of all commands avallable in Ubuntu? In the meanwhile I found a post with some information where to find some documentation:

[http://ubuntuforums.org/showthread.php?t=1495316](http://ubuntuforums.org/showthread.php?t=1495316)

And the next problem is: How can I find out whether or not there is a terminal command for a certain action?
You see I want just to do a very easy thing, I just want to answer my e-mails and for that I need to change the language keyboard layouts all the time and that leads to a very complex and complicated installation by far to difficult for a beginner like me.
And now I know how to get launcher icons on the panel but they look all the same.
So I would like to have icons which consists of two or tree letter combinations like US for English. But I don't know how to convert a string into an icon.
And then I would like to have a notificaton which language keyboard layout is active.
But I don't know by which terminal command I can put an icon into the notificatin area.
My idea would be to add this command to every launcher sending the icon of its own launcher into the notification area. If I would click on US then the us keyboard layout gets activated and in the notification area appears the icon for Us and so on.
But I couldn't find information about this question yet.

Maybe I open another specific tread about it.

---


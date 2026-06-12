---
title: "New to Kubuntu - a few newbie questions"
date: 2011-10-26
forum: General Help
---

### Post by Annorax on 2011-10-26
Hi all,

I've recently installed Kubuntu 11.10 successfully and things work well. I do have a few small, unrelated questions about a few random things:

1.) Before going to 11.10, I was using version 11.04. I did not do an upgrade but a fresh install. I'm now seeing an odd, intermittent issue in that when using the default KDE task bar, sometimes when I close an application, it stays in the task bar until I click the KDE Application Launcher. I did not notice this in 11.04. Is this a known issue or something funky specific to me?

2.) In Firefox, I am coming from Windows where the Backspace button would go back one page in history in the current tab. In Kubuntu this doesn't happen, even when the focus is not in a text box. Is there any way to make this work?

3.) Again coming from Windows, I like that each program I launch (or most of them) remember their window's size and position. But in KDE this is not the case. I need to go to the Special Window Settings popup manually for each window and set it to remember the size and position. Is there any way to have it do this automatically for each new program?

4.) Is there any way to hide the New Activity icon in the upper right corner?

5.) On Windows I like to use portable applications, ie applications that do not write to the registry or any place on your computer except their own folder. On Linux I don't see anything like that as programs seem to install in many places (Filezilla for example). Are there portable apps for Linux? What are the 'standard' places that Linux programs get installed to? In Windows I know it's Program Files.

6.) Is there any way to get program icons (ie for Firefox, Konsole) to the direct right of the KDE Application Launcher? I was able to do this in 11.04 but when trying to drag and drop icons there, they don't stick. I can get them to the left of the clock but not to the right of the Application Launcher.

Thanks for any help. :)

---

### Post by dniMretsaM on 2011-10-26
> **Annorax said:**
> 1.) Before going to 11.10, I was using version 11.04. I did not do an upgrade but a fresh install. I'm now seeing an odd, intermittent issue in that when using the default KDE task bar, sometimes when I close an application, it stays in the task bar until I click the KDE Application Launcher. I did not notice this in 11.04. Is this a known issue or something funky specific to me?

Known issue in KDE 4.7.x. Opening Kickoff removes the offending apps from the task bar I believe.

> **Annorax said:**
> 2.) In Firefox, I am coming from Windows where the Backspace button  would go back one page in history in the current tab. In Kubuntu this  doesn't happen, even when the focus is not in a text box. Is there any  way to make this work?

Shift+scroll down on middle mouse button is th e default shortcut for this, but I honestly don't know how to change it. Try asking on the [FF mega thread]("http://ubuntuforums.org/showthread.php?t=1712247").

> **Annorax said:**
> 3.) Again coming from Windows, I like that each program I launch (or most of them) remember their window's size and position. But in KDE this is not the case. I need to go to the Special Window Settings popup manually for each window and set it to remember the size and position. Is there any way to have it do this automatically for each new program?

In my experience, windows do retain their size. Perhaps you accidentally changed some setting.

> **Annorax said:**
> 4.) Is there any way to hide the New Activity icon in the upper right corner?

Yes, but I don't know exactly how (I've only ever done it by accident).

> **Annorax said:**
> 5.) On Windows I like to use portable applications, ie applications that do not write to the registry or any place on your computer except their own folder. On Linux I don't see anything like that as programs seem to install in many places (Filezilla for example). Are there portable apps for Linux? What are the 'standard' places that Linux programs get installed to? In Windows I know it's Program Files.

Applications are installed in /usr/bin/. For portable apps, check out [PortableLinuxApps]("http://portablelinuxapps.org/").

> **Annorax said:**
> 6.) Is there any way to get program icons (ie for Firefox, Konsole) to the direct right of the KDE Application Launcher? I was able to do this in 11.04 but when trying to drag and drop icons there, they don't stick. I can get them to the left of the clock but not to the right of the Application Launcher.

You should be able to do this. Try moving Kickoff to the left instead of moving the icons to the right.

---

### Post by Tristan_F on 2011-10-30
4) I'd like to know also how to remove that tab!

6) You can add the "Quick Launch" plasmoid next to your kickoff menu and add applications launcher there afterwards

---

### Post by StephanG on 2011-10-30
> **Annorax said:**
> Hi all,

3.) Again coming from Windows, I like that each program I launch (or most of them) remember their window's size and position. But in KDE this is not the case. I need to go to the Special Window Settings popup manually for each window and set it to remember the size and position. Is there any way to have it do this automatically for each new program?


KDE does remember the size and position of windows.  It just doesn't remember the size and position if you change it by dragging it into one of the corners or sides of the screen.

When you drag a window into the corner, it automatically resizes it to take up a quarter of your desktop.  If you drag it away, it goes back to the size that it "remembers".  I also find it annoying, but I guess the KDE devs figured that it's easy enough to drag it back into the side/corner if you want it that size.

---

### Post by slooksterpsv on 2011-10-30
You can press ALT+LEFT ARROW KEY to go back a page. That's how I always do it. Backspace rarely works as I'm usually on pages with forms where it thinks I'm trying to clear the form vs going back a page.

---

### Post by SeijiSensei on 2011-10-30
> 5.) On Windows I like to use portable applications, ie applications that do not write to the registry or any place on your computer except their own folder. On Linux I don't see anything like that as programs seem to install in many places (Filezilla for example). Are there portable apps for Linux? What are the 'standard' places that Linux programs get installed to? In Windows I know it's Program Files.

I actually think it's Windows that scatters configuration files across the machine.

In Linux, most programs are stored in /usr/bin.  Their system-wide configuration files, if any, are stored in /etc, often in /etc/programname.

However the files you're concerned about like those related to Firefox are all stored in your home directory, /home/username.  Most of these settings reside in so-called "hidden" files or directories, ones whose names begin with a dot.  Firefox, for instance, stores all its configuration information in /home/user/.mozilla/firefox.  That actually makes upgrading and migrating rather easy since you generally need only copy the /home directory tree to preserve all the users settings.

---

### Post by mykes on 2011-10-31
No matter what I've tried, Kate opens a window that's so small I can only see 6 lines of text in the editor).  I can resize it fine.  I configure it to use the last session and save a session with window parameters and it still opens small.  I can open the session from the menu and it goes to the proper size.

---

### Post by dniMretsaM on 2011-11-02
Try this for the "New Activity" icon:
[QUOTE=CryptoPaul]...[U]nlock widgets, you are then able to drag it to the  extreme top right, where upon it turns into a far less intrusive quarter  circle icon.[/QUOTE]

---


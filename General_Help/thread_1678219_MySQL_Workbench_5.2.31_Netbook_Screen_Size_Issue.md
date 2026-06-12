---
title: "MySQL Workbench 5.2.31 Netbook Screen Size Issue:"
date: 2011-01-30
forum: General Help
---

### Post by jgcamp99 on 2011-01-30
OK, I have a solution for those that want to use MySQL Workbench on a 1024 x 600 Netbook screen.

1. After enabling root to login (or maybe someone can try this using SUDO), modify permissions for RW capability to this file for groups & users:

/usr/share/mysql-workbench/wb.glade

After doing this, you can open that file with your text editor and make changes and save the file.

2. Open wb.glade with your text editor.

3. Locate this area/lines of code in the text editor (it won't be hard, because it's at the start of the file:

<?xml version="1.0"?>
<glade-interface>
  <!-- interface-requires gtk+ 2.6 -->
  <!-- interface-naming-policy toplevel-contextual -->
  <widget class="GtkWindow" id="wb_main_window">
    <property name="width_request">1024</property>
    <property name="height_request">680</property>
    <property name="window_position">center</property>
    <property name="default_width">1024</property>
    <property name="default_height">720</property>
    <child>

4. The resolutions of 1024 & 680 and 1024 & 720 are the items you can change to your preferences.

5. For my MSI Wind U-100, logged in as a user in Desktop mode, I found changing the settings to 1024 & 520 for both settings and saving the file works for the Gnome Desktop. For a user logged in Netbook mode, I found 950 & 540 fits the screen perfectly (see sample code below).

<?xml version="1.0"?>
<glade-interface>
  <!-- interface-requires gtk+ 2.6 -->
  <!-- interface-naming-policy toplevel-contextual -->
  <widget class="GtkWindow" id="wb_main_window">
    <property name="width_request">950</property>
    <property name="height_request">540</property>
    <property name="window_position">center</property>
    <property name="default_width">950</property>
    <property name="default_height">540</property>
    <child>

Tips: When MySQL Workbench starts and displays the Welcome screen, the first thing you want to do is minimize the "Workbench Central" area. This is easy too, because MySQL has a downward triangle to the left of the words "Workbench Central" that you can click on with your mouse. Once that is minimized, any Existing Open Connections, EER Models and Server Administration connections will be displayed and as you create new ones, they will display and populate too.

Also, I've found when you go less than 1024 for the code that was 1024, there will be negligible truncation to selections, but they are intuitive and readably understandable. Even more important, clicking on those buttons there is no loss of functionality.

MySQL Workbench 5.2.31 is now fully functional on a 1024 x 600 netbook and DBA's can use it instead of the old school gui tools, which still work as well on a netbook display with full functionality and no loss of page.

---

### Post by jgcamp99 on 2011-01-30
Screenshots:

---

### Post by jgcamp99 on 2011-01-30
More screenshots:

---

### Post by jgcamp99 on 2011-01-30
And since everybody loves modeling:

---

### Post by jgcamp99 on 2011-01-31
More about Ubuntu's Netbook Edition, when Unity gets the autohide feature for the Launcher in 11.04, that 1024 resolution spec won't need to be changed to 950 and that should eliminate any horizontal truncation. Short of resizing icons, moving page layouts & other tweaks to optimize Workbench for a 1024 x 600 screen, this will have to do, not that it's that bad. Going from 680 or 720 to 540 for those resolution specs are a 25.9% (680) & 33.3% (720) scaling penalty vertically, and if there were a way to autohide the top menu bar, it would even be less.

---

### Post by jgcamp99 on 2011-02-01
Premature on fully functional, the two items I've found that are blind tab keystrokes to continue thru a progression of screens that don't fit are in Server Administration section to the far right of the Welcome page. Specifically, "New Server Instance" and "Manage server Instances". The "cancel", "back" & "next" buttons. 

Edit: The workaround for this at this point is to setup whatever instances you will need to connect to while the netbook is in a dual monitor mode. Linux has a monitor utility that manages this and a 15" 1024 x 768 resolution monitor will work for setting up saved instances that you will need to connect to later using the new instance connection wizard. Monitors are "unmirrored", that way the monitor can be 1024 x 768 resolution, while the netbook display can remain 1024 x 600 resolution. Otherwise as "mirrored", both the monitor & netbook screen are dialed in at 800 x 600, which is the best common resolution that both displays have in common. The monitor is the default display and the netbook screen is just a blank extension of that desktop at the lower resolution. MySQL Workbench (WB) can be opened and preconfigured, later used as a stand alone netbook once WB is used disconnected from the monitor. I'd say with the original solution, 90-95% of WB gets a fully functional & appearance rating. With the workaround, I'd rate it a 97-99% fully functional appearance rating. LOL, that 1-3 % is my CMA (cover my @**), because we all know that as soon as I give this a 100% fully functional & appearance rating, there's going to be something I or another finds that will make me a liar. I can't vouch for what happens with additional plugins installed as well, but with what downloads as MySQL's developed & maintained Workbench Community Edition product works as described in this thread.

---

### Post by FB91 on 2011-06-11
Thanks!!!!!!!!!! It works perfect in my netbook Dell Mini 10. (screen of 1024x600px).

Really thanks a lot!!!!

---

### Post by jgcamp99 on 2011-06-23
Awesome that this is a workable solution for other IT MySQL database professionals worldwide & still works for subsequent releases of MySQL Workbench 5.2.32, 5.2.33 & 5.2.34. I just updated to 5.2.34 and tested it. :popcorn: :)

---

### Post by joanna_christine on 2011-10-09
> **jgcamp99 said:**
> OK, I have a solution for those that want to use MySQL Workbench on a 1024 x 600 Netbook screen.
 
1. After enabling root to login (or maybe someone can try this using SUDO), modify permissions for RW capability to this file for groups & users:
 
/usr/share/mysql-workbench/wb.glade
 
After doing this, you can open that file with your text editor and make changes and save the file.
 
2. Open wb.glade with your text editor.
 
3. Locate this area/lines of code in the text editor (it won't be hard, because it's at the start of the file:
 
<?xml version="1.0"?>
<glade-interface>
<!-- interface-requires gtk+ 2.6 -->
<!-- interface-naming-policy toplevel-contextual -->
<widget class="GtkWindow" id="wb_main_window">
<property name="width_request">1024</property>
<property name="height_request">680</property>
<property name="window_position">center</property>
<property name="default_width">1024</property>
<property name="default_height">720</property>
<child>
 
4. The resolutions of 1024 & 680 and 1024 & 720 are the items you can change to your preferences.
 
5. For my MSI Wind U-100, logged in as a user in Desktop mode, I found changing the settings to 1024 & 520 for both settings and saving the file works for the Gnome Desktop. For a user logged in Netbook mode, I found 950 & 540 fits the screen perfectly (see sample code below).
 
<?xml version="1.0"?>
<glade-interface>
<!-- interface-requires gtk+ 2.6 -->
<!-- interface-naming-policy toplevel-contextual -->
<widget class="GtkWindow" id="wb_main_window">
<property name="width_request">950</property>
<property name="height_request">540</property>
<property name="window_position">center</property>
<property name="default_width">950</property>
<property name="default_height">540</property>
<child>
 
Tips: When MySQL Workbench starts and displays the Welcome screen, the first thing you want to do is minimize the "Workbench Central" area. This is easy too, because MySQL has a downward triangle to the left of the words "Workbench Central" that you can click on with your mouse. Once that is minimized, any Existing Open Connections, EER Models and Server Administration connections will be displayed and as you create new ones, they will display and populate too.
 
Also, I've found when you go less than 1024 for the code that was 1024, there will be negligible truncation to selections, but they are intuitive and readably understandable. Even more important, clicking on those buttons there is no loss of functionality.
 
MySQL Workbench 5.2.31 is now fully functional on a 1024 x 600 netbook and DBA's can use it instead of the old school gui tools, which still work as well on a netbook display with full functionality and no loss of page.
 
 
hello, im sorry but im really really new to ubuntu, i just installed the os a while ago, and i just want to ask how to do step no. 1. I tried entering /usr/share/mysql-workbench/wb.glade but it says command not found. Thank you very much. :D

---

### Post by jgcamp99 on 2011-10-20
> **joanna_christine said:**
> hello, im sorry but im really really new to ubuntu, i just installed the os a while ago, and i just want to ask how to do step no. 1. I tried entering /usr/share/mysql-workbench/wb.glade but it says command not found. Thank you very much. :DJoanna, to enable the root account:

[http://www.ubuntugeek.com/enable-and-disable-ubuntu-root-password.html](http://www.ubuntugeek.com/enable-and-disable-ubuntu-root-password.html)

once you've done that you can log out as the user you created at installation and at the login screen,

login using the "other" user option. Type "root and press the enter key. Then the password you changed it to from the steps you did from the link above. Then it's a matter of going to the directory where the file is and right clicking it and changing the permissions tab to read & write. The you can open that file in text editor and change the code and save the file. Once you've done that you're done and then you can log out as root and login as the ubuntu user you created and normally log in as. Since Ubuntu has come out with 11.10, this still works, but Workbench has a glitch/bug in it and they need to provide a version for 11.10 for download. Sorry for the delay in response.

---


---
title: "How do I configure gdm in karmic!?"
date: 2009-12-02
forum: General Help
---

### Post by msp3k on 2009-12-02
Hi gurus,

Once upon a time I could disable the shutdown/reboot/suspend/hibernate button in gdm by merely editing /etc/gdm/gdm.conf.  But in karmic, a lot of gdm's configuration has moved to GConf, so now, apparently, I don't know how to do it.

According to the gdm manual, you can override the default system gdm settings by placing the appropriate gconf stuff in the ~gdm/ home directory (which is /var/lib/gdm/.gconf/).

My understanding is that this means the file:
/var/lib/gdm/.gconf/apps/gdm/simple-greeter/%gconf.xml

Also according to the gdm manual, you can disable the shutdown/reboot buttons by setting the GConf variable /apps/gdm/simple-greeter/disable_restart_buttons to true.  So I tried setting that for the user gdm using gconftool-2.  That didn't work, even after a reboot there is still a power icon in the lower-right corner of the login screen that allows anyone capable of clicking a mouse to shutdown or reboot the machine.

The next thing I tried was to use gconf-editor.  Running the editor as a regular user, I set GConf:/apps/gdm/simple-greeter/disable_restart_buttons to true.  Then I copied the contents of ~/.gconf/apps/gdm to ~gdm/.gconf/apps/gdm/, set the ownership and permissions appropriately (owner gdm:gdm, mode 0600 on files, 0700 on folders).

Nope.  No go.

The gdm manual also alures to the ability to use PolicyKit to require authentication before allowing reboot/shutdown actions, but sadly lacks the details on how to actually do this.  And of course, the official gdm gnome page is ever so helpful -- it has absolutely no information on it at all.

Why, oh why, did they make gdm so difficult to configure, and can anyone help me out?

---

### Post by StuartN on 2009-12-02
> **msp3k said:**
> Why, oh why, did they make gdm so difficult to configure, and can anyone help me out?

[http://lionlix.wordpress.com/2009/10/23/hack-ubuntu-9-10-karmic-koala-gdm-login-screen/](http://lionlix.wordpress.com/2009/10/23/hack-ubuntu-9-10-karmic-koala-gdm-login-screen/)

(but the configuration options are very limited)

---

### Post by msp3k on 2009-12-02
Harumph.  You're right.  Very limited.  It doesn't seem to give me what I need at all...

Seems like preventing users from rebooting would be an important enough of a feature that they'd make it easier to figure out.

---

### Post by msp3k on 2009-12-03
To summarize and expand on the reply above:

[LIST=1]
[*]To modify gdm's appearance, background, and other UI features, do the following:
[LIST=1]
[*]Log out, wait for the gdm login screen to appear
[*]Press control+alt+F1 to go to the tty1 console, log into your admin account
[*]Type: export DISPLAY=:0.0
[*]Type: sudo -u gdm gnome-control-center
[*]Press control+alt+F7 to get back to the gdm login.  You will see the gnome control center window.
[*]Make changes to your heart's content.  Most of the control center controls will have no effect on gdm, but you can change the UI theme and background image.
[*]When finished, exit the gnome control center, and press control+alt+F1 to return to the tty1 console.  Log out so no other would-be malicious users can use your admin account to wreak havoc.
[*]Press control+alt+F7 to return once again to the gdm login screen, resume using your computer.

I would love to figure out how to do this from the command line, or find out what files are modified, so that I can package it up to be installed on all of my workstations.
[/LIST]
 
[*]To disable the user list, do the following:
[LIST=1]
[*]Type: sudo -u gdm gconftool-2 -t bool -s /apps/gdm/simple-greeter/disable_user_list true

The next time you see gdm, there will not be a user list.  Instead, when you press a key, you will be prompted to type a username, followed by a second prompt for a password.
[/LIST]
 
[*]To disable the reboot/shutdown/suspend/hibernate features for the average user, see the following thread:

"**How to prevent user reboot/shutdown from desktop and gdm?**"

[http://ubuntuforums.org/showthread.php?p=8433295#post8433295](http://ubuntuforums.org/showthread.php?p=8433295#post8433295)
[/LIST]

[CAUTION: Rant Ahead]

Seriously, there ought to be an easier way for an admin to set such things up for a bunch of managed desktop machines.

Ubuntu wants to make the desktop easier and more accessible for the purpose of spreading Linux to the rest of the world, and they've made it real nice.  It's obvious that they've put a lot of effort into the end product, but it's also obvious that they're still focusing on the single end-user trying it out on their own machine.  But that's far from the only way to spread Linux.  Another way is through people like me, a university sysadmin managing a department of desktops running Linux.  We have the power to influence the up-and-coming youth of today by giving them an alternative to MS and Apple, and there are certain things we will need in order to get our jobs done -- important things like setting up who has the authority to reboot a machine.

...Just sayin'.

---

### Post by StuartN on 2009-12-03
> **msp3k said:**
> [*]To disable the user list, do the following:

This was the first thing I did after installing Karmic - it is completely, utterly irresponsible to default to providing a valid list of usernames at bootup.

It would be so easy to provide a script that would enable the login user list for those people who do want it, or to enable a default logon without password as earlier versions permitted. These should not be a default, especially when disabling the list is not straightforward.

---


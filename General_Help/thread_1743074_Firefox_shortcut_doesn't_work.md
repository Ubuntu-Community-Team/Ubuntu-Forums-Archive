---
title: "Firefox shortcut doesn't work"
date: 2011-04-29
forum: General Help
---

### Post by apw5020 on 2011-04-29
After a while of sifting through other threads, I decided none of them could solve my problem.  My problem: when I click the Firefox icon on the quick launch sidebar in 11.04, it just blinks and Firefox never opens.  

I tried reinstalling Firefox, removing and reinstalling the packages from the Synaptic Package Manager but that's about it.  When I type "Firefox" into the command line it says something along the lines of "/home/apw5020/firefox: firefox not found".  When I go into usr/bin/firefox and run the shell script directly it will run however.  Is the shortcut path non existent or just incorrect?  Any idea how I can fix it?

When I run it in Classic, Firefox doesn't work either.  By the way, I used some workaround to run Firefox 4 before 11.04 was released involving PPAs.  Not sure if that could be the problem.

Thanks for the help.

---

### Post by neodac on 2011-04-29
Having the same problem.  Can't get firefox to launch at all had to go download epiphany to post this.  I'm on an Acer Aspire 5050 if that matters. hope you can help i really want my bookmarks back.

Edit: Just figured out how to log into ubuntu classic Firefox works there just fine, but if anyone can tell me how to get it fixed in unity i'd like to give it a fair shake.

and in case the Origional poster didnt know log out and click your account at the bottom of the screen theres an option for what you want to log into "classic Ubuntu" gives you the old gnome desktop

---

### Post by apw5020 on 2011-04-29
UPDATE:  Okay, when I type firefox in the terminal it says:

/home/apw5020/bin/firefox: line 3: /home/apw5020/firefox/firefox: No such file or directory

Not sure if this is any help.:confused:

---

### Post by sg1efc on 2011-04-29
Sorry, my info does not apply to this thread's question...  :(

---

### Post by ratcheer on 2011-04-29
> **apw5020 said:**
> UPDATE:  Okay, when I type firefox in the terminal it says:

/home/apw5020/bin/firefox: line 3: /home/apw5020/firefox/firefox: No such file or directory

Not sure if this is any help.:confused:

I had the same problem and solved it. See the post #10 in this thread: [http://ubuntuforums.org/showthread.php?t=1742114](http://ubuntuforums.org/showthread.php?t=1742114)

Tim

---

### Post by apw5020 on 2011-04-29
> **ratcheer said:**
> I had the same problem and solved it. See the last post in this thread: [http://ubuntuforums.org/showthread.php?t=1742114](http://ubuntuforums.org/showthread.php?t=1742114)

Tim

Yes, that seems to be the same problem. However, after going through the same procedure as you when I log into classic Ubuntu it never tells me that it can't find /opt/firefox and I can't figure out how to specify a path for the icon.  Any suggestions?

To be specific, here is the output to whereis firefox:

apw5020@Linux:~$ whereis firefox
firefox: /usr/bin/firefox /etc/firefox /usr/lib/firefox /usr/lib64/firefox /usr/local/firefox /usr/share/man/man1/firefox.1.gz

---

### Post by neodac on 2011-04-29
I still need some help here my firefox shortcuts dont work in unity but it runs ok from terminal which i didnt try before i do get this

(firefox-bin:2232): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_menuitem_property_set_shortcut: assertion `gtk_accelerator_valid(key, modifier)' failed

(firefox-bin:2232): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_menuitem_property_set_shortcut: assertion `gtk_accelerator_valid(key, modifier)' failed
david@redlotus:~$ firefox


one seems to be opening and one seems to be closing of firefox once its open the arrows point to the shortcut indicating that its running and that i'm using it.

---

### Post by ratcheer on 2011-04-29
> **apw5020 said:**
> Yes, that seems to be the same problem. However, after going through the same procedure as you when I log into classic Ubuntu it never tells me that it can't find /opt/firefox and I can't figure out how to specify a path for the icon.  Any suggestions?

To be specific, here is the output to whereis firefox:

apw5020@Linux:~$ whereis firefox
firefox: /usr/bin/firefox /etc/firefox /usr/lib/firefox /usr/lib64/firefox /usr/local/firefox /usr/share/man/man1/firefox.1.gz

Wow, you have it in a lot of places! You need to decide which one should be used. Then, in Classic Gnome, right click on the icon and select "Properties". Then, there is a command to be executed with a Browse button to the right of it. Click Browse and navigate to the one you want to execute, for example maybe /usr/bin/firefox. Select it and this should show as the new command to be executed. Close and test the icon.

You do it pretty much the same way with the menu entry, except first you have to get into the menu editing dialog.

Tim

---

### Post by lovinglinux on 2011-05-03
> **neodac said:**
> I still need some help here my firefox shortcuts dont work in unity but it runs ok from terminal which i didnt try before i do get this

(firefox-bin:2232): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_menuitem_property_set_shortcut: assertion `gtk_accelerator_valid(key, modifier)' failed

(firefox-bin:2232): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_menuitem_property_set_shortcut: assertion `gtk_accelerator_valid(key, modifier)' failed
david@redlotus:~$ firefox


one seems to be opening and one seems to be closing of firefox once its open the arrows point to the shortcut indicating that its running and that i'm using it.

Remove the globalmenu.

```
sudo apt-get remove firefox-globalmenu
```

Restart Firefox.

---


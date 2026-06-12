---
title: "Wireless lost"
date: 2009-09-04
forum: General Help
---

### Post by Neodarkness on 2009-09-04
Hi.
I have a  problem. I'm running a jaunty minimal install with openbox on it.
A little while back i had crunchbang and ubuntu gnome and wireless used to work fine, but the other day I made a Debian install on a partition and I had no wireless. Now I did a min-inst with openbox and wireless doesn't work.
My wireless card is rtl8187. Wicd can't detect any wireless network and I can't even compile the realtek web-page driver.
I get this output:

make: *** /lib/modules/2.6.28-15-generic/build: No such file or directory.  Stop.
make: *** [all] Error 2

Also whenever I open wicd and click on preferences, it crashes along with tint2.

Terminal imput:
[email]neodarkness@neodarkness:~/Stuff/PROGRAMS/rtl8185_linux_26.1030.0625.2009.releas[/email]e$ wicd-client
Loading...
Attempting to connect tray to daemon...
Success.
Done.
/usr/share/wicd/wicd/gui.py:1166: GtkWarning: gtk_toolbar_set_icon_size: assertion `icon_size != GTK_ICON_SIZE_INVALID' failed
  self.wTree = gtk.glade.XML(gladefile)
refreshing...
wired profiles found
/usr/share/wicd/wicd/gui.py:1446: GtkWarning: GdkWindow 0x1200003 unexpectedly destroyed
  response = dialog.run()
The program 'wicd-client.py' received an X Window System error.
This probably reflects a bug in the program.
The error was 'RenderBadPicture (invalid Picture parameter)'.
  (Details: serial 3435 error_code 160 request_code 149 minor_code 7)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)



Any help please???
What should I try? Why do you think the wireless stopped working like that? (It has already worked before on Jaunty)
ANy help will be DEEPLY apreciated.

---

### Post by Neodarkness on 2009-09-04
Weird, I installed network-manager and now it works. (never before had network manager worked and wicd no)
I guess tread closed.

---


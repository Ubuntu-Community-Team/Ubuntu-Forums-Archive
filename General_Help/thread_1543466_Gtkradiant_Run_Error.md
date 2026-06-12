---
title: "Gtkradiant Run Error"
date: 2010-08-01
forum: General Help
---

### Post by crazyamerican on 2010-08-01
Yes, I know a thread about this already exists, but it has no answer. I am simply trying to bring the problem back to people's attentions.

System Specs:
1.5GB Memory
1.6Ghz Intel Celeron
Ubuntu 10.04 Lucid

The Problem:

I have installed Gtkradiant, but when I try to run it, I get this:

```


urface@urface-urface:/opt/gtkradiant$ ./radiant.x86 
Gdk-CRITICAL **: gdk_window_get_window_type: assertion `GDK_IS_WINDOW (window)' failed


(process:22326): Gdk-CRITICAL (recursed) **: gdk_window_get_window_type: assertion `GDK_IS_WINDOW (window)' failed
aborting...
Aborted

```

What do I need to do to fix this problem?

---

### Post by huam on 2010-09-20
I've the same problem after installing ubuntu 10.04.
Gdk-CRITICAL **: gdk_window_get_window_type: assertion `GDK_IS_WINDOW (window)' failed


(process:2798): Gdk-CRITICAL (recursed) **: gdk_window_get_window_type: assertion `GDK_IS_WINDOW (window)' failed

---

### Post by EscapeCharacter on 2010-09-22
I am also having this problem. What's worse is that I can't find any information on it here or elsewhere.

I am seriously hoping that there is someone who can help with this.

---

### Post by ramprax on 2010-09-23
Hi,

I am getting the same error, when try to run radiant.x86 on Lucid:
***********************
Gdk-CRITICAL **: gdk_window_get_window_type: assertion `GDK_IS_WINDOW (window)' failed
(process:2651): Gdk-CRITICAL (recursed) **: gdk_window_get_window_type: assertion `GDK_IS_WINDOW (window)' failed
aborting...
Aborted
***********************

I am attaching the strace & ltrace output, if that would help.

Thanks,
Ram

---

### Post by ramprax on 2010-09-23
I also tried to run radiant after disabling Desktop Effects. Still no luck!
Has anyone got it running?

Thanks,
Ram

---

### Post by huam on 2010-09-23
After all everything is running.
If you run GtkRadiant there's a file in your home directory
something like :

~/.GtkRadiant/1.5.0/global.pref

<?xml version="1.0"?>
<qpref version="1.0">
<epair name="gamePrompt">false</epair>
<epair name="gamefile">q2.game</epair>
<epair name="log console">true</epair>
</qpref>

If you change the true value gamePrompt in false the program skips the game selection and then it runs the program.
I don't understand why the model popup is not running anymore. Have to find out this later.

---

### Post by EscapeCharacter on 2010-09-24
I have no directory named ~/.GtkRadiant/ in my home directory, the closest thing that is there one simply named .radiant/.

There is no global.pref file in the 1.5.0 subdirectory. I created a global.pref file using the text and xml data which you provided. 

It did not help as I am still getting exactly the same error message.

---

### Post by huam on 2010-09-26
Sorry I still have the error in zeroradiant, but not in the program which I use (basically branch 1.5).
Do you have installed and build zeroradiant ? [http://www.qeradiant.com/cgi-bin/trac.cgi/wiki/ZeroRadiant](http://www.qeradiant.com/cgi-bin/trac.cgi/wiki/ZeroRadiant)
A long time ago I use the next two checkouts as base for some changes :

[https://zerowing.idsoftware.com/svn/radiant/GtkRadiant/branches/1.5](https://zerowing.idsoftware.com/svn/radiant/GtkRadiant/branches/1.5) ./GtkRadiant1.5br
[https://zerowing.idsoftware.com/svn/radiant.gamepacks/Q2Pack/trunk/](https://zerowing.idsoftware.com/svn/radiant.gamepacks/Q2Pack/trunk/) ./Q2Pack

Is suppose you found also this manual : [http://openarena.wikia.com/wiki/Configure_GTK_Radiant_under_Linux](http://openarena.wikia.com/wiki/Configure_GTK_Radiant_under_Linux)
Is there any radiant.log and if, what's the information in it ?
What's the owner and group of your .radiant directory, because the program need write access.
Is there a screen anyway like the next one ?

[IMG]http://cms.hvamelsvoort.nl/uploads/images/Huub/zeroradiantstartup.png[/IMG]

Do you have the Quake2 data files installed ?
I need some more information.

---

### Post by huam on 2010-10-03
On closer inspection turned out not to work and all the error still occurred when opening some pop-ups.

The problem seems solved now, if you are in the following function of 

<radiantdir>/libs/gtkutil/dialog.cpp 

turns over the two the first lines :

EMessageBoxReturn modal_dialog_show(GtkWindow* window, ModalDialog& dialog)
{
 [I][B] gtk_grab_add(GTK_WIDGET(window));
  gtk_widget_show(GTK_WIDGET(window));[/B][/I]

  dialog.loop = true;
  while(dialog.loop)
  {
    gtk_main_iteration();
  }

  gtk_widget_hide(GTK_WIDGET(window));
  gtk_grab_remove(GTK_WIDGET(window));

  return dialog.ret;
}

change to :

EMessageBoxReturn modal_dialog_show(GtkWindow* window, ModalDialog& dialog)
{
[B][I]  gtk_widget_show(GTK_WIDGET(window));
  gtk_grab_add(GTK_WIDGET(window));
[/I][/B]
  dialog.loop = true;
  while(dialog.loop)
  {
    gtk_main_iteration();
  }

  gtk_widget_hide(GTK_WIDGET(window));
  gtk_grab_remove(GTK_WIDGET(window));

  return dialog.ret;
}

---

### Post by PCaddicted on 2011-04-19
I have tried that in the terminal but I got "No such file or directory".The same thing when I pasted the cpp file in the terminal and pressed Enter.When I tried to run it from Nautilus with the Autorun Prompt,nothing happened.I do not think I'll ever get this problem solved.

---

### Post by aktheus on 2011-07-03
I have the same problem, any idea?

root@XXXXX:/opt/gtkradiant# ./radiant.x86 

(radiant.x86:1842): Pango-WARNING **: error opening config file '/root/.pangorc': Permission denied

Gdk-CRITICAL **: gdk_window_get_window_type: assertion `GDK_IS_WINDOW (window)' failed

(process:1842): Gdk-CRITICAL (recursed) **: gdk_window_get_window_type: assertion `GDK_IS_WINDOW (window)' failed
aborting...
Abortado

I'm on ubutu 10.04.
Netradiant runs but im trying to install gtk.

I've searched but at the momment noting works...

PD: sorry about my english.

---

### Post by MikeDK on 2011-08-06
just wanna tell u guys, that gtkradiant no longer is under development, but continues here [http://ingar.satgnu.net/gtkradiant/](http://ingar.satgnu.net/gtkradiant/)

---


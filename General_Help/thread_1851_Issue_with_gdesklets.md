---
title: "Issue with gdesklets?"
date: 2004-10-23
forum: General Help
---

### Post by cj2003 on 2004-10-23
First time trying Linux - and very happy so far! So I'm a beginner....

I've installed gdesklets and the gdesklets-data from synaptic, but the program won't start when I run it from the Applications->Accesories menu.

When trying gdesklets in a terminal, I get:

"(gDesklets:5383): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
gDesklets 0.26.2
Copyright (C) 2003, 2004 The gDesklets Team

This software is licensed under the terms of the GNU GPL.

/usr/lib/python2.3/site-packages/gtk-2.0/gtk/__init__.py:90: GtkDeprecationWarning: gtk.mainloop is deprecated, use gtk.main instead
  self.warn(message, DeprecationWarning)
"

I've seen the problem mentioned at:

[http://gnomesupport.org/forums/viewtopic.php?t=7900&sid=c879fba4f88608af3ff1c017c0556e2a](http://gnomesupport.org/forums/viewtopic.php?t=7900&sid=c879fba4f88608af3ff1c017c0556e2a)

but haven't been able to get it running?

Any suggestione?

thanks
Christian

---

### Post by Rancoras on 2004-10-23
gdesklets is just the daemon.  The first time you run it with no parameters, it just starts the daemon.  Here's how I did it:

Applications > Run Application

gdesklets > Run

That gets the daemon started

Now find a display or sensor that you want to run.  They should be in /usr/share/gdesklets/Displays or Sensors.

Applications > Run Application

gdesklets /path/to/foo.display > Run

The display will stick to your mouse cursor until you click somewhere on the desktop to drop it.  You can then move it around with a middle button drag.
Now right click the running gdesklet and click quit.  This will also kill the daemon.  You can now start the daemon back up with:

Applications > Accessories > gdesklets

The daemon will now remember what displays it was running the last time it was stopped.

---

### Post by Neo40 on 2004-10-23
I have downloaded the source file "gDesklets-0.30.tar.bz2 " and when I ./configure I get this error:

configure: error: XML::Parser perl module is required for intltool

What packages do I need?

Thanks

---

### Post by cj2003 on 2004-10-24
Excellent, thanks Rancoras - now it works!

Christian

---

### Post by hr15 on 2004-10-26
[QUOTE=Neo40]I have downloaded the source file "gDesklets-0.30.tar.bz2 " and when I ./configure I get this error:

configure: error: XML::Parser perl module is required for intltool

What packages do I need?

Thanks[/QUOTE]

I've got the same problem and i can;t fix it :(
Does anyone knows what kind of package i need ?

---

### Post by Rancoras on 2004-10-26
Search for the word parser in synaptic.  I can't remember the exact name of the package, something like perl-parser I think.

---

### Post by JProgrammer on 2004-10-26
[QUOTE=hr15]I've got the same problem and i can;t fix it :(
Does anyone knows what kind of package i need ?[/QUOTE]
 I have got almost every package needed for that one search in synaptic for XML::Parser in the description and it will already be installed you need to install the -dev package same goes for all the other packages it can't find. You will end up needing GTK2-dev as well as others

---

### Post by Gus-O-Matic on 2004-10-27
I eventually managed to get it to compile. It still doesn't work though, heres what happens;

(process:22551): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
Cannot establish connection to daemon : timeout

Any one have any ideas?

---

### Post by JProgrammer on 2004-10-27
Have your started the daemon?

```
$ gdesklets
```

You must do this before you can start running displays

---

### Post by Gus-O-Matic on 2004-10-27
sorry, let me just clarify.

$./gdesklets start

This results in the output i showed before

$./gdesklets-daemon

(process:5226): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

$./gdesklets-shell

The shell window comes up but then i get this 

(process:5247): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
Cannot establish connection to daemon : timeout

So I presume the problem is the Daemon not starting.

---

### Post by Gus-O-Matic on 2004-10-27
Fixed.

I had another look at the comile instructions in the README, and tried again. Success! :D

---

### Post by FLeiXiuS on 2004-10-30
[QUOTE=Rancoras]gdesklets is just the daemon.  The first time you run it with no parameters, it just starts the daemon.  Here's how I did it:

Applications > Run Application

gdesklets > Run

That gets the daemon started

Now find a display or sensor that you want to run.  They should be in /usr/share/gdesklets/Displays or Sensors.

Applications > Run Application

gdesklets /path/to/foo.display > Run

The display will stick to your mouse cursor until you click somewhere on the desktop to drop it.  You can then move it around with a middle button drag.
Now right click the running gdesklet and click quit.  This will also kill the daemon.  You can now start the daemon back up with:

Applications > Accessories > gdesklets

The daemon will now remember what displays it was running the last time it was stopped.[/QUOTE]
When I type

gdesklets rssgrab.display

It gives me an invalid file error.  Then it tells me the sensons weren't installed correctly.  Yet I ran the Install.bin file.

---

### Post by chibo on 2004-10-31
Somehow related to this... How do I manage to configure weather-display to actually show the weather? It just says that "Retrieval failed". There is this direct URL field in configuration panel. Should I add somethin to it?

---

### Post by JProgrammer on 2004-10-31
[QUOTE=chibo]Somehow related to this... How do I manage to configure weather-display to actually show the weather? It just says that "Retrieval failed". There is this direct URL field in configuration panel. Should I add somethin to it?[/QUOTE]
 Are you behind a proxy server?

---

### Post by Rancoras on 2004-10-31
[QUOTE=FLeiXiuS]When I type

gdesklets rssgrab.display

It gives me an invalid file error.  Then it tells me the sensons weren't installed correctly.  Yet I ran the Install.bin file.[/QUOTE]

I haven't tried that one, I'll try it and let you know.

---

### Post by FLeiXiuS on 2004-11-01
[QUOTE=Rancoras]I haven't tried that one, I'll try it and let you know.[/QUOTE]

Ohh its a must have if your a fan of RSS and love to read a lot of geek news :-P

SLASHDOT!

---

### Post by Sapper2ID on 2005-01-22
Can you add new types of desklets? Like adding themes? I'd like to put active  weather radar on. Possible?

---

### Post by fender1212 on 2005-01-30
alright, did everything, and when trying to run ./configure i get at the end 

checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.

any help for this one?

---

### Post by Buffalo Soldier on 2005-02-08
[QUOTE=FLeiXiuS]When I type

gdesklets rssgrab.display

It gives me an invalid file error.  Then it tells me the sensons weren't installed correctly.  Yet I ran the Install.bin file.[/QUOTE]

I think you must type it in full:```
gdesklets /usr/share/gdesklets/Displays/**xxx_folder**/**rssgrab.display**
```

---

### Post by Nnyan on 2005-02-15
I'm having the same problem as Fender1212.

When I look at the config.log file the error seems to be this:

 "installation problem, cannot exec `cc1plus': No such file or directory"

Not sure what to do at this point.

---

### Post by Xian on 2005-02-15
[QUOTE=Nnyan]I'm having the same problem as Fender1212.[/QUOTE]
Use Synaptic, then install the g++, gcc and cpp packages.

---

### Post by pwnt on 2005-10-23
Hello, i had gdesklets deamon running good, and in my fluxbox window manager, When i right click in the gdesklets in the systray icon and go to Manage Gdesklets then i go to the Weather or the Mail gdesklets, they've been tolding me that i just have to double click on the picture of it that i'm seeing there and it'll jump into my mouse curser so i go to the background and press to paste it somewhere there, but whenever i do, i get that in the terminal, i think it's an error, and the gdesklets didn't go with my cursor, thanks.


[EXC]exceptions.IndexError:
[EXC]list index out of range
in /usr/lib/gdesklets/shell/ItemBrowser.py: line 114 __on_activate_item
in /usr/lib/gdesklets/utils/Observable.py: line 45 update_observer
in ./DisplayBrowser/__init__.py: line 121 __on_activate
in ./gDeskletsClient/__init__.py: line 36 open_display
in /usr/lib/gdesklets/main/client.py: line 58 open_display
[---]/usr/lib/gdesklets/main/client.py
[---]   53 
[---]   54         @return: The ID of the new display.
[---]   55         @rtype : str
[---]   56         """
[---]   57 
[ERR]>  58         return self.__send(COMMAND_OPEN_DISPLAY, path)[0]
[---]   59 
[---]   60 
[---]   61 
[---]   62     def open_display_with_id(self, path, ident):
[---]   63 
[---]   64         """


Thats it all, thanks.

---


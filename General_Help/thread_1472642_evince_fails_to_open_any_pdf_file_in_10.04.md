---
title: "evince fails to open any pdf file in 10.04"
date: 2010-05-04
forum: General Help
---

### Post by luislupe on 2010-05-04
Hi,

evince cannot open any pdf file in Ubuntu 10.04.
I've already removed the package completely, reinstalled, as well as ubuntu-desktop, but the problem remains.

$ evince

[COLOR="Blue"](evince:3737): EggSMClient-WARNING **: Failed to connect to the session manager: None of the authentication protocols specified are supported
(evince:3737): Gtk-WARNING **: Attempting to read the recently used resources file at `/home/br/.recently-used.xbel', but the parser failed: Falha ao abrir o ficheiro '/home/br/.recently-used.xbel': Permissão negada.[/COLOR]

Permission denied, it says, but:
[COLOR="Blue"]$ ll .recently-used.xbel 
-rw------- 1 br br 45437 2010-05-04 18:15 .recently-used.xbel[/COLOR]
seems to have read/write permissions.

When I try to open a pdf file, the output is:
[COLOR="Blue"](evince:3737): Gtk-WARNING **: Failed to read filechooser settings from "/home/br/.config/gtk-2.0/gtkfilechooser.ini": Permissão negada
(evince:3737): Gtk-WARNING **: Failed to read filechooser settings from "/home/br/.config/gtk-2.0/gtkfilechooser.ini": Permissão negada[/COLOR]


[COLOR="Blue"](evince:3737): Gtk-WARNING **: Failed to read filechooser settings from "/home/br/.config/gtk-2.0/gtkfilechooser.ini": Permissão negada
(more two errors like this)
(evince:3737): Gtk-WARNING **: Attempting to store changes into `/home/br/.recently-used.xbel', but failed: Falha ao criar o ficheiro '/home/br/.recently-used.xbel.Q76PCV': Permissão negada
(evince:3737): Gtk-WARNING **: Attempting to set the permissions of `/home/br/.recently-used.xbel', but failed: Permissão negada
(evince:3737): Gtk-WARNING **: Attempting to store changes into `/home/br/.recently-used.xbel', but failed: Falha ao criar o ficheiro '/home/br/.recently-used.xbel.5B7PCV': Permissão negada
(evince:3737): Gtk-WARNING **: Attempting to set the permissions of `/home/br/.recently-used.xbel', but failed: Permissão negada
Error: Couldn't create temporary font file
some font thing failed
(several of this)
[/COLOR]

It says no permission, but permissions seem to be ok here, too:
[COLOR="Blue"]$ ll .config/gtk-2.0/gtkfilechooser.ini 
-rw-r--r-- 1 br br 203 2010-05-03 19:12 .config/gtk-2.0/gtkfilechooser.ini[/COLOR]

What should I do in order to fix this?  It seems I'm the only one with this problem in the new 10.04.

---

### Post by luislupe on 2010-05-05
Is this a bug? or just some misconfiguration?

I'd appreciate an answers.


luislupe

---

### Post by Seal Daemon on 2010-05-05
```
sudo ln -s /etc/apparmor.d/usr.bin.evince /etc/apparmor.d/disable

```

Try again ?

---

### Post by luislupe on 2010-05-06
Thanks for the tip, but evince behaves in the same strange way.

---

### Post by Seanman on 2010-05-07
I found this post when I had the same issue.

When I burnt down the machine and installed Lucid, I copied over my old  bashrc where the TMP variable was set to a directory that doesn't exist on my new system.

Setting the variable in my bashrc to /tmp took care of it for me.  Evince works great now.

Hope that helps with your problem.

---

### Post by thechanklybore on 2010-05-12
> **luislupe said:**
> Thanks for the tip, but evince behaves in the same strange way.

It works for me - definitely a problem with apparmor. Did you reload the apparmour profiles?

sudo /etc/init.d/apparmor restart

---

### Post by canard10 on 2010-05-25
I had a similar problem. In my case  the reason was that my home dir is not in /home/. It could be solved by adapting the apparmor configuration, see [http://www.ubuntu.com/getubuntu/releasenotes/1004](http://www.ubuntu.com/getubuntu/releasenotes/1004) section * Evince PDF viewer does not work for nonstandard home directories.*

---

### Post by misterhaan on 2010-05-27
thanks for the tips -- i also have home directories somewhere other than /home/ so was able to edit /etc/apparmor.d/tunables/home as root, change /home/ to what i'm using, and restarting apparmor.  does anyone have a launchpad bug link for this?

i tried to open pdf files before making this fix by double-clicking them -- NOTHING happens.  you get the busy cursor for a while and then it goes away.  not everyone knows the pdf viewer is called evince or that you can see debug output by opening up a command prompt and running evince from there.

---

### Post by dvo on 2010-05-30
After using evince on a freshly installed ubuntu lucid system for a couple of days, it also stopped showing pages, printing on the console:

```
Error: Couldn't create temporary font file
some font thing failed
```

The suggested solution solved the problem for me:

```
sudo ln -s /etc/apparmor.d/usr.bin.evince /etc/apparmor.d/disable
sudo /etc/init.d/apparmor restart
```

---

### Post by Scoobin on 2010-07-10
I'm having this same problem where I double click a PDF and it looks as though it's in the process of opening a file and then nothing happens.

I've tried the apparmor commands above.

I don't know if this is relevant or not, but when I type evince at the CLI I get this response:

```
evince: symbol lookup error: evince: undefined symbol: ev_get_locale_dir
```

my /etc/apparmor.d/tunables/home file has:

```
# @{HOME} is a space-separated list of all user home directories. While
# it doesn't refer to a specific home directory (AppArmor doesn't
# enforce discretionary access controls) it can be used as if it did
# refer to a specific home directory
@{HOME}=@{HOMEDIRS}/*/ /root/

# @{HOMEDIRS} is a space-separated list of where user home directories
# are stored, for programs that must enumerate all home directories on a
# system.
@{HOMEDIRS}=/home/

# Also, include files in tunables/home.d for site-specific adjustments to
# @{HOMEDIRS}.
#include <tunables/home.d>
```

My home dir is the usual /home, although I access documents from another partition. Tried copying it to /home and it still didn't open.

Is anyone able to assist?

---

### Post by philinux on 2010-07-10
Enable the partner repo in sys>admin>software sources then install acroread.

[https://help.ubuntu.com/community/AcrobatHowTo](https://help.ubuntu.com/community/AcrobatHowTo)

---

### Post by Scoobin on 2010-07-10
Thanks for the tip. Acrobat though wouldn't be my preferred option. Ideally the default viewer would actually work. If I couldn't get it going, I see there is a 'ePDFViewer' (based on Evince but not using the Gnome libraries) and 'ViewPDF' at least, in the repos.

---

### Post by Scoobin on 2010-07-10
It's working now. 

It seems I had to download one of the updates. Perhaps a previous update 'broke' it.

---

### Post by cpbl on 2010-08-31
I have the same problem with evince:

> Error: Couldn't create temporary font file
some font thing failed


but my home directory is in the standard place. I recently moved my /tmp dir to a symbolic link to /export/tmp.  Is that my problem? But is /tmp tunable? I don't see any mention of it. And what is wrong with a symbolic link for /tmp?

Thanks for any ideas!

---

### Post by cpbl on 2010-08-31
Also, btw, when I use the apparmor disabling method, I get told:

> * Reloading AppArmor profiles                                                  Skipping profile in /etc/apparmor.d/disable: usr.bin.evince
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
   

Is it okay that firefox protection seems also to have been disabled by someone?

---

### Post by roderikk on 2010-09-03
> **dvo said:**
> After using evince on a freshly installed ubuntu lucid system for a couple of days, it also stopped showing pages, printing on the console:

```
Error: Couldn't create temporary font file
some font thing failed
```

The suggested solution solved the problem for me:

```
sudo ln -s /etc/apparmor.d/usr.bin.evince /etc/apparmor.d/disable
sudo /etc/init.d/apparmor restart
```

I had the same problem and this solution also worked for me. I upgraded from 9.10 to 10.04 and it suddenly stopped working.

---


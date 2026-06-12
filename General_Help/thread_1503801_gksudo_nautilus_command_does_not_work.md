---
title: "gksudo nautilus command does not work"
date: 2010-06-07
forum: General Help
---

### Post by t.wicks on 2010-06-07
hi all,

I cannot get gksudo nautilus to work.  I downloaded nautilus-elementary, and then nautilus desktop, now when I try to access gksudo nautilus in the command line i get this message:

Nautilus could not create the required folder "/root/.config/nautilus".

Before running Nautilus, please create the following folder, or set permissions such that Nautilus can create it.

I tried to create the file with sudo mkdir, but it told me the file already existed.

Can someone help me get the, gksudo nautilus, command working for me again?  

I posted a question at the nautilus-elementary launchpad site but my question was taken down without explanation.

I posted a bug there about my photos losing ability to auto rotate in default photo viewer after installing nautilus-elementary, and "kitkat" promptly and coldly replied it is not his/her problem and the bug post was being deleted.  Don't know "kitkat" but my feeling is he/she won't be helping me...ever.

thanks to all that try to help!
-tom

---

### Post by Smart Viking on 2010-06-07
I don't think it is meant to be a file like that at least i do not have that file and nautilus works. :)

Does it work to use "sudo nautilus"?

---

### Post by t.wicks on 2010-06-07
sudo nautilus, does not work either, it gives me the same error message.

and i tried, gksu nautilus, as well, it does not work either, with the same error message.

---

### Post by afrodeity on 2010-06-07
make sure that gksu-nautilus is installed. I recently upgraded to Lucid and for some reason it got removed.

Open synaptic and search for nautilus, it should be there.

---

### Post by Smart Viking on 2010-06-07
This might sound stupid but worth a try, what about "sudo gksudo nautilus"?

Also, does you have a directory called "/root/.nautilus"?

---

### Post by t.wicks on 2010-06-07
@afrodeity

Yes, I have nautilus-gksu activated, you are correct it was deactivated, but activating it was one of the first things I did when I started to troubleshoot this problem.

---

### Post by t.wicks on 2010-06-07
@Smart Viking

No, that is not stupid, but it didn't work either

no I do not have a folder named /root/.nautilus

but are you talking about /root/.config/nautilus instead? the one nautilus says is not there.

I would love to actually see what is in my root folder but, gksudo nautilus does not work.

if this helps, looking for /root/.config/nautilus returns a does not exist in terminal, but.....

.config/nautilus does exist in terminal, without typing "/root"

---

### Post by Smart Viking on 2010-06-07
I was talking about "/root/.nautilus", i have that directory, try to make it and then try. :)

EDIT: The directory is empty though.

---

### Post by t.wicks on 2010-06-07
@Smart Viking

Termial says it already exist

---

### Post by afrodeity on 2010-06-07
Try this:

```

gconftool-2 --recursive-unset /apps/nautilus

```

---

### Post by t.wicks on 2010-06-07
I got it to work.

I made the folder step by step.

1. sudo mkdir /root (terminal said it already existed)
2. sudo mkdir /root/.config
3. sudo mkdir /root/.config/nautilus

I am new to ubuntu, is this normal?

anyways I ran it and got it to work but the window messed up and I got these warnings in terminal, is this a problem?


ubuntu@ubuntu:~$ gksudo nautilus
Initializing nautilus-open-terminal extension
Initializing nautilus-dropbox 0.6.2
Initializing nautilus-gdu extension

(nautilus:3579): Gtk-WARNING **: Redo: missing action Redo

(nautilus:3579): Gtk-WARNING **: Reset to Defaults: missing action Reset to Defaults
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:3579): Gtk-CRITICAL **: gtk_widget_render_icon: assertion `stock_id != NULL' failed

(nautilus:3579): Gtk-CRITICAL **: gtk_icon_theme_load_icon: assertion `icon_name != NULL' failed

(nautilus:3579): Gtk-CRITICAL **: gtk_widget_render_icon: assertion `stock_id != NULL' failed

(nautilus:3579): Gtk-CRITICAL **: gtk_icon_theme_load_icon: assertion `icon_name != NULL' failed

(nautilus:3579): Gtk-CRITICAL **: gtk_widget_render_icon: assertion `stock_id != NULL' failed

(nautilus:3579): Gtk-CRITICAL **: gtk_icon_theme_load_icon: assertion `icon_name != NULL' failed

(nautilus:3579): Gtk-CRITICAL **: gtk_widget_render_icon: assertion `stock_id != NULL' failed

(nautilus:3579): Gtk-CRITICAL **: gtk_icon_theme_load_icon: assertion `icon_name != NULL' failed

(nautilus:3579): Gtk-CRITICAL **: gtk_widget_render_icon: assertion `stock_id != NULL' failed

(nautilus:3579): Gtk-CRITICAL **: gtk_icon_theme_load_icon: assertion `icon_name != NULL' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

---

### Post by t.wicks on 2010-06-07
@aphrodite

what does "gconftool-2 --recursive-unset /apps/nautilus" do?

and should I run it anyways?

also

how do you get the "code box" to show when posting here, I'm trying to learn.

Thanks for your time and effort!  I apprecite it!

---

### Post by t.wicks on 2010-06-07
@aphrodite
@Smart Viking

My first post @ ubuntu forums, thanks to you both!

-tom

---

### Post by afrodeity on 2010-06-07
> **t.wicks said:**
> @aphrodite

what does "gconftool-2 --recursive-unset /apps/nautilus" do?

and should I run it anyways?

also

how do you get the "code box" to show when posting here, I'm trying to learn.

Thanks for your time and effort!  I apprecite it!

It appears to reset the nautilus presets to the gnome desktop via gconf. I've experienced problems with nautilus because of the settings. Seeing as how you're hacking around, you may as well take a look inside gconf.

Alt F2

Type: gconf-editor

go to apps > nautilus > preferences

---

### Post by ammonkey on 2010-06-07
@t.wicks i suggest u reinstall correctly nautilus from the ppa. Many of your output errors come from missing icons.

---

### Post by nutsy.ben on 2010-06-08
> **afrodeity said:**
> make sure that gksu-nautilus is installed. I recently upgraded to Lucid and for some reason it got removed.

Open synaptic and search for nautilus, it should be there.

SMART LITTLE ONE .... 

I had the same problem since my update to Lucid ... it was indeed due to a removal of gksu-nautilus.

---

### Post by elvisrv on 2010-06-08
Installing nautilus-gksu worked perfect for me. Now gksudo nautilus opens ok

---

### Post by bra|10n on 2010-06-09
Out of the blue I experienced this problem also. 
I looked for nautilus-gksu and indeed it was not installed.
Installing it made no difference for me.
I then tried "gconftool-2 --recursive-unset /apps/nautilus".
It too did not solve the issue.
I then tried t.wicks solution
```
1. sudo mkdir /root (terminal said it already existed)
2. sudo mkdir /root/.config
3. sudo mkdir /root/.config/nautilus
```Still did not work for me. Only change was I stopped seeing the error msg.
I log out, restarted a couple of times, no luck.
I went snooping in gconf-editor apps > nautilus > preferences
I made one change only... show_advanced_permissions and checked this and problem solved!
Now I don't know what this all means but I've now unchecked the item and all is still well.
Anyone...

---

### Post by afrodeity on 2010-06-11
> **bra|10n said:**
> Out of the blue I experienced this problem also. 
I looked for nautilus-gksu and indeed it was not installed.
Installing it made no difference for me.
I then tried "gconftool-2 --recursive-unset /apps/nautilus".
It too did not solve the issue.
I then tried t.wicks solution
```
1. sudo mkdir /root (terminal said it already existed)
2. sudo mkdir /root/.config
3. sudo mkdir /root/.config/nautilus
```Still did not work for me. Only change was I stopped seeing the error msg.
I log out, restarted a couple of times, no luck.
I went snooping in gconf-editor apps > nautilus > preferences
I made one change only... show_advanced_permissions and checked this and problem solved!
Now I don't know what this all means but I've now unchecked the item and all is still well.
Anyone...

Yes, that is what I was trying to get at, you first reset nautilus via gconf and then turn on the options you need. Managed to get my nautilus browser back after the lucid upgrade by doing this.:)

---

### Post by dcstar on 2010-06-11
```
gksudo "dbus-launch nautilus --no-desktop --browser"
```

---

### Post by yo2boy on 2010-06-17
This is what I tried and it worked like a charm:

```
gconftool-2 --recursive-unset /apps/nautilus
```

Then, finally

```
sudo killall -9 nautilus && gksu nautilus
```

I am now happy :)

---

### Post by Yogotiss on 2010-06-29
> **yo2boy said:**
> This is what I tried and it worked like a charm:

```
gconftool-2 --recursive-unset /apps/nautilus
```Then, finally

```
sudo killall -9 nautilus && gksu nautilus
```I am now happy :)


That did the trick!

---

### Post by thornspear on 2010-10-02
I tried both of those commands, and the output was I got was
```

** Message: Initializing gksu extension...Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

```I just installed 10.04 from scratch.  Nautilus runs, but I still don't have permissions to move files around. 

I also downloaded gksu nautilus in synaptic and ticked the show_advanced_permissions box in gconf-edit.

Any other way to get permission to move files around from the root directory?

---

### Post by dilei on 2010-10-05
> **thornspear said:**
> I tried both of those commands, and the output was I got was
```

** Message: Initializing gksu extension...Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

```I just installed 10.04 from scratch.  Nautilus runs, but I still don't have permissions to move files around. 

I also downloaded gksu nautilus in synaptic and ticked the show_advanced_permissions box in gconf-edit.

Any other way to get permission to move files around from the root directory?


I did the same, got the same and suddenly (I don't know how I got it) it asked for my pass and went through...
[INDENT][INDENT][LEFT]di@di:~$ sudo killall -9 nautilus && gksu nautilus
[sudo] password for di: 
[sudo] password for di: 
Initializing nautilus-gdu extension
[/LEFT]
[/INDENT][/INDENT]...then opened Nautilus in the root directory.

But, although I seem to have write-permission (I could create a folder), I only have Desktop, and nothing into it... I was looking for Fonts.

I'm new with Ubuntu and like it, but have been more than two hours trying to get tahoma.tff installed! It seems that I'm still missing the key to the Linux world.

Thanks for the help you may provide,
Di

---EDIT

Ok. The problem I was having was into Wine. Now I notice what I need to do is to copy the fonts into c:\windows\fonts, which is not a problem at all.

And I found a couple of threads more specific than what I thought there would be about running counter strike, but I'm more interested in how to resolve these problems than in running the game.

If anyone can help me on how to add Fonts clearly, it'd be great since all I read is confusing.

---

### Post by thornspear on 2010-10-05
I was experiencing a few other issues with my system as well, so I just reinstalled 10.04 last night.  Will try Nautilus again tonight and see if it's working.  The reinstall has fixed all of my other issues so far...

---

### Post by dilei on 2010-10-05
> **thornspear said:**
> I was experiencing a few other issues with my system as well, so I just reinstalled 10.04 last night.  Will try Nautilus again tonight and see if it's working.  The reinstall has fixed all of my other issues so far...


Good to know. I had a couple of strange episodes, like the whole system not responding when trying to get back from the screensaver...

Other thing that happens to me is that I usually have to enter the password twice... I understand this has to do with security, but why TWICE? It seems that my attempts to install the fingerprint reader have something to do with this... I can't get that working either.

I don't know why the emails are gone from the upper right shortcut bar (the one that has the time), and can't get myubuntu and the instant messenger to remain open.

If I want to reinstall Ubuntu, will I be losing information? Will I have to reinstall the drivers? I have to make an effort to get my laptop to a cable so I can download drivers for wireless.

I should probably look for help for each of my issues individually, but  if anyone can throw a quick piece of advice I'll appreciate it.

Thanks!
Ivo

---

### Post by thornspear on 2010-10-05
Before I reinstall Ubuntu, I just copy my Home folder to an external HD,  start from scratch with a fresh install, and then import my home folder to my new Ubuntu.  

I've also gotten in the habit of bookmarking forum pages that have helped me solve issues with my particular system, so when I reinstall I don't have to go through searching for everything again.  I'd open them all up in Firefox and then email myself the links (although there's probably an easier way to save bookmarks - I'm just not aware of it and I knew this would do the trick). 

A couple of times when booting into Ubuntu 10.04, I've noticed that there have been problems with the upper right portion of the task bar.  My user name would appear twice and I wouldn't be able to access the I/O button to shut down or restart.  Thinking back, I may have installed a 32-bit version last night instead of a 64-bit.  Will check that when I get home.  

I'm sure there's a way to save your drivers, but I'm not aware of it.  Luckily for me, the wireless on my new laptop works right out of the box.

---

### Post by sputnikeee on 2011-01-06
[LEFT]Hi.  I realize this thread is getting a bit old, but posting for the benefit of those that may be searching for this problem as I have been for quite some time.  I hope posting here is the appropriate method.  

I had the problem that although sudo nautilus seemed to work just fine, the terminal window from which I spawned it would spew forth several gtk-WARNING messages and it was annoying. I tried all the remedies spoken of in this thread, but they didn't help. They did put me on the right track however.  In my ~/.nautilus/metadata folder is a file that states: > Nautilus 2.32 deprecated this directory and tried migrating this configuration to ~/.config/nautilus. And indeed, there is a Nautilus/metadata folder in ~/.config with the configurations. When I tried creating a /root/.config/Nautilus folder as suggested in this thread, I found that the folder was already in existence. BUT there was nothing in the folder. I copied the metadata folder from ~/.config/Nautilus folder to the /root/.config/Nautilus folder and voila! No more warnings. 

I couldn't find a more elegant fix, like a config file for nautilus, obviously there is a discrepancy in where it looks for these files.  But this down & dirty fix does the job. Also posted at the Aurora (my Linux version) forums:  [http://forums.auroraos.org/viewtopic.php?f=54&t=6169](http://forums.auroraos.org/viewtopic.php?f=54&t=6169)[/LEFT]

---

### Post by lidex on 2011-01-07
First of all, you should never run a graphical app with 'sudo', only 'gksu' or 'gksudo' and I'm willing to bet that those of you with this problem probably did exactly that.
Reference: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)
I have none of the files mentioned in these posts and yet 'gksudo nautilus' works perfectly for me.

---

### Post by gorencgregor on 2013-04-16
> **afrodeity said:**
> Try this:

```

gconftool-2 --recursive-unset /apps/nautilus

```

Just install ''gksu'' in synaptic.. It worked for me :)

---

### Post by overdrank on 2013-04-16
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/misc.php?do=showrules")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---


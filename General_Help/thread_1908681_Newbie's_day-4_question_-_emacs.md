---
title: "Newbie's day-4 question - emacs"
date: 2012-01-13
forum: General Help
---

### Post by chenxinghao on 2012-01-13
Just installed GNU Emacs editor (metapackage) and the Dash home's Installed section lists Emacs23.

Then, typed "emacs testpage" in a Terminal window and got the following:

 chenxinghao@MyUbuntuSandBox:~$ emacs testpapge 

(emacs:5640): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emacs:5640): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emacs:5640): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emacs:5640): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emacs:5640): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emacs:5640): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emacs:5640): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emacs:5640): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

Don't know what this emacs error message 5640 means. They come out every time I use emacs. On the other hand, emacs seems work fine - I only used a few basic editing features.

Expert comments are very much appreciated.

(This is on an IBM ThinkCenter A50P with Ubuntu 11.10 installed several days ago, with all the "default" options - I did not key-in any thing during the installation. Installed GNU Emacs editor metapackage this afternoon and there has been no customization of emacs and Ubuntu from me.)

---

### Post by Telengard C64 on 2012-01-13
(emacs:5640): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

5640 is Emacs' process id. The rest of it is just a *warning* (not an error), coming from a package unrelated to emacs.

---

### Post by chenxinghao on 2012-01-14
Could you or anyone explain the meaning of the message. If it is from an unrelated package (what is it?), why does the message appear while I am using emacs?

---

### Post by Telengard C64 on 2012-01-14
> **chenxinghao said:**
> Could you or anyone explain the meaning of the message. If it is from an unrelated package (what is it?), why does the message appear while I am using emacs?

I'm afraid I can't explain it. I can only guess what might be causing the warning message.

My guess is that it is because the Emacs package for Ubuntu isn't being properly integrated into your GUI environment. Because the word "theme" appears in the message, you might try changing the appearance of desktop windows. That is only a guess though, because I have zero experience with the guts of GNOME and GTK.

I think you have good cause to file a bug report against the Emacs package, but please collect all relevant information first.

To prove to yourself that Emacs itself is perfectly fine, try running it inside the terminal with this command:

```
emacs -nw -Q
```

Then exit from Emacs with **C-x C-c**. Note that there are no warning messages left on the command line.

Sorry I can't help much more than that.

---

### Post by MG&amp;TL on 2012-01-14
I can tell you that the warnings are coming from some compatibility issues from Gtk2 to Gtk3. I'm not entirely sure what line of code  it is, but anytime you launch some graphical apps, it looks like that. It's no problem, and will go away shortly, I imagine.

It's NOT an issue. :)

---

### Post by chenxinghao on 2012-01-14
Thank you both for the inputs. I tried "emacs -nw file_name" and "emacs -nw -Q" and in both cases there were no messages of any kind, clean in-terminal screens.

In general, I think this type of messages should not be put to the users because it is meaningless and mostly there is nothing we, the users, can do or need to do about it. While recognizing the usefulness of these messages for development and integration, they should be masked off in general releases.

Great softwares demand cleanness, free or not.

Thank you both again - I love this Ubuntu community.

---

### Post by Telengard C64 on 2012-01-14
> **chenxinghao said:**
> In general, I think this type of messages should not be put to the users because it is meaningless and mostly there is nothing we, the users, can do or need to do about it. While recognizing the usefulness of these messages for development and integration, they should be masked off in general releases.

Actually, you *could* fix it. The source code is available. I understand not wanting to, and agree that you should not be required to.

The devs probably just need to tweak a configuration file or two to fix the problem.

---

### Post by chenxinghao on 2012-04-12
This is puzzling!

The emacs GTK warning messages disappeared (I don't know how) long ago. I don't recall doing anything special to fix it after posting this original note. This is with my desktop PC. I thought that maybe the (automatic) updates corrected whatever it was needed to correct.

Several days ago I installed the same Ubuntu 11.10 on to my ThinkPad X41 Tablet computer, from the same CD that I used to install Ubuntu on to my desktop PC, installed the latest updates and loaded exact the same applications on the desktop to this laptop.

But the gnu emacs reports the same GTK warning messages every time I use it on the laptop, but not on the desktop!  Isn't this strange?

Any advice?

---

### Post by brainwash on 2012-04-12
Looks like you have installed **gtk2-engines-pixbuf** at some point. By doing so the warnings should disappear.

You can find the bug report here:

[https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/762167](https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/762167)

---

### Post by chenxinghao on 2012-04-12
I did not specifically install this mentioned package myself. Was it in the automatic updates since January this year?

Is there a way to know whether or not this  [B]gtk2-engines-pixbuf is indeed installed on my desktop Ubuntu?
[/B]

---

### Post by redmk2 on 2012-04-12
> **chenxinghao said:**
> I did not specifically install this mentioned package myself. Was it in the automatic updates since January this year?

Is there a way to know whether or not this  [B]gtk2-engines-pixbuf is indeed installed on my desktop Ubuntu?
[/B]

The package *emacs23* uses a graphical user interface (GTK libs for this).  See [**_[COLOR="Blue"]here[/COLOR]_**]("http://packages.ubuntu.com/oneiric/emacs23") for details.

If you are using Synaptic you can check there to see a list of what is installed.  Filter the output by the package *gtk2-engines-pixbuf*.

The reason for the notices (not errors) is you started Emacs from the terminal.  Look on the launcher for Emacs and start it there.  You can look at the properties and see what is used to start emacs there.

Edit: The package *gtk2-engines-pixbuf* is a update for all versions of the emacs package upto 11.04.  Updates are how I got this package on my 10.04 workstation.  It looks like GTK was going through a transition.

Edit2: Read the last commet on [**_[COLOR="Red"]this[/COLOR]_**]("https://jira.mongodb.org/browse/SERVER-3997") post

---

### Post by MG&amp;TL on 2012-04-12
The following command shows whether a package is installed or not.

```
 apt-cache policy gtk2-engines-pixbuf
```

---

### Post by chenxinghao on 2012-04-13
Thanks for the advices. I understand the issue better now.

I used the provide command on both my desktop PC and my TP X41T laptop. The messages on the desktop shows that gtk2-engines-pixbuf is installed but not on the laptop. Since I didn't do the manual install of the gtk2 package, how did it get into my desktop Ubuntu? Should I expect the same "majic" with my laptop (wait for it to be installed somehow)?

Anyways, how to manually install the gtk2-engines-pixbuf package?

Thank you again.

---

### Post by MG&amp;TL on 2012-04-13
> **chenxinghao said:**
> 
Anyways, how to manually install the gtk2-engines-pixbuf package?


```
sudo apt-get install gtk2-engines-pixbuf
```

---

### Post by chenxinghao on 2012-04-13
Did the sudo line but now the message becmes the following:

Gtk-Message: Failed to load module "gtk-vector-screenshot"

PS: I installed the vector-screenshot by mistake and had removed it. Would this confuse the system?

---


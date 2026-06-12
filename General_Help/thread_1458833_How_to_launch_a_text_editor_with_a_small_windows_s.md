---
title: "How to launch a text editor with a small windows size?"
date: 2010-04-20
forum: General Help
---

### Post by RobertL on 2010-04-20
I'm looking for a programmable way to open an editor with a small window size. For example 60 columns and 3 lines. So I need an editor that can take its initial window size from command line args or environment variables, or possibly from an initial command that can be given on the command line. Any suggestions? 

I've looked at documentation and experimented with gedit, gvim (and vi & vim), and nano and I don't think any of them can be controlled this way. Vi and its friends have a "window" option and also a "resize" command, both of which are described as setting the number of rows, but they don't change the graphical window size they just change the number of rows displayed in the window.

---

### Post by gzarkadas on 2010-04-20
You can open a gnome terminal and launch in it a console editor. For example (this does not work with less than 6 lines):

```

gnome-terminal --geometry=60x6 --title='Small Window Editor' --hide-menubar --working-directory=/home/libero --command=nano

```

---

### Post by quadproc on 2010-04-20
> **gzarkadas said:**
> You can open a gnome terminal and launch in it a console editor.
This also works with vi (and probably with vim but I didn't try vim.)

quadproc

---

### Post by patchwork on 2010-04-20
I haven't used nedit much, but according to the man pages you can control its geometry..
[http://linux.die.net/man/1/nedit-client](http://linux.die.net/man/1/nedit-client)

---


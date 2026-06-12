---
title: "register thumbnailer in gnome config"
date: 2010-10-02
forum: General Help
---

### Post by Aegluin on 2010-10-02
Hi!
I try to implement thumbnails for files from a Wine program in order to integrate it better in Ubuntu. The Program is Sketchup which creates *.skp files in a binary format, but I found a ruby script that can extract the thumbnail (*.png).

Now I wanted to register it in the gnome configuration according to the following instruction:
[http://library.gnome.org/devel/integumbnailer.html]("http://library.gnome.org/devel/integumbnailer.html")

It works perfect if I execute the script manually (package *ruby* installed, script is executable):

```
ruby ~/.wine/skp-thumbnailer.rb /home/user/test.skp /home/user/test.png
```

Creates successfully a thumbnail test.png from the file test.skp.
With the following commands, I registered the script, but it doesn't create thumbnails automatically:

```
gconftool-2 -s /desktop/gnome/thumbnailers/application@wine-extension-skp/enable --type=bool true
gconftool-2 -s /desktop/gnome/thumbnailers/application@wine-extension-skp/command --type=string "ruby ~/.wine/skp-thumbnailer.rb %i %o"
```

Now my question is how to find the mistake. Do I need to copy the script into /usr/bin ? Apart from that, would it be possible to create it as a shell script (without *ruby* requirement)? If I knew how to translate it into .sh, I would prefer that.
I have really no clue how to make it work.
Many many thanks for help!

---

### Post by Aegluin on 2010-10-03
Does anyone have an idea what I could do? Or whom I could contact and ask?

---


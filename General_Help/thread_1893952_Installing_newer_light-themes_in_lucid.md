---
title: "Installing newer light-themes in lucid"
date: 2011-12-11
forum: General Help
---

### Post by Avidanborisov on 2011-12-11
Hello everyone!

Recently I reverted back to lucid, but I am not much a fan of the current light-themes there. They just seem pretty ugly. However, newer versions of Ubuntu have much nicer light-themes, that I actually really like. I tried to install them in lucid by adding the following ppa:

```
sudo add-apt-repository ppa:glasen/ubuntu-artwork-backport
sudo apt-get update
sudo apt-get upgrade
```

And it did, install them.

gtk2-engines-murrine version: 0.98~really0.98.1.1~glasen~ppa1
light-themes version: 0.1.8~really0.1.8.13~glasen~ppa1

It works great except of one problem, Qt apps like Skype (and some more), don't look natural. They use the default grey GTK theme, and they are pretty disgusting (as opposed to the light-themes, which are great). I do, however may have an error that might look useful for you to help me. When I load Skype from the shell, I get this error:

```
/usr/share/themes/Ambiance/gtk-2.0/gtkrc:101: error: unexpected identifier `default_button_color', expected character`}'
```

Also, perhaps posting the file here might be helpful too:

[URL="http://pastebin.com/gzrTqeD6"]http://pastebin.com/gzrTqeD6
[/URL]

---

### Post by Avidanborisov on 2011-12-12
Does someone have an idea?
I checked and I use the same versions of light-themes and gtk2-engines-murrine as in Natty. The only thing I could find related to this problem is [this bug]("https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/549028"), which states it was fixed. But what was fixed? How did they fix it?

---

### Post by Frogs Hair on 2011-12-12
For the bug , fix released would indicate an update was released to solve the problem . It doesn't say what the fix was .

I came across this in my search . [http://blog.bodhizazen.net/linux/using-gtk-2-themes-with-qt-applications/](http://blog.bodhizazen.net/linux/using-gtk-2-themes-with-qt-applications/)

---

### Post by Avidanborisov on 2011-12-12
Actually, I did already try to run qtconfig-qt4 and to select GTK+ as the theme, but it doesn't fix the problem. I think this is because Skype and some other Qt apps I am using are Qt3 apps, not Qt4 apps. For example, VLC, Synaptic and other Qt4 apps (I think, as they are posted in the link) are working great (They do not have the ugly color).

---

### Post by Avidanborisov on 2011-12-12
Well, tried many things, none helped. If anyone knows a solution I'd really like to hear it, Meanwhile, I guess I will just use Dust theme, as it looks pretty nice.

---


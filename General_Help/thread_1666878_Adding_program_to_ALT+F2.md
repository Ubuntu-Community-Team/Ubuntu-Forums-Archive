---
title: "Adding program to ALT+F2"
date: 2011-01-14
forum: General Help
---

### Post by sombrancelha on 2011-01-14
Hello,

I have just downloaded a program (Songbird), which came as .tar.gz.

I extracted it and had the program working just fine, but I'd like to be able to run it through ALT+F2 and typing it's name.

Is there a specific place where it should be extracted, and a "list" of programs that can be run by ALT+F2, that I should update?

Thank you!

---

### Post by nothingspecial on 2011-01-14
In order for an app to run simply by typing it`s name it needs to be in your path.

```
echo $PATH
```

To see the directories in your path.

---

### Post by kirkface8 on 2011-01-14
i don't know if this will help. but installing gnome-do or synapse would make this task easy.

```

sudo add-apt-repository ppa:synapse-core/ppa
sudo apt-get update
sudo apt-get install synapse
```

---

### Post by x1a4 on 2011-01-14
Where did you install it to?

If you installed it in /usr/local/songbird/ create a symlink to the executable in /usr/local/bin
```
sudo ln -s /usr/local/songbird/songbird /usr/local/bin/songbird
```

Ensure that /usr/local/bin/ is in your $PATH (it should be by default).

Also, you can always specify the full path in the 'Run' dialog.

---

### Post by wojox on 2011-01-14
Where did you find this. They dropped support for Linux I thought.

---

### Post by sombrancelha on 2011-01-15
Thank you for the Quick replies, I set a symlink in /usr/bin. Now I'd like to set the symlink icon, so when I type it in the Run dialog, the icon will appear. How?

@wojox: [Songbird 1.8.0]("https://wiki.songbirdnest.com/Developer/Articles/Builds/Contributed_Builds")

---

### Post by VCoolio on 2011-01-15
You can create a songbird.desktop launcher file in ~/.local/share/applications, or /usr/[local/]share/applications following [these](http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-0.9.4.html) standards and set the icon like this (also you won't need the executable in $PATH this way):
```

[Desktop Entry]
Version=0.8
Type=Application
Encoding=UTF-8
Name=Songbird
Comment=Some comment about my favorite player
Exec=/path/to/executable
Icon=/path/to/songbird.png
```
Or if the executable is named 'songbird' it *may* work to put a songbird.png in /usr/share/pixmaps. Above way is preferred though to prevent leaving a trail of single files all around your filesystem.

---

### Post by sombrancelha on 2011-01-15
Thank you!

---


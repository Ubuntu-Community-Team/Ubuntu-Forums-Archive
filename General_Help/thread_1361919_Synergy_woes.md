---
title: "Synergy woes"
date: 2009-12-22
forum: General Help
---

### Post by jbond007m3 on 2009-12-22
Installed, made config in home dir.  When i run sudo synergys --config synergy.conf i get an output of this:
synergys: no configuration available.

I have also specified the directory and got the same results.  This in on karmic, ive tried it on a few vm's and natively with all the same results.

I am sure im missing something very simple that no one in any of the guides/forums bothers to write it.

---

### Post by audiomick on 2009-12-22
Hi.
I love synergy, one of the slickest things I have ever seen :)

I start mine using a launcher that points to a script.

This is the script:
```
synergys --config /home/mick/my_scripts/synergy.conf
```

synergy.conf is at /home/mick/my_scripts/synergy.conf

This is my config
```
section: screens
ubuntu-desktop:
mick-laptop:
vista-laptop:
end

section: links
 ubuntu-desktop:
  right = vista-laptop
 mick-laptop:
  left = vista-laptop
 vista-laptop:
  left = ubuntu-desktop 
  right = mick-laptop
end
```

This is for three computers. Ubuntu-desktop on the left, Vista-laptop in the middle, mick-laptop on the right. It works even when only one of the laptops is present.

---

### Post by jbond007m3 on 2009-12-22
I have mine setup about the same, but when i launch, it doesnt recognize the config file

---

### Post by audiomick on 2009-12-22
have you got the conf set to execute as a program? I think you have to. Mine is.
right click> properties
in the pop up, third tab "permissions", check the box down near the bottom.

---

### Post by jbond007m3 on 2009-12-22
Thanks, that worked great.  i figured it was something small and simple like that.

Thanks again

---

### Post by audiomick on 2009-12-22
Great.

Just for your information, I have noticed on the Vista machine that sometimes when I select an item in the file browser it does "select all" instead. I work around this using the cursor arrows.

have fun with synergy!:)

---


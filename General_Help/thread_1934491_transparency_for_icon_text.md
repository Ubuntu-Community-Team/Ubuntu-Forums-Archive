---
title: "transparency for icon text"
date: 2012-03-02
forum: General Help
---

### Post by mike555 on 2012-03-02
How do I set transparency for desktop icons for all users in Xubuntu ? I know how for each user, but there should be a way to effect all users....

---

### Post by Toz on 2012-03-02
I believe you can add them to /etc/gtk-2.0/gtkrc. 

Source: [http://developer.gnome.org/gtk/unstable/gtk-Resource-Files.html]("http://developer.gnome.org/gtk/unstable/gtk-Resource-Files.html")

---

### Post by mike555 on 2012-03-02
I don't seam to have that in /etc/gtk-2.0.

---

### Post by Toz on 2012-03-02
If the file doesn't exit, create it and add the following content:
```

$ cat /etc/gtk-2.0/gtkrc 
#desktop icon transparency tweak
style "xfdesktop-icon-view" {
    XfdesktopIconView::label-alpha = 0

    base[NORMAL] = "#000000"
    base[SELECTED] = "#000000"
    base[ACTIVE] = "#000000"

    fg[NORMAL] = "#ffffff"
    fg[SELECTED] = "#ffffff"
    fg[ACTIVE] = "#ffffff"

    XfdesktopIconVIew::cell-spacing = 0
    XfdesktopIconView::cell-padding = 0
    XfdesktopIconView::cell-text-width-proportion = 2.0
}
widget_class "*XfdesktopIconView*" style "xfdesktop-icon-view"

```

It should make icons transparent for all users.

---

### Post by mike555 on 2012-03-02
Ok, I tried it and it didn't work , even after logging out and back in ...
 btw.. I'm using Xubuntu 11.10 with Xfce 4.8

---

### Post by Toz on 2012-03-02
Thats odd. It works for me (same setup 11.10/4.8 ). Anything interesting in ~/.xsession-errors?:
```

cat ~/.xsession-errors | grep gtkrc
```

---

### Post by mike555 on 2012-03-02
no errors, all I have in /etc/gtk-2.0. is a file called "im-multipress.conf", so I ( as root) adding the file "gtkrc" with the code text in it to the gtk-2 folder and restarted but it didn't work.
    did I not do right ?

---

### Post by Toz on 2012-03-02
Mind if I check settings and contents?

```
ls -l /etc/gtk-2.0
```
...and
```
cat /etc/gtk-2.0/gtkrc
```

What appearance theme are you using?

---

### Post by mike555 on 2012-03-03
mike@mike-IM7B:~$ ls -l /etc/gtk-2.0
total 4
-rw-r--r-- 1 root root 890 2011-10-05 16:37 im-multipress.conf
mike@mike-IM7B:~$ 


mike@mike-IM7B:~$ cat /etc/gtk-2.0/gtkrc
$ cat /etc/gtk-2.0/gtkrc 
#desktop icon transparency tweak
style "xfdesktop-icon-view" {
    XfdesktopIconView::label-alpha = 0

    base[NORMAL] = "#000000"
    base[SELECTED] = "#000000"
    base[ACTIVE] = "#000000"

    fg[NORMAL] = "#ffffff"
    fg[SELECTED] = "#ffffff"
    fg[ACTIVE] = "#ffffff"

    XfdesktopIconVIew::cell-spacing = 0
    XfdesktopIconView::cell-padding = 0
    XfdesktopIconView::cell-text-width-proportion = 2.0
}
widget_class "*XfdesktopIconView*" style "xfdesktop-icon-view"mike@mike-IM7B:~$


graybird theme.

---

### Post by Toz on 2012-03-03
> **mike555 said:**
> > mike@mike-IM7B:~$ ls -l /etc/gtk-2.0
total 4
-rw-r--r-- 1 root root 890 2011-10-05 16:37 im-multipress.conf
mike@mike-IM7B:~$
You seem to be missing the gtkrc file here. Is is just an ommission? (Because you can successfully cat it in the next statement)


> mike@mike-IM7B:~$ cat /etc/gtk-2.0/gtkrc
$ cat /etc/gtk-2.0/gtkrc 
#desktop icon transparency tweak
style "xfdesktop-icon-view" {
    XfdesktopIconView::label-alpha = 0

    base[NORMAL] = "#000000"
    base[SELECTED] = "#000000"
    base[ACTIVE] = "#000000"

    fg[NORMAL] = "#ffffff"
    fg[SELECTED] = "#ffffff"
    fg[ACTIVE] = "#ffffff"

    XfdesktopIconVIew::cell-spacing = 0
    XfdesktopIconView::cell-padding = 0
    XfdesktopIconView::cell-text-width-proportion = 2.0
}
widget_class "*XfdesktopIconView*" style "xfdesktop-icon-view"mike@mike-IM7B:~$


graybird theme.
This should work. Are you using a clean xubuntu or is this xfce installed on ubuntu? 

Is xfdesktop managing the desktop:
```
ps -ef  | grep xfdesktop | grep -v grep
```

What does the following return?
```
file /etc/gtk-2.0/gtkrc
```

And if you don't mind, please post back the contents of ~/.xsession-errors. (Use code blocks please -> Advanced-># mark).

---

### Post by mike555 on 2012-03-03
mike@mike-IM7B:~$ ps -ef  | grep xfdesktop | grep -v grep
mike      1392     1  0 07:07 ?        00:00:01 xfdesktop
mike@mike-IM7B:~$

---

### Post by mike555 on 2012-03-03
mike@mike-IM7B:~$ ps -ef  | grep xfdesktop | grep -v grep
mike      1392     1  0 07:07 ?        00:00:01 xfdesktop
mike@mike-IM7B:~$ 


mike@mike-IM7B:~$ file /etc/gtk-2.0/gtkrc
/etc/gtk-2.0/gtkrc: ASCII text
mike@mike-IM7B:~$

---

### Post by mike555 on 2012-03-03
```
mike@mike-IM7B:~$ cat ~/.xsession-errors | grep gtkrc
/etc/gtk-2.0/gtkrc:1: error: scanner: digit is beyond radix - e.g. `style'
/etc/gtk-2.0/gtkrc:1: error: scanner: digit is beyond radix - e.g. `style'
/etc/gtk-2.0/gtkrc:1: error: scanner: digit is beyond radix - e.g. `style'
/etc/gtk-2.0/gtkrc:1: error: scanner: digit is beyond radix - e.g. `style'
/etc/gtk-2.0/gtkrc:1: error: scanner: digit is beyond radix - e.g. `style'
/etc/gtk-2.0/gtkrc:1: error: scanner: digit is beyond radix - e.g. `style'
** (xfce4-session:1379): WARNING **: Unable to launch "/etc/gtk-2.0/gtkrc" (specified by autostart/icon text.desktop): Failed to execute child process "/etc/gtk-2.0/gtkrc" (Permission denied)
/etc/gtk-2.0/gtkrc:1: error: scanner: digit is beyond radix - e.g. `style'
/etc/gtk-2.0/gtkrc:1: error: scanner: digit is beyond radix - e.g. `style'
/etc/gtk-2.0/gtkrc:1: error: scanner: digit is beyond radix - e.g. `style'
/etc/gtk-2.0/gtkrc:1: error: scanner: digit is beyond radix - e.g. `style'
Starting Dropbox.../etc/gtk-2.0/gtkrc:1: error: scanner: digit is beyond radix - e.g. `style'
/etc/gtk-2.0/gtkrc:1: error: scanner: digit is beyond radix - e.g. `style'
/etc/gtk-2.0/gtkrc:1: error: scanner: digit is beyond radix - e.g. `style'
/etc/gtk-2.0/gtkrc:1: error: scanner: digit is beyond radix - e.g. `style'
/etc/gtk-2.0/gtkrc:1: error: scanner: digit is beyond radix - e.g. `style'
/etc/gtk-2.0/gtkrc:1: error: scanner: digit is beyond radix - e.g. `style'
/etc/gtk-2.0/gtkrc:1: error: scanner: digit is beyond radix - e.g. `style'
/etc/gtk-2.0/gtkrc:1: error: scanner: digit is beyond radix - e.g. `style'
/etc/gtk-2.0/gtkrc:1: error: scanner: digit is beyond radix - e.g. `style'
/etc/gtk-2.0/gtkrc:1: error: scanner: digit is beyond radix - e.g. `style'
/etc/gtk-2.0/gtkrc:1: error: scanner: digit is beyond radix - e.g. `style'
/etc/gtk-2.0/gtkrc:1: error: scanner: digit is beyond radix - e.g. `style'
/etc/gtk-2.0/gtkrc:1: error: scanner: digit is beyond radix - e.g. `style'
/etc/gtk-2.0/gtkrc:1: error: scanner: digit is beyond radix - e.g. `style'
/etc/gtk-2.0/gtkrc:1: error: scanner: digit is beyond radix - e.g. `style'
/etc/gtk-2.0/gtkrc:1: error: scanner: digit is beyond radix - e.g. `style'
/etc/gtk-2.0/gtkrc:1: error: scanner: digit is beyond radix - e.g. `style'
/etc/gtk-2.0/gtkrc:1: error: scanner: digit is beyond radix - e.g. `style'
/etc/gtk-2.0/gtkrc:1: error: scanner: digit is beyond radix - e.g. `style'
/etc/gtk-2.0/gtkrc:1: error: scanner: digit is beyond radix - e.g. `style'
/etc/gtk-2.0/gtkrc:1: error: scanner: digit is beyond radix - e.g. `style'
/etc/gtk-2.0/gtkrc:1: error: scanner: digit is beyond radix - e.g. `style'
/etc/gtk-2.0/gtkrc:1: error: scanner: digit is beyond radix - e.g. `style'
/etc/gtk-2.0/gtkrc:1: error: scanner: digit is beyond radix - e.g. `style'
/etc/gtk-2.0/gtkrc:1: error: scanner: digit is beyond radix - e.g. `style'
/etc/gtk-2.0/gtkrc:1: error: scanner: digit is beyond radix - e.g. `style'
/etc/gtk-2.0/gtkrc:1: error: scanner: digit is beyond radix - e.g. `style'
/etc/gtk-2.0/gtkrc:1: error: scanner: digit is beyond radix - e.g. `style'
/etc/gtk-2.0/gtkrc:1: error: scanner: digit is beyond radix - e.g. `style'
/etc/gtk-2.0/gtkrc:1: error: scanner: digit is beyond radix - e.g. `style'
/etc/gtk-2.0/gtkrc:1: error: scanner: digit is beyond radix - e.g. `style'
/etc/gtk-2.0/gtkrc:1: error: scanner: digit is beyond radix - e.g. `style'
/etc/gtk-2.0/gtkrc:1: error: scanner: digit is beyond radix - e.g. `style'
/etc/gtk-2.0/gtkrc:1: error: scanner: digit is beyond radix - e.g. `style'
/etc/gtk-2.0/gtkrc:1: error: scanner: digit is beyond radix - e.g. `style'
/etc/gtk-2.0/gtkrc:1: error: scanner: digit is beyond radix - e.g. `style'
/etc/gtk-2.0/gtkrc:1: error: scanner: digit is beyond radix - e.g. `style'
/etc/gtk-2.0/gtkrc:1: error: scanner: digit is beyond radix - e.g. `style'
/etc/gtk-2.0/gtkrc:1: error: scanner: digit is beyond radix - e.g. `style'
mike@mike-IM7B:~$ 

```    as you can see I even tried setting it to auto start , but that didn't work...

---

### Post by Toz on 2012-03-03
Is the first line of your /etc/gtk-2.0/gtkrc file:
> $ cat /etc/gtk-2.0/gtkrc 

If so, delete it.

---

### Post by mike555 on 2012-03-03
All right , deleting the first line worked ....... thanks so much......

---


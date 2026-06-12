---
title: "How to fix bash: &lt;filename&gt; : Permission denied"
date: 2009-11-15
forum: General Help
---

### Post by Brii on 2009-11-15
I just installed 9.10 and I can't access my /root/ file or my xorg.conf without getting some sort of access denied sign!

This is what I get when I just try to get into root through the file browser:
You do not have the permissions necessary to view the contents of "root".

I'm the only user on the computer too HELP!

Thank you

---

### Post by unamanic on 2009-11-15
by default, Ubuntu and 99% of Linux distributions do not allow the default user access to system files.  In order to edit your xorg.conf, issue the following from a terminal:
```

sudo gedit /etc/X11/xorg.conf

```
and enter your password when it asks for it

alternately, if you prefer not to open a teminal, you can press alt-f2 and enter:
```

gksu gedit /etc/X11/xorg.conf

```

---

### Post by jeannacav on 2009-11-20
> **unamanic said:**
> by default, Ubuntu and 99% of Linux distributions do not allow the default user access to system files.  In order to edit your xorg.conf, issue the following from a terminal:
```

sudo gedit /etc/X11/xorg.conf

```
and enter your password when it asks for it

alternately, if you prefer not to open a teminal, you can press alt-f2 and enter:
```

gksu gedit /etc/X11/xorg.conf

```

My problem is more generic.
I am unable to type anything when I need to give the password.
the keybord gets turned off rather than allow me to type my password.
WHERE can I even look for help?

thank you,

jeanna

---

### Post by BenAshton24 on 2009-11-20
> **jeannacav said:**
> My problem is more generic.
I am unable to type anything when I need to give the password.
the keybord gets turned off rather than allow me to type my password.
WHERE can I even look for help?

thank you,

jeanna

Your password will not show up but trust me, it is being typed :P just type it and press enter and it will work... you shouldn't see any characters on your screen. hope this helps ya.

Ben.

EDIT: If this is happening when you use gksudo then there is a problem because you should see bullets in place of your password as you are typing then...

---

### Post by jeannacav on 2009-11-20
> **BenAshton24 said:**
> Your password will not show up but trust me, it is being typed :P just type it and press enter and it will work... you shouldn't see any characters on your screen. hope this helps ya.

Ben.

EDIT: If this is happening when you use gksudo then there is a problem because you should see bullets in place of your password as you are typing then...

I was just going to check again

I see your edit and I typed gksudo into a terminal and I got a window asking me how I want to run something.
Is this how I perform sudo operations in ubuntu?

thank you,

jeanna

---

### Post by jeannacav on 2009-11-20
OK 
I have been trying to get my wireless to shake hands with my router.
I think that in itself is a known problem, so I can wait.

I was using the terminal trying to get the backports things and there was a request for my password.
Am I to understand that whenever someone gives me instrrux to type sudo, I should use gksudo in its place?

I just typed gksudo and I got the run window which displayed my pwd when I typed it, then I closed the run the window, and right in the terminal I was also able to type the pwd.
Is that it?

thank you for helping,

jeanna

---

### Post by neerajadsul on 2009-11-20
And from 9.10 there is no xorg.conf file in order to avoid confusions and other problems related to display devices and input devices. You need to see what you want to configure and refer to corresponding configuration file.

If you try to open xorg.conf file in ubuntu 9.10, it will give a blank text file with name xorg.conf

You don't need to type *gksudo* in the terminal. In terminal it's only *sudo*. If you want to open some application in GUI then you can use *gksu* e.g. Alt+F2, gksu nautilus.

---

### Post by lavinog on 2009-11-20
take a moment to read this:
[uhelp]community/RootSudo[/uhelp]
or this:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

also as mentioned /etc/X11/xorg.conf will not exist by default.  Why do you think you need to edit this file?  Are you following an outdated thread?

---

### Post by jeannacav on 2009-11-21
I am using a new computer and I am alarmed about some of the things that are/ are not happening.
I had the wireless working and then after the update/reboot yesterday I lost the wireless.
I followed some advice and typed a number of commands into the terminal about backports and things like that...

Whenever the computer asked me for the pwd, the keyboard stopped responding. One time it asked me why I wanted to get this information... was I root? Kriminy!

Today, I realized I need to figure out if this a problem with the computer. I do not need to use the terminal now, but if I ever do, I want to be fully able to do it.

thank you,

jeanna

> Your password will not show up but trust me, it is being typed  just type it and press enter and it will work... you shouldn't see any characters on your screen. hope this helps ya.

Ben.
And, I saw just now a piece about how the password appears to be doing nothing, so I am going to believe what you said and relax.

thx
j

---


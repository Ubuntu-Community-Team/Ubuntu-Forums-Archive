---
title: "Launcher icons"
date: 2012-07-10
forum: General Help
---

### Post by agkq62 on 2012-07-10
I have just loaded 12.04 on a Dell Inspiron 1501 laptop.The launcher panel is just solid black no icons, the icon labels do appear it you hover over the panel.

Any ideas?

Thanks

---

### Post by Frogs Hair on 2012-07-10
Try the command from the terminal ```
unity --reset-icons
```

---

### Post by agkq62 on 2012-07-10
> **Frogs Hair said:**
> Try the command from the terminal ```
unity --reset-icons
```

Thanks for the reply.

I have just restarted Ubuntu and the launcher panel has totally disappeared.
Where is the terminal now hiding?

---

### Post by Frogs Hair on 2012-07-10
Try logging into to Ubuntu 2D by selecting it from the greeter. The icon on the right side of the greeter box with the user name will display a menu with the option. 

If you are able to login to Ubuntu 2D test Unity 3D support with the following terminal command.```
/usr/lib/nux/unity_support_test -p
```

---

### Post by agkq62 on 2012-07-10
Sorry you have lost me. What or where is the greeter?

---

### Post by Frogs Hair on 2012-07-10
> **agkq62 said:**
> Sorry you have lost me. What or where is the greeter?

It is the box you enter the password in when logging in.

---

### Post by agkq62 on 2012-07-10
Now Getting somewhere, I had set to auto login so no greeter.

Found 2D, that works. Ran command prompt

maxwell@maxwell-Inspiron-1501:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   X.Org R300 Project
OpenGL renderer string: Gallium 0.4 on ATI RS480
OpenGL version string:  2.1 Mesa 8.0.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
maxwell@maxwell-Inspiron-1501:~$ 

So back to you with thanks.

---

### Post by Frogs Hair on 2012-07-10
Since you have 3D support try the following. 

Login to Ubuntu use Ctrl + Alt + F1 to enter TTY. Next, enter user name , password, and run the following command when (user name:~$)appears.
 
```
unity --reset
```

Wait until the process is complete and your user name appears again. Use Ctrl + Alt + F7 to renter the desktop environment.

If there is error reporting wait until finished. If Unity doesn't appear within a minute or two restart and login to Ubuntu. 

I have used this method on my system to restore Unity 3D successfully.

---

### Post by mc4man on 2012-07-10
If, when in the ubuntu session, (unity 3D) you get a 'black launcher' with usable icons then 1 possible cause could be that you have enabled a custom Background color in the unity settings but have #000000 as the color. *#000000 is the default color

The custom color is enabled once the Opacity is set to any value above 0

The use of #000000 as a color is a known bug, not yet fixed though 12.04 users can fix & rebuild unity to do so, at least thru the current 5.12 source
screen shows what you MAY be seeing

---

### Post by agkq62 on 2012-07-11
Thanks for the replies.

I have tried the reset but no luck. I haven't altered any settings and the problem has been there right from the new install.

I think I'll just stay with 2D.

What is the difference to 3D?

---

